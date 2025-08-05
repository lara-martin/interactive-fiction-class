---
layout: default-2024
img: estimating_time.png
caption: Don't Panic
img_link: https://xkcd.com/1658/
title: Project Progress
type: Project Milestone
number: 2
active_tab: homework
release_date: 2024-10-08
due_date: 2024-10-28 23:59:00EST
submission_link: 
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


<!-- Check whether the assignment is up to date -->
{% capture this_year %}{{'now' | date: '%Y'}}{% endcapture %}
{% capture due_year %}{{page.due_date | date: '%Y'}}{% endcapture %}
{% if this_year != due_year %} 
<div class="alert alert-danger">
Warning: this assignment is out of date.  It may still need to be updated for this year's class.  Check with your instructor before you start working on this assignment.
</div>
{% endif %}
<!-- End of check whether the assignment is up to date -->


<div class="alert alert-info">
This assignment is due on {{ page.due_date | date: "%A, %B %-d, %Y" }} before {{ page.due_date | date: "%I:%M%p" }}. 
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


{{page.type}} {{page.number}}: {{page.title}}
=============================================================

By now, you should have made some progress on your project. This milestone will flesh out some of the components of your project from the proposal. Be sure to read the appropriate section for your project type below as the requirements start to diverge.


## Demo: Build a novel interactive experience
For this milestone, you will describe your demo in more detail. The milestone after this one will have a shorter report needed but will require a somewhat-working demo.

Write a report that includes the following sections:
1. __Project Description__: What novel interactive experience do you propose to design? (This will collapse the __Project Description__ and __Related Work__ sections from your proposal into one section.)
  - Do similar games/experiences exist to the one you propose to create? Give pointers to them and explain how you think they relate to your project idea. What were your inspirations?
  - Include a repo link to your code (as it is so far) in this section.
2. __Front End__: What will the user interact with?
  - Give an example mockup of what the user experience will look like. (Also consider: will there be any graphics or AI-generated images?)
  - Describe how you expect users to interact with the system. For example, if this is a game, what types of input will it take/will you be parsing commands?
3. __Back End Architecture__: What does the overall architecture of your system look like? 
  - Describe how your architecture will work.
  - Give an example diagram of the backend system (the pipeline of components).
4. __Back End Details__: What will each component of your pipeline be?
  - If you are using any datasets, does the needed data already exist?  If so, how much data is available? What does the data look like? If you are just using a few examples for few-shot prompting, how did you select those?
  - If you are using few- or zero-shot prompting, what do your prompts look like?
  - What specific models will you be using? Will they be trained from scratch, finetuned, or just prompted?
5. __Team Members__: Give a list of the students who are participating in this project, and what contributions you have made and expect to make for the project.
  - In this section also mention what you have completed so far and what is still left to do. You won't be graded on how far you've gotten in the project, but obviously the further you get, the less you'll have to scramble last-minute.
6. __LLM Use Statement__: Describe exactly how you used LLMs to generate parts of your proposal document (<a href="https://laramartin.net/interactive-fiction-class/index.html#using-llms-or-generative-ai">refer to the syllabus for guidance</a>). If you did not use **any** generative text, please state so in this section.

### Grading
<div class="alert alert-warning" markdown="1">
You will get full points if you 1) include all of the material listed above and 2) incorporate the feedback you got from the previous submission.<br>

* Project Description - 5 points
* Front End - 5 points
* Back End Architecture - 5 points
* Back End Details - 5 points
* Team Members - 2 points
* LLM Use Statement - 1 point

Total: 23 points
</div>


## Paper: Attempt to answer a research question about text generation or interactive fiction
For this milestone, you will take the components of your proposal and begin to move them into more "paper-like" sections. You will also be adding in some more details.

While not required at this stage, we highly recommend that you use LaTeX and a conference template. If you do not have a conference/workshop in mind, I recommend that you use the [template from the Association for Computational Linguistics](https://www.overleaf.com/latex/templates/association-for-computational-linguistics-acl-conference/jvxskxpnznfj).

Your paper should include the following sections:
1. __Introduction__: What research question(s) or problem are you trying to solve? (This is where your problem definition from the __Project Description__ of your proposal goes.)
  - Why this it worth researching?
  - What contributions does this work make? (i.e., What are you doing that's novel?)
2. __Related Work__: What previous research has been done on this research question?
  - Turn your previous list of citations into a little narrative of what has been done previously in the field. Take a look at some previously-published papers to see how they write their related works section.
3. __Methods__: What are you doing or making to address your research question(s)?
  - If you are using any datasets, does the needed data already exist?  If so, how much data is available? What does the data look like? If you are just using a few examples for few-shot prompting, how did you select those?
  - Describe your solution to the problem/research question. What model(s) are you using? If you are using few- or zero-shot prompting, what do your prompts look like?
4. __Experiments__: What experiments will you be running?
  - What are you measuring and why? What evaluation metrics do you plan to use to answer your research question(s)?
  - What are your proposed *baselines*? (That is, what are you comparing your method against?)
  - How do these experiments answer your research questions?
5. __Team Members__: Give a list of the students who are participating in this project, and what contributions you have made and expect to make for the project.
  - In this section also mention what you have completed so far and what is still left to do. You won't be graded on how far you've gotten in the project, but obviously the further you get, the less you'll have to scramble last-minute.
6. __LLM Use Statement__: Describe exactly how you used LLMs to generate parts of your proposal document (<a href="https://laramartin.net/interactive-fiction-class/index.html#using-llms-or-generative-ai">refer to the syllabus for guidance</a>). If you did not use **any** generative text, please state so in this section.

### Grading
<div class="alert alert-warning" markdown="1">
You will get full points if you 1) include all of the material listed above and 2) incorporate the feedback you got from the previous submission.<br>

* Introduction - 5 points
* Related Work - 5 points
* Methods - 5 points
* Experiments - 5 points
* Team Members - 2 points
* LLM Use Statement - 1 point

Total: 23 points
</div>

# What to Submit
Submit the following to [Blackboard]({{page.submission_link}}):
* `team#-milestone2.pdf` which contains your milestone 2 submission. To make grading easier, your proposal should include section headers corresponding to each of the bulleted points as well. 



