---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---
{% include nav.html %}

# About
Hi! My name is Ryan. I am a Software Engineer who likes to create small projects and learn new things.

{% include_relative project_pages/project_summary.md %}

# Posts
{% for post in site.posts limit:5 %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
{% endfor %}