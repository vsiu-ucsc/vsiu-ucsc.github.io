---
permalink: /
title: ""
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

## <span class="section-mark" aria-hidden="true">👋</span> About {#about}

I am a PhD student at the University of California, Santa Cruz, advised by <a href="https://cgraywang.github.io/">Prof. Chenguang Wang</a> and very fortunate to closely work with <a href="https://dawnsong.io/">Prof. Dawn Song</a>. I interned at Meta Superintelligence Labs in summer 2026 working on post-training agents, and previously worked at Scale Labs on computer-use. I completed my Bachelor’s degree in Data Science from the Mathematics Department at Washington University in St. Louis, graduating with Highest Distinction. You can find my full CV [here]({{ '/cv/' | relative_url }}).

My research focuses on developing methods to better interpret and ensure the safety and performance of large language models (LLMs) and LLM agents.

<p class="topic-filter">
{%- for topic in site.data.topics %}
<a class="topic topic--{{ topic.key }}" href="#publications" data-topic-filter="{{ topic.key }}">{{ topic.name }}</a>
{%- endfor %}
</p>

## <span class="section-mark" aria-hidden="true">📣</span> News {#news}

<ul class="entry-list entry-list--narrow entry-list--scroll">
{%- for item in site.data.news %}
<li class="entry">
<div class="entry__label">{{ item.date }}</div>
<div class="entry__body">{{ item.text }}</div>
</li>
{%- endfor %}
</ul>

## <span class="section-mark" aria-hidden="true">📚</span> Publications {#publications}

{% include publication-list.html %}

## <span class="section-mark" aria-hidden="true">📰</span> Media Coverage {#media}

<div class="tile-grid">
{%- for item in site.data.media %}
<a class="tile" href="{{ item.url }}">
<span class="tile__logo" role="img" aria-label="{{ item.outlet }}" style="--logo: url('{{ '/images/media/' | append: item.logo | relative_url }}')"></span>
<span class="tile__title">{{ item.title }}</span>
<span class="tile__meta">{{ item.date }}</span>
</a>
{%- endfor %}
</div>

## <span class="section-mark" aria-hidden="true">🤝</span> Service {#service}

<h3 class="entry-group">Agents in the Wild: Safety, Security, and Beyond <span class="entry-group__note">workshop series</span></h3>
<div class="tile-grid">
<a class="tile" href="https://agentwild-workshop.github.io/neurips2026/">
<img class="tile__flag" src="{{ '/images/flags/au.svg' | relative_url }}" alt="Flag of Australia">
<span class="tile__kicker venue"><span class="venue__icon"><img src="{{ '/images/venues/neurips.png' | relative_url }}" alt=""></span>NeurIPS 2026</span>
<span class="tile__title">Core Organizer</span>
<span class="tile__meta">Sydney, Australia</span>
</a>
<a class="tile" href="https://agentwild-workshop.github.io/icml2026/">
<img class="tile__flag" src="{{ '/images/flags/kr.svg' | relative_url }}" alt="Flag of South Korea">
<span class="tile__kicker venue"><span class="venue__icon"><img src="{{ '/images/venues/icml.png' | relative_url }}" alt=""></span>ICML 2026</span>
<span class="tile__title">Workshop Staff</span>
<span class="tile__meta">Seoul, South Korea</span>
</a>
<a class="tile" href="https://agentwild-workshop.github.io/">
<img class="tile__flag" src="{{ '/images/flags/br.svg' | relative_url }}" alt="Flag of Brazil">
<span class="tile__kicker venue"><span class="venue__icon"><img src="{{ '/images/venues/iclr.png' | relative_url }}" alt=""></span>ICLR 2026</span>
<span class="tile__title">Co-Organizer</span>
<span class="tile__meta">Rio de Janeiro, Brazil</span>
</a>
</div>
<p class="entry-note">Featured in <a href="https://berkeleyrdi.substack.com/i/186622689/workshop-at-iclr-2026-agents-in-the-wild-safety-security-and-beyond">Agentic AI Weekly by Berkeley RDI</a>. Sponsored by Scale AI, Skywork, Lambda, AG2, Snorkel AI, Donut Labs, and Aveo Research Labs.</p>

<h3 class="entry-group">Open Source</h3>
<div class="tile-grid">
<a class="tile" href="https://github.com/Leezekun/MassGen">
<span class="tile__kicker"><i class="fa-brands fa-github" aria-hidden="true"></i> Contributor</span>
<span class="tile__title">MassGen</span>
<span class="tile__meta"><i class="fa-solid fa-star" aria-hidden="true"></i> 1k+ GitHub stars</span>
</a>
</div>

<script>
/* Highlights the masthead tab for the section currently in view. */
(function () {
  var links = [].slice.call(document.querySelectorAll('#site-nav a[href*="#"]'));
  var sections = links.map(function (a) { return document.getElementById(a.hash.slice(1)); });
  function update() {
    var current = -1;
    sections.forEach(function (s, i) {
      if (s && s.getBoundingClientRect().top < 140) { current = i; }
    });
    links.forEach(function (a, i) { a.classList.toggle('is-current', i === current); });
  }
  window.addEventListener('scroll', update, { passive: true });
  update();
})();

/* Topic chips filter the publication list; clicking the active chip clears the filter. */
(function () {
  var chips = [].slice.call(document.querySelectorAll('[data-topic-filter]'));
  var papers = [].slice.call(document.querySelectorAll('[data-topics]'));
  var active = '';
  function apply(topic) {
    active = topic;
    chips.forEach(function (chip) {
      var on = chip.getAttribute('data-topic-filter') === active;
      chip.classList.toggle('is-active', on);
      if (chip.hasAttribute('aria-pressed')) { chip.setAttribute('aria-pressed', on); }
    });
    papers.forEach(function (paper) {
      paper.hidden = active !== '' && paper.getAttribute('data-topics').split(' ').indexOf(active) === -1;
    });
  }
  chips.forEach(function (chip) {
    chip.addEventListener('click', function () {
      var topic = chip.getAttribute('data-topic-filter');
      apply(chip.tagName === 'BUTTON' && topic === active ? '' : topic);
    });
  });
})();

</script>
