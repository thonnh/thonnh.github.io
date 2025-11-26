---
layout: default
title: Research Notes & Blog
---

# Research Notes & Blog

<ul style="list-style: none; padding: 0;">
  {% for post in site.posts %}
    <li style="margin-bottom: 20px; border-bottom: 1px solid #30363d; padding-bottom: 15px;">
      <div style="font-size: 0.9em; color: #8b949e; margin-bottom: 5px;">
        {{ post.date | date: "%Y-%m-%d" }} </div>
      <a href="{{ post.url }}" style="font-size: 1.3em; font-weight: bold; color: #58a6ff; text-decoration: none;">
        {{ post.title }} </a>
    </li>
  {% endfor %}
</ul>
