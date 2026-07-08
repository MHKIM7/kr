---
layout: page
title: projects
permalink: /projects/
description: Funded research projects.
nav: true
nav_order: 3
---

<style>
  .proj-section { margin-top: 2rem; margin-bottom: 2.5rem; }
  .proj-section > h2 {
    font-size: 1.55rem;
    margin-bottom: 1.2rem;
    padding-bottom: 0.4rem;
    border-bottom: 2px solid var(--global-theme-color);
    color: var(--global-theme-color);
    letter-spacing: -0.01em;
  }
  .proj {
    display: grid;
    grid-template-columns: 1fr;
    gap: 0.4rem;
    padding: 1.1rem 0 1.2rem;
    border-bottom: 1px solid var(--global-divider-color, #eee);
  }
  @media (min-width: 760px) {
    .proj { grid-template-columns: 200px 1fr; gap: 1.4rem; align-items: start; }
  }
  .proj .meta {
    font-size: 0.85rem;
    color: var(--global-text-color-light, #666);
    line-height: 1.55;
  }
  .proj .meta .label {
    display: block;
    font-size: 0.7rem;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--global-theme-color);
    font-weight: 700;
    margin-top: 0.55rem;
  }
  .proj .meta .label:first-child { margin-top: 0; }
  .proj h3 {
    font-size: 1.05rem;
    line-height: 1.35;
    margin: 0 0 0.5rem 0;
    font-weight: 700;
    color: var(--global-text-color);
  }
  .proj p {
    font-size: 0.92rem;
    line-height: 1.55;
    color: var(--global-text-color);
    margin: 0;
  }
</style>

{% assign categories = "ongoing,completed" | split: "," %}
{% assign labels = "Ongoing,Completed" | split: "," %}

{% for cat in categories %}
  {% assign in_cat = site.projects | where: "category", cat | sort: "importance" %}
  {% if in_cat.size > 0 %}
  <div class="proj-section">
    <h2>{{ labels[forloop.index0] }}</h2>
    {% for p in in_cat %}
      <div class="proj">
        <div class="meta">
          {% if p.period %}<span class="label">Period</span>{{ p.period }}{% endif %}
          {% if p.sponsor %}<span class="label">Sponsor</span>{{ p.sponsor }}{% endif %}
        </div>
        <div>
          <h3>{{ p.title }}</h3>
          {% if p.description %}<p>{{ p.description }}</p>{% endif %}
        </div>
      </div>
    {% endfor %}
  </div>
  {% endif %}
{% endfor %}
