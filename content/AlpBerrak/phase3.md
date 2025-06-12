---
title: "Phase 3 Deliverable"
date: 2025-06-05
draft: false
description: "Phase 3 Individual Deliverable"
slug: "phase3alp"   # if you use, needs to be different for every post
tags: ["authors", "config", "docs"]
authors:
  - "alpberrak"
showAuthorsBadges : false
---

# Phase Three Blog Post
During this phase, significant progress was made, particularly with features tailored to the diplomat persona. My primary focus was implementing the routes used by the EU Commissioner (to be renamed later) and designing the corresponding user interface and sidebar. This interface includes four pages—two of which currently contain placeholder data that will be finalized in Phase 4. One of the functional pages retrieves data from SQL tables to display each country's ratio of accepted refugee applications to its population. This is presented in a bar chart that can show all countries, the top ten, or the bottom ten, using a simple GET request.

Another key feature under development is the aid projects page. Although the chart meant to visualize aid projects by country is not yet functioning correctly, it is in progress. Below the chart, there's a form allowing users to submit (POST) new aid project suggestions, with functionality to edit (PUT) their own submissions already in place. The option to delete user-submitted projects is also planned for the near future.

This phase also came with its share of challenges, many of which required close collaboration with my teammates. A problematic merge created issues that led us to learn how to revert pull requests effectively. I also encountered repeated Docker crashes, which required considerable debugging to restore container functionality. Additionally, understanding how the various routes and data structures connected demanded ongoing communication and coordination within the team.