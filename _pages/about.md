---
layout: about
title: about
permalink: /
subtitle: 

profile:
    align: right
    image: Abijith.jpg
    image_circular: false # crops the image to make it circular
    more_info: >

news: true # includes a list of news items
latest_posts: true # includes a list of the newest posts
selected_papers: true # includes a list of papers marked as "selected={true}"
social: false # includes social icons at the bottom of the page
---

<p style="text-align: justify;">
I am a postdoctoral researcher at the <a href="https://bigwww.epfl.ch/" target="_blank" rel="noopener">Biomedical Imaging Group, EPFL</a> and the <a href="https://cibm.ch" target="_blank" rel="noopener" class="affiliation-cibm"> CIBM Centre d'Imagerie Biomedicale</a> Signal Processing, Mathematical Imaging Group with <a href="https://bigwww.epfl.ch/unser/" target="_blank" rel="noopener">Prof. Michaël Unser</a>. Previously, I was with the Department of Electrical Engineering, Indian Institute of Science, with <a href="https://spectrum.ee.iisc.ac.in/" target="_blank" rel="noopener" class="affiliation-cibm">Prof. Chandra Sekhar Seelamantula</a>.
</p>

<div class="about-tl">
  <div class="atl-item atl-current">
    <div class="atl-dot"></div>
    <div class="atl-body">
      <span class="atl-place">EPFL</span>
      <span class="atl-role">Postdoctoral Researcher, STI LIB</span>
    </div>
  </div>
  <div class="atl-item">
    <div class="atl-dot"></div>
    <div class="atl-body">
      <a class="atl-place" href="https://iisc.ac.in" target="_blank" rel="noopener">IISc</a>
      <span class="atl-role">PhD, Electrical Engineering</span>
    </div>
  </div>
  <!-- <div class="atl-item">
    <div class="atl-dot"></div>
    <div class="atl-body">
      <a class="atl-place" href="https://www.nitk.ac.in" target="_blank" rel="noopener">NITK</a>
      <span class="atl-role">B.Tech, Electrical Engineering</span>
    </div>
  </div>
</div> -->

<style>
.about-tl {
  display: flex;
  flex-direction: column;
  margin-top: 0.85rem;
  margin-bottom: 0;
}

.atl-item {
  display: flex;
  align-items: flex-start;
  position: relative;
  padding-left: 1.1rem;
  padding-bottom: 0.45rem;
}

.atl-item:not(:last-child)::after {
  content: "";
  position: absolute;
  left: 0.255rem;
  top: 0.75rem;
  bottom: 0;
  width: 1px;
  background: var(--global-divider-color);
}

.atl-dot {
  position: absolute;
  left: 0;
  top: 0.2rem;
  width: 0.55rem;
  height: 0.55rem;
  border-radius: 50%;
  border: 1px solid var(--global-text-color-light);
  background: transparent;
  flex-shrink: 0;
}

.atl-current .atl-dot {
  background: var(--global-theme-color);
  border-color: var(--global-theme-color);
}

.atl-body {
  display: flex;
  flex-direction: column;
  gap: 0.1rem;
  line-height: 1.3;
}

.atl-place {
  font-size: 0.82rem;
  font-weight: 600;
  color: var(--global-text-color);
  letter-spacing: 0.01em;
  text-decoration: none !important;
}

a.atl-place:hover {
  text-decoration: underline !important;
  color: var(--global-text-color) !important;
  opacity: 0.7;
}

.atl-current .atl-place {
  color: var(--global-theme-color);
}

.atl-role {
  font-size: 0.75rem;
  color: var(--global-text-color-light);
}
</style>
