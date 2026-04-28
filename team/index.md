---
title: Team
nav:
  order: 3
  tooltip: About our team
---

# {% include icon.html icon="fa-solid fa-users" %}Team

We are building a collaborative, interdisciplinary, and internationally connected research team dedicated to understanding gut remodeling and regeneration in development, injury, and disease. We welcome students, fellows, and collaborators who share these interests.

{% include section.html %}

{% include list.html data="members" component="portrait" filter="role == 'principal-investigator'" %}

{% include list.html data="members" component="portrait" filter="role == 'postdoc'" %}

{% include list.html data="members" component="portrait" filter="role == 'phd'" %}

{% include section.html background="images/background.jpg" dark=true %}
