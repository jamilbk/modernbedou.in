---
layout: post
title: Serve Rails Assets From CloudFront in 5 Easy Steps
date: 2012-06-19
tags:
- rails 3.1
- cloudfront
---

I have a love/hate relationship with the Rails asset pipeline. On one hand, it speeds up your application and provides simple asset helpers. On the other hand, it makes caching and production deployment a little tricky. In this post I hope to show you it's not rocket science to get a fast, scalable, and simple asset system up and running in just a few minutes.

The basic premise is that you use your Amazon S3+Cloudfront-hosted compiled assets for production, but fall back to dynamic compilation in your development environment. Let me walk you through it.

### Step 1: Create an S3 bucket and Cloudfront distribution

_I'll assume you know how to do this already._

### Step 2: Ensure your asset manifest file will make it to production when you deploy

_Note that you can safely add the rest of the contents of public/assets to .gitignore. All you need is the manifest. Who's crazy enough to track all those assets in version control anyway?_

    $ echo 'public/assets' >> .gitignore
    $ git add -f public/assets/manifest.yml

### Step 3: Ensure development and production environments are configured properly

_config/environments/development.rb_:

{% highlight ruby %}
# let's compile assets on-the-fly for development
config.serve_static_assets = false
{% endhighlight %}

_config/environments/production.rb_:

    # We'll be serving static assets with Cloudfront
    config.serve_static_assets = false

    # don't compile an asset on-the-fly if it's not found in manifest.yml
    # warning: this will cause a 500 error if asset isn't listed in manifest.yml!
    config.assets.compile = false

    # Prefix all asset paths with asset_host
    config.action_controller.asset_host = 'http://{bucket-name}.s3.amazonaws.com'


### Step 4: Add the asset\_sync gem and generate config:

_Gemfile_:

{% highlight ruby %}
gem 'asset_sync'
{% endhighlight %}

_then do_:

    $ bundle
    $ rails g asset_sync:install


### Step 5: Edit config/asset\_sync.yml for your environment:


{% highlight ruby %}
defaults: &defaults
  fog_provider: 'AWS'

  aws_access_key_id: {your AWS account key id}
  aws_secret_access_key: {your AWS account access key}

  # This is your S3 bucket name
  fog_directory: "{S3 bucket name here}"

  # You may need to specify what region your storage bucket is in.
  # For regions like us-west-1a just use us-west-1
  fog_region: us-west-1  

  # overwrite stale assets
  existing_remote_files: delete

  # Automatically replace files with their equivalent gzip compressed version
  gzip_compression: true

development:
  <<: *defaults

test:
  <<: *defaults

staging:
  <<: *defaults

production:
  <<: *defaults
{% endhighlight %}


_Et voila! All you need to do now is_:

    $ rake assets:precompile
    $ git commit -am "my assets are now scalable"
    $ git push && cap deploy

And that's it! asset\_sync automatically syncs your assets to Amazon S3 whenever you run rake assets:precompile. Now, each time you deploy, you would do something like this:

1. $ rake assets:precompile
2. $ git commit -am "unicorns are sexy"
3. $ git push && cap deploy

**Done and done.**


Resources:

- [AWS S3](http://aws.amazon.com/s3/)
- [AWS CloudFront](http://aws.amazon.com/cloudfront/)
- [Rails Asset Pipeline Guide](http://guides.rubyonrails.org/asset_pipeline.html)
- [asset\_sync gem](https://github.com/rumblelabs/asset_sync)
