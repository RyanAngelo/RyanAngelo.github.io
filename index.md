---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---
{% include nav.html %}

# About
The ability for software to solve problems, improve quality of life, and open new opportunities is what makes programming a passion. I hope to develop projects and ideas that explore the ever-evolving field of Computer Science.

{% include_relative project_pages/project_summary.md %}

# Posts
{% for post in site.posts limit:5 %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
{% endfor %}