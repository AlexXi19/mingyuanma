---
layout: page
permalink: /publications/
title: Publications
description: It is a collection of my publications 
years: [2023]
# 1967, 1956, 1950, 1935, 1905
nav: True
nav_order: 1
---
<!-- _pages/publications.md -->
<div class="publications">

{%- for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}

</div>
