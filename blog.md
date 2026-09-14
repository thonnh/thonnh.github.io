---
layout: default
title: Research Notes & Blog
nav_section: blog
wide_content: true
---

# Research Notes & Blog

<p class="page-intro">Notes, presentations, demonstrations, and updates from my work in computational mechanics and scientific machine learning.</p>

<ul class="post-list">
  {% for post in site.posts %}
    <li>
      <a class="post-card" href="{{ post.url }}">
        <time datetime="{{ post.date | date: '%Y-%m-%d' }}">{{ post.date | date: "%d %b %Y" }}</time>
        <span class="post-title">{{ post.title }}</span>
        <span class="post-arrow" aria-hidden="true">↗</span>
      </a>
    </li>
  {% endfor %}
</ul>
