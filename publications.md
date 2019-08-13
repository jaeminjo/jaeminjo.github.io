---
layout: post
title: Publications
order: 1
---
{% assign publications = site.data.publications %}
{% assign international_publications = publications | where_exp: "item", "item.attrs contains 'international'" | group_by: "year" | sort: "name" | reverse%}
{% assign domestic_publications = publications | where_exp: "item", "item.attrs contains 'domestic'" | group_by: "year" | sort: "name" | reverse %}


<h2>International</h2>

{% for year in international_publications %}
{% assign sorted = year.items | sort: "index" %}
{% for pub in sorted %}
{% include publication.html pub = pub %} 
{% endfor %}
{% endfor %}

<h2>Domestic</h2>


{% for year in domestic_publications %}
{% assign sorted = year.items | sort: "index" %}
{% for pub in sorted %}
{% include publication.html pub = pub %} 
{% endfor %}
{% endfor %}