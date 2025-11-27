---
layout: page
title: projects
permalink: /projects/
description: 
nav: true
nav_order: 3
display_categories: [unlimited sampling, inverse problems]
horizontal: false
---

<div class="projects-modern">
  {% if site.enable_project_categories and page.display_categories %}
    {% for category in page.display_categories %}
      <h2 class="category-header">{{ category }}</h2>
      <div class="projects-grid">
        {% assign categorized_projects = site.projects | where: "category", category %}
        {% assign sorted_projects = categorized_projects | sort: "importance" %}
        {% for project in sorted_projects %}
          {% include projects_modern.liquid %}
        {% endfor %}
      </div>
    {% endfor %}
  {% else %}
    <div class="projects-grid">
      {% assign sorted_projects = site.projects | sort: "importance" %}
      {% for project in sorted_projects %}
        {% include projects_modern.liquid %}
      {% endfor %}
    </div>
  {% endif %}
</div>

<style>
.projects-modern {
  margin-top: 2rem;
}

.category-header {
  color: var(--global-text-color);
  border-bottom: 2px solid var(--global-theme-color);
  padding-bottom: 0.5rem;
  margin-bottom: 2rem !important;
  font-weight: 600;
  font-size: 1.5rem;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
  gap: 2rem;
  margin-bottom: 3rem;
}

.project-card {
  display: flex;
  flex-direction: column;
  padding: 0;
  height: 100%;
  position: relative;
  overflow: hidden;
}

.project-link {
  text-decoration: none;
  color: inherit;
  display: block;
}

.project-link:hover {
  text-decoration: none;
  color: inherit;
}

.project-card.clickable {
  cursor: pointer;
}

.project-header {
  display: flex;
  justify-content: flex-end;
  align-items: flex-start;
  margin-bottom: 0.5rem;
  height: 24px; /* Set a fixed height */
}

.project-code {
  background: transparent;
  color: var(--global-theme-color);
  padding: 0;
  border-radius: 0;
  font-size: 0.85rem;
  font-weight: 600;
  min-width: fit-content;
  text-transform: uppercase;
}

.project-link-icon {
  color: var(--global-text-color-light);
  opacity: 0.7;
  transition: opacity 0.2s ease;
}

.project-card.clickable:hover .project-link-icon {
  opacity: 1;
  color: var(--global-theme-color);
}

.project-content {
  flex-grow: 1;
}

.project-image-container {
  margin-bottom: 1rem;
  overflow: hidden;
  border-radius: 0;
}

.project-image {
  width: 100%;
  height: auto;
  display: block;
}

.project-title {
  color: var(--global-text-color);
  font-weight: 600;
  line-height: 1.3;
  margin-bottom: 0.75rem !important;
  transition: color 0.3s ease;
}

.project-card.clickable:hover .project-title {
  color: var(--global-theme-color);
}

.project-description {
  color: var(--global-text-color-light);
  font-size: 0.95rem;
  line-height: 1.5;
  margin-bottom: 1rem !important;
}

.project-footer {
  margin-top: auto;
  padding-top: 1rem;
  border-top: 1px solid var(--global-divider-color);
  display: flex;
  justify-content: flex-end;
}

.github-button {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  background-color: transparent;
  color: var(--global-text-color);
  padding: 0;
  border: none;
  font-weight: 500;
  font-size: 0.85rem;
  text-decoration: none !important;
  transition: all 0.3s ease;
}

.github-button:hover {
  color: var(--global-theme-color);
}

.github-button .fa-star {
  color: #ffc107;
}

@media (max-width: 768px) {
  .projects-grid {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
}
</style>
