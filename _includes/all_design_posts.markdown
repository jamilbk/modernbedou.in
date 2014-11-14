Read all tiny hacker house posts:

<ul>
  {% assign sorted_posts = (site.tags.house | sort: 'date') %}
  {% for post in sorted_posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
