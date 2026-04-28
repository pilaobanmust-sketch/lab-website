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

{% include section.html %}

## Collaborative Network

Our work is supported by collaborations across Macau, Mainland China, and international partner institutions.

{% capture col1 %}

**Macau and Greater Bay Area**

- Zhuhai Maternal and Child Health Hospital
- Centro Hospitalar Conde de São Januário (Macau)

**Mainland China**

- Shanghai Children's Hospital
- Capital Institute of Pediatrics
- Shengjing Hospital of China Medical University

{% endcapture %}

{% capture col2 %}

**International**

- The Hospital for Sick Children, Toronto
- Great Ormond Street Hospital, London

{% endcapture %}

{% include cols.html col1=col1 col2=col2 %}

{% include section.html background="images/background.jpg" dark=true %}
