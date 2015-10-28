---
layout: page
title: Tutorials
permalink: /tutorials/
---
<div class="post-container">
    <ul class="post-list">
      {% assign sorted_posts = (site.posts | sort: 'date', 'first') %}
      {% for post in sorted_posts %}
        {% if post.categories contains "tutorials" %}
        <li>
          <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>

          <h2>
            <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
          </h2>
        </li>
        {% endif %}
      {% endfor %}
    </ul>
</div>