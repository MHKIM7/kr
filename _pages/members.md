---
layout: page
title: members
permalink: /members/
description: People at the GIScience & Spatial Bigdata Lab.
nav: true
nav_order: 1
---

<style>
  .member-section { margin-top: 1.5rem; margin-bottom: 2.5rem; }
  .member-section h2 { font-size: 1.4rem; margin-bottom: 1rem; }
  .member-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 1.5rem;
  }
  .member-card {
    text-align: center;
  }
  .member-card img {
    width: 100%;
    aspect-ratio: 1 / 1;
    object-fit: cover;
    border-radius: 50%;
    background: #f0f0f0;
  }
  .member-card .name { font-weight: 600; margin-top: 0.6rem; }
  .member-card .role { font-size: 0.9rem; color: var(--global-text-color-light, #888); }
  .member-card .interests { font-size: 0.85rem; margin-top: 0.4rem; line-height: 1.3; }
  .member-card .note { font-size: 0.8rem; font-style: italic; color: #888; margin-top: 0.3rem; }
  .member-card .email { font-size: 0.85rem; margin-top: 0.3rem; }
</style>

{% assign groups = "pi,phd,ms,ug,alumni" | split: "," %}
{% assign labels = "Principal Investigator,PhD Students,MS Students,Undergraduate Students,Alumni" | split: "," %}

{% for group in groups %}
  {% assign members = site.data.members[group] %}
  {% if members and members.size > 0 %}
  <div class="member-section">
    <h2>{{ labels[forloop.index0] }}</h2>
    <div class="member-grid">
      {% for m in members %}
      <div class="member-card">
        {% assign pos = m.image_position | default: "center center" %}
        {% if m.image %}
          <img src="{{ '/assets/img/' | append: m.image | relative_url }}" alt="{{ m.name }}" style="object-position: {{ pos }};" onerror="this.src='{{ '/assets/img/prof_pic.jpg' | relative_url }}'">
        {% else %}
          <img src="{{ '/assets/img/prof_pic.jpg' | relative_url }}" alt="{{ m.name }}" style="object-position: {{ pos }};">
        {% endif %}
        <div class="name">{{ m.name }}</div>
        <div class="role">
          {{ m.role }}{% if m.since %} · since {{ m.since }}{% endif %}
        </div>
        {% if m.interests %}<div class="interests">{{ m.interests }}</div>{% endif %}
        {% if m.email %}<div class="email"><a href="mailto:{{ m.email }}">{{ m.email }}</a></div>{% endif %}
        {% if m.note %}<div class="note">{{ m.note }}</div>{% endif %}
      </div>
      {% endfor %}
    </div>
  </div>
  {% endif %}
{% endfor %}
