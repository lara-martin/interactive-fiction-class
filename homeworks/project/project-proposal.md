---
layout: default
img: estimating_time.png
caption: Don't Panic
img_link: https://xkcd.com/1658/
title: Project Proposal
type: Project Milestone
number: 1
active_tab: homework
release_date: 2024-09-22
due_date: 2024-09-30 23:59:00EST
submission_link: https://blackboard.umbc.edu/ultra/courses/_82444_1/outline/assessment/test/_7135696_1?courseId=_82444_1&gradeitemView=details
gen_policy: "https://laramartin.net/interactive-fiction-class/index.html#using-llms-or-generative-ai"

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
<br><br>
Please reacquaint yourself with the <a href="{{gen_policy}}">course's text generation policy</a>.
<br>
And then <a href="{{submission_link}}">submit a pdf of your proposal here</a>.
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

The project is a chance for you to delve into one of the topics we have covered in class. You can choose between two directions: creating a novel interactive experience or answering a research question. The final deliverable will a poster presentation and either a **demo** or a **paper**.

If you are trying to decide between multiple project ideas, or if you're struggling to come up with something, we highly encourage you to come to office hours and discuss it with Dr. Martin. She will be able to help you narrow down which ideas of yours are the most feasible + interesting.

For this milestone, you will pick whether you are doing a demo or a paper and then write a project proposal that contains the following sections. Guiding questions are given to help you fill out each section.

## Demo: Build a novel interactive experience
Use the techniques we have learned in class to build a novel interactive experience that involves generated text. While fine-tuning a large language model on a custom dataset or few-shot prompting your model could be a _component_ of your project, we are expecting something more involved than just this. Can you expand on the homeworks to build a text-based game that uses language models to make a novel and fun game experience? Can you incorporate elements of classical planning or dialogue systems into your generation? By the end of the semester, you should have a demo that runs either in a Python Notebook or on a website showcasing your interactive experience.

Write a project proposal that includes the following sections:
1. __Project Description__: What novel interactive experience do you propose to design? You're not stuck with whatever design decisions you make here, but this will be your starting point.
  - Give an example mockup of what the user experience will look like.
2. __Data__: What data will be needed to build your interactive experience?
  - Does the needed data already exist?  If so, how much data is available?  
  - What does the data look like?
3. __Proposed Method__: How will you be using text generation systems or other concepts from class in order to enable the interactive experience? Will you need to train your own neural networks?
  - Write 2-3 paragraphs explaining your proposed method.
  - Give an example diagram of the backend system.
4. __Related work__: Do similar games/experiences exist to the one you propose to create?
  - Give pointers to them and explain how you think they relate to your project idea.
5. __Team members__: Give a list of the students who will participate in this project, and what contribution you expect each one to make to the project.
6. __LLM Use Statement__: Describe exactly how you used LLMs to generate parts of your proposal document (<a href="{{gen_policy}}">refer to the syllabus for guidance</a>). If you did not use **any** generative text, please state so in this section.


## Paper: Attempt to answer a research question about text generation or interactive fiction
In class, we have discussed multiple open questions related to text generation. Choose one of these questions and conduct experiments to attempt to answer the question. By the end of the semester, you should have an academic paper that describes the research question, the experiments you ran to try and answer it, and an analysis of the experimental results.

<div class="alert alert-info">
If you are interested in trying to submit a paper to a conference or workshop (aka publish the work), please state this at the top of your paper in bold. This won't affect your grade but will affect the thoroughness of feedback you get.
</div>

Write a project proposal that includes the following sections:
1. __Project Description__: What research question or problem are you trying to solve?
  - Write a problem definition (1 to 2 paragraphs)
  - Give an illustrative example of the problem and/or your proposed solution.
2. __Data__: What kind of data will you need to train and evaluate your method?
  - Does the needed data already exist?  If so, how much data is available?
  - What does the data look like?
3. __Evaluation__: What are you measuring and why?
  - What evaluation metrics do you plan to use to answer your research question?
4. __Related work__: What previous research has been done on this research question?
  - Give citations to several research papers that you think are relevant along with short explanations of how you think they relate to your project idea. This can be a list with summaries of the papers for now and you will turn it into a proper Related Work section later.
5. __Team members__: Give a list of the students who will participate in this project, and what contribution you expect each one to make to the project.
6. __LLM Use Statement__: Describe exactly how you used LLMs to generate parts of your proposal document (<a href="{{gen_policy}}">refer to the syllabus for guidance</a>). If you did not use **any** generative text, please state so in this section.

# What to Submit
Submit to Blackboard:
* `team#-proposal.pdf` which is your project proposal. To make grading easier, your proposal should include section headers corresponding to each of the bulleted points as well.


# Grading
<div class="alert alert-warning" markdown="1">
* Project Description - 5 points
* Data - 3 point
* Proposed Method or Evaluation - 3 points
* Related Work - 1 point
* Team Members - 1 point
* LLM Use Statement - 1 point

Total: 14 points
</div>
