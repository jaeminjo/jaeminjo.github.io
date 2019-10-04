---
layout: post
title: Publications
order: 1
---
{% assign publications = site.data.publications %}
{% assign international_publications = publications | where_exp: "item", "item.attrs contains 'international'" | group_by: "year" | sort: "name" | reverse %}
{% assign domestic_publications = publications | where_exp: "item", "item.attrs contains 'domestic'" | group_by: "year" | sort: "name" | reverse %}
{% assign papers = publications | where_exp: "item", "item.type == 'Paper'" | group_by: "year" | sort: "name" | reverse %}

{% assign others = "" | split: "" %}
{% for pub in publications %}
{% if pub.type =='Poster' or pub.type == 'Patent' %}
{% assign others = others | push:pub %}
{% endif %}
{% endfor %}
{% assign others = others | group_by: "year" | sort: "name" | reverse %}

<h2>Peer-reviewed Papers</h2>

{% for year in papers %}
{% assign sorted = year.items | sort: "index" %}
{% for pub in sorted %}
{% include publication.html pub = pub %} 
{% endfor %}
{% endfor %}

<h2>Posters and Patents</h2>

{% for year in others %}
{% assign sorted = year.items | sort: "index" %}
{% for pub in sorted %}
{% include publication.html pub = pub %} 
{% endfor %}
{% endfor %}