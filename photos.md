---
title: "Photos"
layout: single
permalink: /photos/
author_profile: false
---

<div class="photo-grid">
  {% for photo in site.data.photos %}
    <a class="photo-card" href="{{ photo.image | relative_url }}">
      <img src="{{ photo.image | relative_url }}" alt="{{ photo.alt }}">
      {% if photo.caption %}
        <span>{{ photo.caption }}</span>
      {% endif %}
    </a>
  {% endfor %}
</div>