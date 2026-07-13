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
  }
  .proj {
    display: grid;
    grid-template-columns: 1fr;
    gap: 0.4rem;
    padding: 1.1rem 0 1.2rem;
    border-bottom: 1px solid var(--global-divider-color, #eee);
  }
  @media (min-width: 760px) {
    .proj { grid-template-columns: 160px 1fr; gap: 1.4rem; align-items: start; }
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
  .thumb-group {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    margin-top: 0.9rem;
  }
  .thumb {
    width: 110px;
    height: 110px;
    object-fit: cover;
    border-radius: 6px;
    cursor: zoom-in;
    border: 1px solid var(--global-divider-color, #ddd);
    transition: opacity 0.15s;
  }
  .thumb:hover { opacity: 0.85; }

  #proj-lightbox {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.85);
    z-index: 9999;
    align-items: center;
    justify-content: center;
    cursor: zoom-out;
    padding: 2rem;
  }
  #proj-lightbox.open { display: flex; }
  #proj-lightbox img {
    max-width: 90vw;
    max-height: 90vh;
    border-radius: 4px;
    box-shadow: 0 10px 40px rgba(0,0,0,0.5);
  }
  #proj-lightbox .close-btn {
    position: absolute;
    top: 1.2rem;
    right: 1.6rem;
    color: #fff;
    font-size: 2rem;
    line-height: 1;
    cursor: pointer;
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
          {% if p.images and p.images.size > 0 %}
            <div class="thumb-group">
              {% for item in p.images %}
                {% assign img_first_char = item | slice: 0, 1 %}
                {% if img_first_char == "/" %}
                  {% assign img_src = item %}
                {% else %}
                  {% assign img_src = "/assets/img/" | append: item %}
                {% endif %}
                <img class="thumb" src="{{ img_src | relative_url }}" alt="{{ p.title }}" onclick="openProjLightbox('{{ img_src | relative_url }}')">
              {% endfor %}
            </div>
          {% endif %}
        </div>
      </div>
    {% endfor %}
  </div>
  {% endif %}
{% endfor %}

<div id="proj-lightbox" onclick="closeProjLightbox()">
  <span class="close-btn">&times;</span>
  <img id="proj-lightbox-img" src="" alt="">
</div>

<script>
  function openProjLightbox(src) {
    document.getElementById('proj-lightbox-img').src = src;
    document.getElementById('proj-lightbox').classList.add('open');
  }
  function closeProjLightbox() {
    document.getElementById('proj-lightbox').classList.remove('open');
  }
  document.addEventListener('keydown', function(e) {
    if (e.key === 'Escape') closeProjLightbox();
  });
</script>
