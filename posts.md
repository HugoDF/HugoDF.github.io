---
layout: page
title: Posts
permalink: /posts/
---

<p>I also write on <a href="https://medium.com/@hugo__df">my medium account</a> and for <a href="https://medium.com/artificial-labs">Artificial Labs</a></p>.
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