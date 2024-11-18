---
layout: default
img: estimating_time.png
caption: Don't Panic
img_link: https://xkcd.com/1658/
title: Rough Draft
type: Project Milestone
number: 3
active_tab: homework
release_date: 2024-11-16
due_date: 2024-11-25 23:59:00EST
submission_link: https://blackboard.umbc.edu/ultra/courses/_82444_1/outline/assessment/test/_7180658_1?courseId=_82444_1&gradeitemView=details
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

At this stage you will be starting to wrap things up. Again, be sure to read the appropriate section for your project type to learn more about the requirements for this milestone.


## Demo: Build a novel interactive experience
You should have a semi-working system in place. For this deliverable, you will need to share a 5-10 minute video showing the various components of what you have working so far. Not everything needs to be completed. **You are allowed to have placeholders in the code for components that are incomplete.** For this reason, we are asking you to submit a video instead of having you write a report and us trying to run the code ourselves.


Your video should include the following things:
1. __Description__: A high-level description of the your system.
	- What have you been making?
	- What will it be like? (e.g., What do you imagine people will use this tool for? or What sort of game/experience will this be?)
2. __Algorithm Explanation__: An explanation of the algorithm(s)/model(s) of the system, while showing the code for them.
	- Be sure to include plenty of details where relevant, such as: how you are using the models, what prompts you use, what symbolic components you are using, or how you are using datasets or knowledge bases. Feel free to use anything you wrote about from the **Back End Details** of your previous milestone.
3. __End-to-end Example__: An example of how it looks or will look when someone uses your system. (For example, a playthrough of part of your game.)
	- This is basically showing the interface and demonstrating how all of the pieces go together; i.e., the **Front End** section from Milestone 2 but in video format.

You do not need to talk about your inspirations for the project at this stage, unless you think they are relevant. The video does not need to include a slide show unless you feel that it will improve your explanation of the system.


In a separate document called `team#-supplement.pdf`, include:
1. __Title__: What are you calling your system?
2. __System Diagram__: This might be in something formal like [UML](https://slickplan.com/blog/how-to-make-a-uml-diagram) or a more informal format, but it should include more details than your **Back End Architecture** diagram(s) from the previous milestone probably had.
3. __Team Members__: Give a list of the students who are participating in this project, and what contributions you have made and expect to make for the project.
  - In this section also mention what you have completed so far and what is still left to do.
4. __LLM Use Statement__: Describe exactly how you used LLMs to generate **parts of your code** (<a href="https://laramartin.net/interactive-fiction-class/index.html#using-llms-or-generative-ai">refer to the syllabus for guidance</a>). If you did not use **any** generative text, please state so in this section.

### Grading
<div class="alert alert-warning" markdown="1">
You will get full points if you 1) include all of the material listed above and 2) incorporate the feedback you got from the previous submission.<br>


* Title - 1 point
* Code - 2 points
* System Diagram  - 3 points
* Video: Description - 5 points
* Video: Algorithm Explanation - 10 points
* Video: End-to-end Example - 5 points
* Team Members - 2 points
* LLM Use Statement - 1 point

Total: 29 points
</div>

### What to Submit
Submit the following to [Blackboard]({{page.submission_link}}):
* The link to your repository.
* Your video or a link to where your video is hosted.
* `team#-supplement.pdf`

## Paper: Attempt to answer a research question about text generation or interactive fiction

To help you, here are some example reports from previous classes:
* [Example Report 1](example_report-2022-1.pdf)
* [Example Report 2](example_report-2022-2.pdf)
* [Example Report 3](example_report.pdf)

For this milestone, you will take the components of your proposal and begin to move them into more "paper-like" sections. You will also be adding in some more details.

Your paper needs to be in a conference template, written in LaTeX.
* You can use [Overleaf](https://www.overleaf.com) to write LaTeX papers together. The CSEE department has a subscription to Overleaf now, so you should be able to have multiple collaborators on the same paper.
* If you do not have a conference/workshop in mind, I recommend that you use the [template from the Association for Computational Linguistics](https://www.overleaf.com/latex/templates/association-for-computational-linguistics-acl-conference/jvxskxpnznfj).




Your paper should include the following sections:
<div class="alert alert-warning" markdown="1">
Note that at this stage the questions below are *guiding* questions. Do not include the questions themselves in your paper and make sure that what you write in each section builds to be one cohesive section. Your content in each section should contain information beyond these questions as well.
</div>

Discussion and Conclusion sections will be added in the final deliverable.

1. __Title__: What are you calling your study?
1. __Abstract__: A high-level 
2. __Introduction__: What research question(s) or problem are you trying to solve?
<div class="alert alert-warning" markdown="1">
<b>Science 101</b><br>
A *research question* should be **something that can be proved true or false.** An example of a *bad* research question might be "Which dog is the best dog?" because it cannot be rejected (i.e., null hypothesis). <br> A *better* way to rephrase this---by potentially looking at the same problem---would be to ask "Is Pharaoh a good dog?". This can then be tested. You just need to define how to measure "goodness" in this case.
</div>
  - Why this it worth researching?
  - What contributions does this work make? (i.e., What are you doing that's novel?) You might have to compare to other research.
3. __Related Work__: What previous research has been done on this research question?
  - I want you to do a deeper dive of the related work now. Find *at least five more papers* to add to the narrative you've written so far.
4. __Methods__: What are you doing or making to address your research question(s)?
  - If you are using any datasets, does the needed data already exist?  If so, how much data is available? What does the data look like? If you are just using a few examples for few-shot prompting, how did you select those?
  - Describe your solution to the problem/research question. What model(s) are you using? If you are using few- or zero-shot prompting, what do your prompts look like?
5. __Evaluation__: *Renamed from Experiments section* What experiments will you be running?
  - What are you measuring and why? What evaluation metrics do you plan to use to answer your research question(s)?
  - What are your proposed *baselines*? (That is, what are you comparing your method against?)
  - How do these experiments answer your research questions?
6. __Results__: What did you find from your evaluation?
	- This should be more than just a list of raw numbers. You should explain to the reader how to interpret any graphs or tables you have and describe any trends that you see.
	- It's okay if you don't have all of your results yet! Just report what you have so far. 
<!--8. __Conclusion__: In CS, this is often just a brief paragraph reminding people what the highlights of your paper were.-->
9. __References__: Papers are cited correctly in the conference's format and are references in the main text.

In a separate document called `team#-supplement.pdf`, write:
1. __Team Members__: Give a list of the students who are participating in this project, and what contributions you have made and expect to make for the project.
  - In this section also mention what you have completed so far and what is still left to do.
2. __LLM Use Statement__: Describe exactly how you used LLMs to generate parts of your paper (<a href="https://laramartin.net/interactive-fiction-class/index.html#using-llms-or-generative-ai">refer to the syllabus for guidance</a>). If you did not use **any** generative text, please state so in this section.

### Grading
<div class="alert alert-warning" markdown="1">
You will get full points if you 1) include all of the material listed above and 2) incorporate the feedback you got from the previous submission.<br>

* Title - 1 point
* Abstract - 2 points
* Introduction - 5 points
* Related Work - 5 points
* Methods - 5 points
* Evaluation - 5 points
* Results - 2 points
* References - 1 points
* Team Members - 2 points
* LLM Use Statement - 1 point

Total: 29 points
</div>

### What to Submit
Submit the following to [Blackboard]({{page.submission_link}}):
* `team#-roughdraft.pdf` which is your draft.
* `team#-supplement.pdf`, the supplemental material mentioned above.



