---
layout: about
title: about
permalink: /
subtitle: <em>Geography that listens to data, places, and people.</em>

selected_papers: true
social: true

latest_posts:
  enabled: false
---

<style>
  /* ---------- Home page custom ---------- */
  .home-intro {
    max-width: 660px;
    font-size: 1.05rem;
    line-height: 1.6;
    color: var(--global-text-color, #333);
    margin: 0.6rem 0 2.4rem;
  }

  .pillars {
    display: grid;
    grid-template-columns: 1fr;
    gap: 0;
    margin: 1.5rem 0 2.6rem;
    border-top: 1px solid var(--global-divider-color, #e5e5e5);
  }
  @media (min-width: 760px) {
    .pillars { grid-template-columns: repeat(3, 1fr); border-top: none; }
  }
  .pillar {
    padding: 1.5rem 1.6rem;
    border-bottom: 1px solid var(--global-divider-color, #e5e5e5);
    transition: background-color .2s ease;
  }
  @media (min-width: 760px) {
    .pillar {
      border-bottom: none;
      border-right: 1px solid var(--global-divider-color, #e5e5e5);
      padding: 0 1.6rem 0.4rem 0;
    }
    .pillar:last-child { border-right: none; padding-right: 0; }
    .pillar:first-child { padding-left: 0; }
    .pillar:not(:first-child) { padding-left: 1.6rem; }
  }
  .pillar:hover { background-color: rgba(127,127,127,0.06); }

  .pillar-num {
    font-family: "Roboto Slab", Georgia, serif;
    font-size: 0.85rem;
    letter-spacing: 0.18em;
    color: var(--global-theme-color);
    margin-bottom: 0.5rem;
    font-weight: 700;
  }
  .pillar h3 {
    font-size: 1.25rem;
    font-weight: 700;
    margin: 0 0 0.5rem 0;
    line-height: 1.25;
    letter-spacing: -0.01em;
    color: var(--global-text-color);
  }
  .pillar p {
    font-size: 0.92rem;
    line-height: 1.55;
    color: var(--global-text-color-light, #666);
    margin: 0;
  }

  .home-cta {
    display: flex;
    flex-wrap: wrap;
    gap: 0.4rem 1.6rem;
    font-size: 0.95rem;
    margin: 0 0 2rem;
    padding: 0.9rem 0 1rem;
    border-top: 1px solid var(--global-divider-color, #e5e5e5);
    border-bottom: 1px solid var(--global-divider-color, #e5e5e5);
  }
  .home-cta a {
    color: inherit;
    border-bottom: 1px solid transparent;
    transition: border-bottom-color .15s ease;
  }
  .home-cta a:hover { border-bottom-color: currentColor; }
  .home-cta .arrow { color: var(--global-theme-color); margin-right: 0.3rem; font-weight: 700; }

  /* Tweaks for the auto-rendered news / selected publications headings */
  article > h2 {
    font-size: 1.45rem;
    margin-top: 2rem;
    border-bottom: 1px solid var(--global-divider-color, #e5e5e5);
    padding-bottom: 0.4rem;
  }

  /* Make the hero subtitle (page.subtitle) feel like a real hero line */
  .post-header .desc {
    font-size: 1.35rem;
    line-height: 1.4;
    color: var(--global-text-color);
    margin-top: 0.4rem;
  }
  @media (min-width: 760px) {
    .post-header .desc { font-size: 1.6rem; }
  }

  /* ---------- Slideshow ---------- */
  .lab-slideshow {
    position: relative;
    width: 100%;
    aspect-ratio: 16 / 9;
    overflow: hidden;
    border-radius: 10px;
    margin: 0.8rem 0 2.4rem;  /* sits right under the hero */
    background: #1a1f3a;
    box-shadow: 0 6px 22px rgba(44, 50, 96, 0.12);
  }
  .lab-slideshow .slide {
    position: absolute;
    inset: 0;
    opacity: 0;
    transition: opacity 1.2s ease-in-out;
    pointer-events: none;
  }
  .lab-slideshow .slide.active { opacity: 1; pointer-events: auto; }
  .lab-slideshow .slide img {
    width: 100%; height: 100%; object-fit: cover;
    display: block;
  }
  .lab-slideshow .ss-nav {
    position: absolute;
    top: 50%; transform: translateY(-50%);
    width: 38px; height: 38px;
    border: none;
    border-radius: 50%;
    background: rgba(255, 255, 255, 0.7);
    color: #2c3260;
    font-size: 1.4rem; font-weight: 700;
    line-height: 1;
    cursor: pointer;
    z-index: 2;
    opacity: 0; transition: opacity .2s ease, background .2s ease;
  }
  .lab-slideshow:hover .ss-nav { opacity: 1; }
  .lab-slideshow .ss-nav:hover { background: white; }
  .lab-slideshow .ss-nav.prev { left: 12px; }
  .lab-slideshow .ss-nav.next { right: 12px; }
  .lab-slideshow .dots {
    position: absolute;
    bottom: 12px; left: 50%; transform: translateX(-50%);
    display: flex; gap: 6px;
    z-index: 2;
  }
  .lab-slideshow .dot {
    width: 8px; height: 8px;
    border-radius: 50%;
    background: rgba(255,255,255,0.45);
    cursor: pointer;
    transition: background .2s ease, transform .2s ease;
  }
  .lab-slideshow .dot:hover { transform: scale(1.3); }
  .lab-slideshow .dot.active { background: white; }
</style>

<div class="lab-slideshow" aria-label="Lab life">
  {% assign all_slides = "" | split: "" %}
  {% for f in site.static_files %}
    {% if f.path contains '/assets/img/slideshow/' and f.extname == '.jpg' %}
      {% assign all_slides = all_slides | push: f %}
    {% endif %}
  {% endfor %}
  {% for f in all_slides %}
    <div class="slide{% if forloop.first %} active{% endif %}">
      <img src="{{ f.path | relative_url }}"
           alt="Lab activity {{ forloop.index }}"
           loading="{% if forloop.first %}eager{% else %}lazy{% endif %}">
    </div>
  {% endfor %}
  <button class="ss-nav prev" aria-label="Previous slide">‹</button>
  <button class="ss-nav next" aria-label="Next slide">›</button>
  <div class="dots">
    {% for f in all_slides %}
      <span class="dot{% if forloop.first %} active{% endif %}" data-i="{{ forloop.index0 }}"></span>
    {% endfor %}
  </div>
</div>

<p class="home-intro">
  We are a research lab at the <strong>Department of Geography, Kyungpook
  National University</strong>, working at the intersection of GIScience,
  spatial big data, and mobility — to understand how cities, regions, and
  people move and change.
</p>

<div class="pillars">
  <div class="pillar">
    <div class="pillar-num">01 — RESEARCH</div>
    <h3>GIScience</h3>
    <p>Representing and analysing the real world for the digital-twin era.</p>
  </div>
  <div class="pillar">
    <div class="pillar-num">02 — RESEARCH</div>
    <h3>Spatial Big Data</h3>
    <p>Discovering hidden patterns from mobile, social-media, and sensor data.</p>
  </div>
  <div class="pillar">
    <div class="pillar-num">03 — RESEARCH</div>
    <h3>Mobility &amp; Future Vehicles</h3>
    <p>Tracking how EVs, AVs, and shared mobility reshape urban space.</p>
  </div>
</div>

<script>
(function() {
  var box = document.querySelector('.lab-slideshow');
  if (!box) return;
  var slides = box.querySelectorAll('.slide');
  var dots = box.querySelectorAll('.dot');
  var idx = 0;
  var timer;
  function show(i) {
    idx = (i + slides.length) % slides.length;
    slides.forEach(function(s, k) { s.classList.toggle('active', k === idx); });
    dots.forEach(function(d, k) { d.classList.toggle('active', k === idx); });
  }
  function start() { timer = setInterval(function() { show(idx + 1); }, 5000); }
  function stop()  { clearInterval(timer); }
  box.querySelector('.next').addEventListener('click', function() { stop(); show(idx + 1); start(); });
  box.querySelector('.prev').addEventListener('click', function() { stop(); show(idx - 1); start(); });
  dots.forEach(function(d) {
    d.addEventListener('click', function() { stop(); show(parseInt(d.dataset.i, 10)); start(); });
  });
  box.addEventListener('mouseenter', stop);
  box.addEventListener('mouseleave', start);
  start();
})();
</script>

<div class="home-cta">
  <a href="{{ '/members/' | relative_url }}"><span class="arrow">→</span>Meet the team</a>
  <a href="{{ '/publications/' | relative_url }}"><span class="arrow">→</span>Read our publications</a>
  <a href="{{ '/projects/' | relative_url }}"><span class="arrow">→</span>Ongoing projects</a>
  <a href="{{ '/contact/' | relative_url }}"><span class="arrow">→</span>Get in touch</a>
</div>
