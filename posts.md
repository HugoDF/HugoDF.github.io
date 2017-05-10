---
layout: blog
title: 
permalink: /posts/
---

You will find posts about Functional Programming, JavaScript, Ruby and assorted development practices.

You can also find [beginner tutorials](/tutorials) and some of [my talks](/talks).


<ul class="post-list">
    {% for post in site.posts %}
      {% unless post.categories contains "tutorials" %}
      <li>
        <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
        <h2>
          <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
        </h2>
      </li>
      {% endunless %}
    {% endfor %}
</ul>

<p class="rss-subscribe">subscribe <a href="{{ "/feed.xml" | prepend: site.baseurl }}">via RSS</a></p>
