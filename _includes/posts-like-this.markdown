<a name="posts-like-this"></a>
Read all posts like this:

<ul>
  {% for category in page.categories %}
    {% assign sorted_posts = (site.categories[category] | sort: 'date') %}
    {% for post in sorted_posts %}
      <li>
        <a href="{{ post.url }}">{{ post.title }}</a>
      </li>
    {% endfor %}
  {% endfor %}
</ul>
