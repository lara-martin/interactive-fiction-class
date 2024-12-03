---
layout: default
img: estimating_time.png
caption: Don't Panic
img_link: https://xkcd.com/1658/
title: Final Presentation
type: Project Milestone
number: 4
active_tab: homework
release_date: 2024-11-26
due_date: 2024-12-12 23:59:00EST
submission_link: https://blackboard.umbc.edu/ultra/courses/_82444_1/outline/assessment/test/_7180658_1?courseId=_82444_1&gradeitemView=details
materials:
  -
    name: Poster Template
    url: poster-template.pptx
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



<div class="alert alert-info">
This assignment is due on {{ page.due_date | date: "%A, %B %-d, %Y" }} before {{ page.due_date | date: "%I:%M%p" }}. <br>
The presentation day will be on December 12, 2024 from 10:30am - 12:30pm in Sherman Hall 150.
Posters must be submitted by December 9th or earlier to <a href="https://researchgraphics.umbc.edu/welcome/poster-printing/">Research Graphics</a>.
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

Here are the requirements for the final submission of your project. Please refer to the appropriate section below for your project type.

## How will the presentation day work?

### Getting Ready
* Posters should be size 36 x 42. This can be 42" tall and 36" wide or vice versa. You can print your poster through Research Graphics: [https://researchgraphics.umbc.edu/welcome/poster-printing/](https://researchgraphics.umbc.edu/welcome/poster-printing/). 
	* The CSEE department has generously agreed to pay for the printing of the poster, but you will still have to order and pick it up yourself.
	* Please allow them **at least 3 business days** to approve the file.
	* If you want Dr. Martin to look at your poster before you print it, be sure to give them a couple days before you want to print it.
* I have provided a [poster template]({{page.materials[0].url}}) for you to use. You're welcome to adapt it as much as you like except make sure to keep it 36 x 42 (or 42 x 36).
	* You are not required to use the template at all, but make sure it's the correct size. You can also make a poster in LaTeX, if you prefer.
	* Regardless of the format you choose, **save it as a pdf before sending it to Research Graphics**.
	

### On Presentation Day
* Posters will be either attached to the walls or presented on easels around the room (SHER 150).
* Please be in SHER 150 on time or a bit earlier!! (10:30am on December 12th)
* The presentations will be open to the university, broadly.
* Within your team, designate some members to be "group 1" and the rest to be in "group 2". The first half of the time group 1 will present and group 2 will walk around and look at other posters/demos. Everyone will switch halfway through so that you all get a chance to see each other's work. You don't have to tell us who is in which group; this is just to let you know what's going to happen on presentation day.
* There will be a voting box where visitors can vote for their favorite presentation(s). The team with the most votes will get 3 points of extra credit on Milestone 4.
* **For demo teams**: Please bring a laptop and charger, and have your demo ready to be played with.


### Poster Grading
The posters will be graded on two main criteria:
* __Content__: (8 points) The poster contains enough relevant information that someone can get the highlights of the project without you necessarily presenting (although you will still be presenting it).
	* Information is written in clear language.
	* Contains: 1) an introduction to what you did, 2) information about the methods/system, and 3) any results/discussion (for paper teams) or takeaways (for demo teams).
* __Visuals__: (4 points) The poster contains relevant visuals without overwhelming the reader, and the text organization is nicely displayed.



---

## Demo: Build a novel interactive experience

The final deliverable is the demo itself and a poster. Your demo should be a complete program that can run end-to-end.

Your demo should:
* Be runable by the grader, following the read me.
* Be posted on GitHub (or the repository site of your choice).
* **Not** be edited after the deadline. We will be grading the last commit pushed before the deadline.

In a separate document called `team#-supplement.pdf`, provide the
__LLM Use Statement__: Describe exactly how you used LLMs to generate **parts of your code** (<a href="https://laramartin.net/interactive-fiction-class/index.html#using-llms-or-generative-ai">refer to the syllabus for guidance</a>) **or your poster**. If you did not use **any** generative text, please state so.



### What to Submit
Submit the following to [Blackboard]({{page.submission_link}}):
* The link to your repository.
* `team#-poster.pdf` which is your poster.
* `team#-supplement.pdf`, the LLM use statement.



### Grading
<div class="alert alert-warning" markdown="1">
You will get full points if you 1) include all of the material listed above and 2) incorporate the feedback you got from the previous submission.<br>


* Poster Content - 8 points ([See description above.](#poster-grading))
* Poster Visuals - 4 points
* System Diagram  - 5 points - Updated to reflect your final system. This can also be put onto your poster, if you want.
* Minimal bugs - 5 points - Runs from beginning to end with minimal bugs (1-3 bugs, depending on the size/type of bug).
* Complete - 10 points - The demo does what the previous milestones' architecture claim to do (within reason).
* Read Me - 3 points - A short document explaining what your system is, and how to setup and run your demo. Put this readme in the README.md file of your repository.
* LLM Use Statement - 1 point


Total: 36 points
</div>
---

## Paper: Attempt to answer a research question about text generation or interactive fiction

The final deliverable is the paper itself and a poster. The paper will be a continuation of the same one you've been building on.

Here are some example reports from previous classes again to aid you:
* [Example Report 1](example_report-2022-1.pdf)
* [Example Report 2](example_report-2022-2.pdf)
* [Example Report 3](example_report.pdf)




Your paper needs to be in a conference template, written in LaTeX.
* You can use [Overleaf](https://www.overleaf.com) to write LaTeX papers together. The CSEE department has a subscription to Overleaf now, so you should be able to have multiple collaborators on the same paper.
* If you do not have a conference/workshop in mind, I recommend that you use the [template from the Association for Computational Linguistics](https://www.overleaf.com/latex/templates/association-for-computational-linguistics-acl-conference/jvxskxpnznfj).




Your paper should include the following sections:
<div class="alert alert-warning" markdown="1">
Note that at this stage the questions below are *guiding* questions. Do not include the questions themselves in your paper and make sure that what you write in each section builds to be one cohesive section. Your content in each section should contain information beyond these questions as well.
</div>

<div class="alert alert-warning" markdown="1">
<b>Science 101</b><br>
A *research question* should be **something that can be proved true or false.** An example of a *bad* research question might be "Which dog is the best dog?" because it cannot be rejected (i.e., null hypothesis). <br> A *better* way to rephrase this---by potentially looking at the same problem---would be to ask "Is Pharaoh a good dog?". This can then be tested. You just need to define how to measure "goodness" in this case.
</div>

Your paper should have the following components, in order:

1. __Title__: What are you calling your study?
2. __Abstract__: A high-level overview of the paper and what people should take away from it if they aren't reading the whole thing.
3. __Introduction__: What research question(s) or problem are you trying to solve? (Start numbering sections from here.)
  - Why this it worth researching?
  - What contributions does this work make? (i.e., What are you doing that's novel?) You might have to compare to other research.
4. __Related Work__: What previous research has been done on this research question?
  - I want you to do a deeper dive of the related work now. Find **at least five more papers** (for a total of 8-10+) to add to the narrative you've written so far.
5. __Methods__: What are you doing or making to address your research question(s)?
  - If you are using any datasets, does the needed data already exist?  If so, how much data is available? What does the data look like? If you are just using a few examples for few-shot prompting, how did you select those?
  - Describe your solution to the problem/research question. What model(s) are you using? If you are using few- or zero-shot prompting, what do your prompts look like?
5. __Evaluation__: *Renamed from Experiments section* What experiments will you be running?
  - What are you measuring and why? What evaluation metrics do you plan to use to answer your research question(s)?
  - What are your proposed *baselines*? (That is, what are you comparing your method against?)
  - How do these experiments answer your research questions?
6. __Results__: What did you find from your evaluation?
	- This should be more than just a list of raw numbers. You should explain to the reader how to interpret any graphs or tables you have and describe any trends that you see.
7. __Discussion__: What insights can you take away from the results?
8. __Conclusion__: In CS, this is often just a brief paragraph reminding people what the highlights of your paper were.
9. __References__: (Un-numbered) Papers are cited correctly in the conference's format and are references in the main text.

In a separate document called `team#-supplement.pdf`, provide the
__LLM Use Statement__: Describe exactly how you used LLMs to generate parts of your paper (<a href="https://laramartin.net/interactive-fiction-class/index.html#using-llms-or-generative-ai">refer to the syllabus for guidance</a>) **or your poster**. If you did not use **any** generative text, please state so.



### What to Submit
Submit the following to [Blackboard]({{page.submission_link}}):
* `team#-finaldraft.pdf` which is your final paper.
* `team#-poster.pdf` which is your poster.
* `team#-supplement.pdf`, the LLM use statement.


### Grading
<div class="alert alert-warning" markdown="1">

* Poster Content - 8 points ([See description above.](#poster-grading))
* Poster Visuals - 4 points
* Results - 5 points - Data is displayed in a clear format and tables/graphs are made to accompany the text.
* Discussion - 5 points - Insights make sense and 
* Tips Integrated - 3 points - All previous tips/recommendations were integrated or adjusted for.
* Complete - 10 points - All sections listed above are included, paper seems cohesive, and paper is in correct format.
* LLM Use Statement - 1 point

Total: 36 points
</div>
