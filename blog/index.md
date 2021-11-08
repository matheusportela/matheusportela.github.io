---
layout: page
title: Blog
---

<div class="post-list">
  {% for post in site.posts %}
    <div class="post-list-item">
      <div class="post-list-date">{{ post.date | date_to_string }}</div>
      <a href="{{ post.url }}">
        {{ post.title }}
      </a>
    </div>
  {% endfor %}
</div>
