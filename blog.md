---
layout: default
title: Blog
---

# 📝 My Research & Notes

<ul>
  {% for post in site.posts %}
    <li style="margin-bottom: 15px;">
      <span style="color: #8b949e; font-size: 0.9em; margin-right: 10px;">
        {{ post.date | date: "%Y-%m-%d" }}
      </span>
      <a href="{{ post.url }}" style="font-size: 1.2em; font-weight: bold;">
        {{ post.title }}
      </a>
      <div style="color: #aaa; font-size: 0.9em;">
        {{ post.excerpt }}
      </div>
    </li>
  {% endfor %}
</ul>
