---
layout: default
title: Make your own mini script
type: in-class
active_tab: homework
release_date: 2024-09-24
due_date: 2024-10-01 23:59:00EST
submission_link: https://blackboard.umbc.edu/ultra/courses/_82444_1/outline/assessment/test/_7137009_1?courseId=_82444_1&gradeitemView=details
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
{% else %}
<!-- Homework assignment -->
<div class="alert alert-info">
This assignment is due on {{ page.due_date | date: "%A, %B %-d, %Y" }} before {{ page.due_date | date: "%I:%M%p" }}. 
</div>

{% endif %}

{% if page.materials %}
<div class="alert alert-info">
The materials that you will need for this in-class activity are:
<ul>
{% for item in page.materials %}
<li><a href="{{item.url}}">{{ item.name }}</a></li>
{% endfor %}
</ul>
</div>
{% endif %}



In Class Activity: Make Your Own Mini Script
=============================================================

Now that you've seen a bit about what scripts can be, make your own on your own or in pairs!
Specifically, you will make a graph to represent a script for "checking out at the grocery store"

### What to do

1. Open [draw.io](draw.io) or get out pen/pencil and paper
2. Make a graph like the "ordering at a restaurant" one seen in class but for "checking out at the grocery store"
3. Save as a picture file (e.g., png or jpeg) or take a picture of the piece of paper
4. Submit to [Blackboard]({{page.submission_link}}) by {{ page.due_date | date: "%A, %B %-d, %Y" }} before {{ page.due_date | date: "%I:%M%p" }}. 

