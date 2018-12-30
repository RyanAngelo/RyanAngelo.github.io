---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---
{% include nav.html %}

# About
The ability for software to solve problems, improve quality of life, and open new opportunities is what makes programming a passion. I hope to develop projects and ideas that explore the ever-evolving field of Computer Science.

# Projects
[Around The Clock](/aroundtheclock) A simple, elegant time keeping application written in Swift for MacOS

[Goal Guardian](https://github.com/RyanAngelo/goalguardian) iOS application for keeping track of goals and executing on them

[Time Guardian](https://github.com/RyanAngelo/timeguardian) iOS application for keeping track of the amount of time that you work on different tasks

# Posts
{% for post in site.posts limit:5 %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
{% endfor %}