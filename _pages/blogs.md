---
title:              "Blogs"
layout:             archive
permalink:          /Blogs/
author_profile:     true
comments:           true
---
This is my blog page. Better late than never.. !!

{% for post in site.posts %}
    {%include archive-single.html %}
{% endfor %}