---
layout: default
img: presentation.jpg
img_link: https://www.learner.org/wp-content/uploads/2020/05/two-bit-circus-lesson-plans-unit-elementary-school-engineering-towers-group-presentation-1298x672.jpg
title: Paper Presentation
active_tab: homework
release_date: 2024-09-10
attribution: This homework was developed by Lara Martin and Chris Callison-Burch for their Interactive Fiction and Text Generation class (CIS 700-008) which was taught at the University of Pennsylvania in Spring 2022.
submission_link: https://blackboard.umbc.edu/ultra/courses/_82444_1/outline/assessment/Test/_7121736_1?courseId=_82444_1&gradeitemView=details&gradebookCategoryId=_24131213_1&assessmentSubtype=Assignment

---

<div class="alert alert-info">
This assignment is due 5PM EST the day before your presentation. 
</div>

{% if page.materials %}
<div class="alert alert-info">
You can download the materials for this assignment here:
<ul>
{% for item in page.materials %}
<li><a href="{{item.url}}">{{ item.name }}</a></li>
{% endfor %}
</ul>
</div>
{% endif %}


{{page.title}}
=============================================================

This assignment is to measure your ability to...
* critically read academic papers
* apply techniques and methods mentioned in the paper to other scenarios

# Instructions

Once you are assigned a paper, you will be told the approximate date when your presentation will be. (Since the lecture material moves around as the course progresses, the presentation dates might move as well.)

Your presentation should be about 8 minutes long + a few minutes for questions.

Your talk should include:
- a summary of the paper,
- what the strengths of the paper are,
- what the weaknesses of the paper are, and
- how it relates to story generation and interactive fiction playing/generation
   - if it's not about either, how could it be used for making stories or interactive fiction?
   - if it's about story generation, how could it be used for creating or playing interactive fiction?
   - if it's about interactive fiction, how could it be used for story generation?

# Rubric

| Criteria | Possible Points| Description|
|---------|-------------------|-------------|
|Summary| 4 points | High-level summary that explains the key points of the paper without going into unnecessary detail, but explains concepts that might be unknown to the class |
| Strengths | 4 points | A few strengths of the paper compared to other work in the field|
|Weaknesses | 4 points | A few weaknesses of the paper compared to other work in the field|
|Relation to storytelling/IF | 4 points | Thoughtful application of techniques/methods of the paper to IF or storytelling or both|
|Length | 1 point | Presentation is about 8 minutes long |
|Slides| 3 points| Slides are organized/look professional, not overly wordy, and not just copying text from the paper|


## What to submit

1. <a href="{{page.submission_link}}">A Powerpoint (ppt or pptx) file or a link to where we can find the slides online (e.g., Google Slides).</a>


