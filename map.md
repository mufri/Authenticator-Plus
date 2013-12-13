---
 layout: default
 title: Sitemap Policy
---
 - [http://{{ site.domain }}][1]
{% for page in site.posts %}
    - http://{{ site.domain }}{{ page.url }}
{% endfor %}

{% for page in site.html_pages %}

 - http://{{ site.domain }}{{ page.url }}

{% endfor %}


  [1]: http://%7B%7B%20site.domain%20%7D%7D%20http://%7B%7B%20site.domain%20%7D%7D