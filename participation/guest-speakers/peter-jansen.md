---
layout: default
img: scienceworld.jpg
img_link: https://cognitiveai.org
caption: Science World
title: think of questions for Peter Jansen
type: participation
speaker: Peter Jansen
active_tab: homework
release_date: 2024-01-18
due_date: 2024-01-25 13:45:00EST
materials:
submission_link: https://www.gradescope.com/courses/704268/assignments/3964459/
---

<!-- Check whether the assignment is ready to release -->
{% capture today %}{{'now' | date: '%s'}}{% endcapture %}
{% capture release_date %}{{page.release_date | date: '%s'}}{% endcapture %}
{% if release_date > today %} 
<div class="alert alert-danger">
Warning: this assignment is out of date.  It may still need to be updated for this year's class.  Check with your instructor before you start working on this assignment.
</div>
{% endif %}
<!-- End of check whether the assignment is up to date -->



{% if page.type == "in-class" %}
<!-- In class activity -->
<div class="alert alert-info">
This is the in-class activity for {{ page.release_date | date: "%A %B %-d" }}.
</div>
{% elsif page.type == "participation" %}
<div class="alert alert-info">
This activity counts towards your participation grade. It is due on {{ page.due_date | date: "%A, %B %-d, %Y" }} before {{ page.due_date | date: "%I:%M%p" }}. 
</div>
{% else %}
<!-- Homework assignment -->
<div class="alert alert-info">
This assignment is due on {{ page.due_date | date: "%A, %B %-d, %Y" }} before {{ page.due_date | date: "%I:%M%p" }}. 
</div>

{% endif %}

{% if page.materials %}
<div class="alert alert-info">
The materials that you will need for this activity are:
<ul>
{% for item in page.materials %}
<li><a href="{{item.url}}">{{ item.name }}</a></li>
{% endfor %}
</ul>
</div>
{% endif %}



Participation Activity: Research Our Guest Speaker
=============================================================

We'll have several guest speakers this semester, including game designers, AI professors and industrial researchers.  For each speaker, you should learn a bit about them before they give their talk, and prepare at least one question that you'd like us to ask them to hear their insights about our course topics. 

You should [submit your question to gradescope]({{page.submission_link}}), along with a short bio for the speaker and the websites that you used to research them  before class begins.

On {{ page.due_date | date: "%A, %B %-d, %Y" }} our guest speaker will be **{{ page.speaker }}**.
