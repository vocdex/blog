---
layout: page
title: misc
permalink: /misc/
description: A growing collection of robots I have worked with and some photos I have taken.
nav: true
nav_order: 2
horizontal: false
---

<!-- pages/misc.md -->
<div class="gallery">
{%- if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized gallery -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_gallery = site.gallery | where: "category", category -%}
  {%- assign sorted_gallery = categorized_gallery | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for project in sorted_gallery -%}
      {% include gallery_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for project in sorted_gallery -%}
      {% include gallery.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display gallery without categories -->
  {%- assign sorted_gallery = site.gallery | sort: "importance" -%}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for project in sorted_gallery -%}
      {% include gallery_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for project in sorted_gallery -%}
      {% include projects.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
