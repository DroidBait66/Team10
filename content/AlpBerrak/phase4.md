---
title: "Phase 4 Deliverable"
date: 2025-06-05
draft: false
description: "Phase 4 Individual Deliverable"
slug: "phase4alp"   # if you use, needs to be different for every post
tags: ["authors", "config", "docs"]
authors:
  - "alpberrak"
showAuthorsBadges : false
---

# Phase Four Blog Post
This phase was the final stretch and it included a lot. To start, I worked with one of my DS teammates to implement the lag 5 time series model to predict each countries expenditure on social programs per gdp. This data was plotted onto a graph with two different colors, one for actual and one for projected data. to connect the two lines, we had to add 2022 (from real) to the projected and real data.

I also established a functional connection between the lawyer and commissioner personas. By using a shared database table, lawyers can now submit funding requests (via POST), which commissioners can then view and either approve or reject (via PUT).

Additionally, I developed part of the country demographics page. Specifically, I created a new GET route to retrieve the total number of students across different education levels for each country, and displayed the data using a bar chart.

To enhance usability, I added a dropdown menu on each page explaining its purpose and functionality.

Throughout this phase, I collaborated closely with my team to debug each other’s code, refine the user interface, and prepare for our final presentation