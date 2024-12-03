---
layout: default
img: ATOMIC.png
img_link: https://doi.org/10.1609/aaai.v33i01.33013027
caption: "ATOMIC: An Atlas of Machine Commonsense for If-Then Reasoning"
title: COMET-ATOMIC Schema
type: Homework
number: 5
active_tab: homework
release_date: 2024-11-18
due_date: 2024-12-09 23:59:00EST
materials:
    - 
        name: HW 5 Python Notebook
        url: hw5.ipynb
submission_link: https://blackboard.umbc.edu/ultra/courses/_82444_1/outline/assessment/test/_7156635_1?courseId=_82444_1&gradeitemView=details
readings:
    -
      title: "(COMET-)ATOMIC-2020: On Symbolic and Neural Commonsense Knowledge Graphs"
      authors: Jena D. Hwang, Chandra Bhagavatula, Ronan Le Bras, Jeff Da, Keisuke Sakaguchi, Antoine Bosselut, and Yejin Choi
      url: https://ojs.aaai.org/index.php/AAAI/article/view/16792
    -
      title: "ATOMIC: An Atlas of Machine Commonsense for If-Then Reasoning"
      authors: Maarten Sap, Ronan Le Bras, Emily Allaway, Chandra Bhagavatula, Nicholas Lourie, Hannah Rashkin, Brendan Roof, Noah A. Smith, and Yejin Choi
      url: https://doi.org/10.1609/aaai.v33i01.33013027
    -
      title: "COMET: Commonsense Transformers for Automatic Knowledge Graph Construction"
      authors: Antoine Bosselut, Hannah Rashkin, Maarten Sap, Chaitanya Malaviya, Asli Celikyilmaz, and Yejin Choi
      url: https://aclanthology.org/P19-1470/
---

<!-- Check whether the assignment is ready to release -->
{% capture today %}{{site.time | date: '%Y%m%d'}}{% endcapture %}
{% capture due_date %}{{page.due_date | date: '%Y%m%d'}}{% endcapture %}
{% if due_date < today %} 
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
This assignment is due on {{ page.due_date | date: "%A, %B %-d, %Y" }} at {{ page.due_date | date: "%I:%M%p" }} EST. 
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
## Learning Objectives
* Create a schema using a commonsense knowledge base.
* Define the boundaries of your schema.
* Determine when/what knowledge bases should be used for a given task.

## Instructions

[ATOMIC](https://ojs.aaai.org/index.php/AAAI/article/view/4160) is a crowdsourced commonsense knowledge graph that is used for state-of-the-art commonsense reasoning tasks. In this homework, you will be working with [COMET-ATOMIC-2020](https://ojs.aaai.org/index.php/AAAI/article/view/16792), a [BART](https://aclanthology.org/2020.acl-main.703/) (encoder-decoder) model finetuned on an updated version of the original ATOMIC. You will take the information provided to you by COMET-ATOMIC-2020 and structure it into a schema used to track the state of a story. (A schema is a structured representation.)

Go to the [Python notebook]({{page.materials[0].url}}) for more information.

### Part 1: Creating a Schema
You will be filling in 4 methods in the code:
* **checkPrecondition**: check whether or not a pre-condition passes
* **getPreconditions**: query COMET to get relevant pre-conditions for a given event
* **getEffects**: query COMET to get relevant effects for a given event
* **updateSchema**: update the story state to reflect these new pre-conditions & effects

1. (3 pts) Explain how you made your schema. (e.g., Why did you decide to design it the way you did? What are your inputs and outputs?) (1 paragraph)
You can test how your schema does on the "testing call". **Once your schema is finalized, uncomment out the 5 story blocks**, and then answer the following questions for each story:

	2-6. (1 pt each) What went well when processing this story? What went poorly? (2-3 sentences)


### Part 2: Questions about COMET-ATOMIC
Answer each of the following with a couple of sentences:

1.   (2 pts) What types of stories might COMET-ATOMIC be *good* at tracking in general? In other words, what types of information is it good at modeling? (It might help to think about how COMET-ATOMIC compares to other knowledge bases.)
2.   (2 pts) What types of stories might COMET-ATOMIC be *bad* at tracking in general?

   2a. (4 pts) Do you think any of the other knowledge bases mentioned in class could better model these? Which ones and why? If none of them could, why not?

## What to Submit

1. An iPython notebook called `hw5.ipynb` that runs your COMET-ATOMIC schema. **Important: Save the output for the Story Tracking Questions!**
2. A pdf that has **your schema explanation and the answers to the COMET-ATOMIC questions** (Parts 1 & 2 above).

Submissions should be done on [Blackboard]({{page.submission_link}}).

## Grading
<div class="alert alert-warning" markdown="1">
* Code - 4 points + 2 points extra credit
* Schema Explanation - 3 points
* Story Tracking Questions - 5 points
* COMET-ATOMIC Questions - 8 points
</div>

{% if page.readings %} 
## Related Readings
{% for reading in page.readings %}
* {{ reading.authors }}, <a href="{{ reading.url }}">{{ reading.title }}</a>.  <i>{{ reading.note }}</i>
{% endfor %}
{% endif %}

