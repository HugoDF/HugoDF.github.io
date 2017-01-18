---
layout: blog
title: Blog
permalink: /posts/
---

You can find posts about Functional Programming, JavaScript, Ruby and assorted development practices on [my Medium blog](https://medium.com/@hugo__df).

I also host some beginner tutorials [here](/tutorials).

And most of my talks are [here](/talks).



{% comment %}
<ul class="post-list">
    {% for post in site.posts %}
      <li>
        <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>

        <h2>
          <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
        </h2>
      </li>
    {% endfor %}
</ul>

<p class="rss-subscribe">subscribe <a href="{{ "/feed.xml" | prepend: site.baseurl }}">via RSS</a></p>
{% endcomment %}