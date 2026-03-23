---
title: Contact
nav:
  order: 5
  tooltip: Email, address, and location
---

# {% include icon.html icon="fa-regular fa-envelope" %}Contact


{%
  include button.html
  type="email"
  text="jbo.li@must.edu.mo"
  link="bo.li@must.edu.mo"
%}
{%
  include button.html
  type="phone"
  text=""
  link=""
%}
{%
  include button.html
  type="address"
  tooltip="Our location on Google Maps for easy navigation"
  link="https://www.google.com/maps"
%}

{% include section.html %}

{% capture col1 %}

{% endcapture %}

{% capture col2 %}


{% endcapture %}

{% include cols.html col1=col1 col2=col2 %}

{% include section.html dark=true %}

{% capture col1 %}
{% endcapture %}

{% capture col2 %}
{% endcapture %}

{% capture col3 %}
{% endcapture %}

{% include cols.html col1=col1 col2=col2 col3=col3 %}
