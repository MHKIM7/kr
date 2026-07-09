---
layout: page
title: news
permalink: /news/
description: Lab news and updates.
nav: true
nav_order: 4
---

<style>
  .proj-section { margin-top: 2rem; margin-bottom: 2.5rem; }
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
  }
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

<div class="proj-section">
  {% assign sorted_news = site.news | sort: "date" | reverse %}
  {% for n in sorted_news %}
    <div class="proj">
      <div class="meta">
        <span class="label">Date</span>
        {% assign date_str = n.date | append: "" %}
        {% if date_str contains " - " %}
          {{ date_str }}
        {% else %}
          {{ n.date | date: "%Y.%m.%d" }}
        {% endif %}
      </div>
      <div>
        <h3>{{ n.title }}</h3>
        {% if n.description %}<p>{{ n.description }}</p>{% endif %}
        {% if n.images and n.images.size > 0 %}
          <div class="thumb-group">
            {% for item in n.images %}
              {% assign img_first_char = item | slice: 0, 1 %}
              {% if img_first_char == "/" %}
                {% assign img_src = item %}
              {% else %}
                {% assign img_src = "/assets/img/" | append: item %}
              {% endif %}
              <img class="thumb" src="{{ img_src | relative_url }}" alt="{{ n.title }}" onclick="openProjLightbox('{{ img_src | relative_url }}')">
            {% endfor %}
          </div>
        {% endif %}
      </div>
    </div>
  {% endfor %}
</div>

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
