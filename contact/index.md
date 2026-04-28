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
  text="bo.li@must.edu.mo"
  link="bo.li@must.edu.mo"
%}
{%
  include button.html
  type="address"
  tooltip="Our location on Google Maps for easy navigation"
  link="https://www.google.com/maps/search/Macau+University+of+Science+and+Technology"
%}

{% include section.html %}

{% capture col1 %}

**Bo Li Laboratory**
Precision Regenerative Medicine Research Centre
Macau University of Science and Technology
Macau SAR, China

Main Office: ITC-01, Innovation and Technology Centre
Email: bo.li@must.edu.mo

Our research activities are based in Macau and Hengqin.

{% endcapture %}

{% capture col2 %}

We welcome inquiries regarding research collaborations, postgraduate training, and postdoctoral opportunities.

{% endcapture %}

{% include cols.html col1=col1 col2=col2 %}

{% include section.html %}

<div class="row">
  <div class="col">
    {%
      include figure.html
      image="images/map1.png"
      caption="Macau campus location"
      link="https://www.google.com/maps/search/Macau+University+of+Science+and+Technology"
    %}
  </div>
  <div class="col">
    {%
      include figure.html
      image="images/map2.png"
      caption="Hengqin campus location"
      link="https://www.google.com/maps/search/Macau+University+of+Science+and+Technology+Hengqin"
    %}
  </div>
</div>
