---
layout: default
img: scribe.png
img_link: https://parl.ai/projects/light/
caption: Automatically write descriptions for text adventure games
title: Prompting and Fine-tuning
type: Homework
number: 2
active_tab: homework
release_date: 2024-09-16
materials:
   -
     name: hw2.ipynb
     url: interactive-fiction-class/homeworks/generating-descriptions/hw2.ipynb
due_date: 2024-10-07 23:59:00EST
submission_link: https://blackboard.umbc.edu/ultra/courses/_82444_1/outline/assessment/test/_7129306_1?courseId=_82444_1&gradeitemView=details
readings:
  - 
    title: OpenAI API Documentation
    url: https://platform.openai.com/docs/overview
    type: documentation
  -
    title: Language Models are Few-Shot Learners
    authors: Tom B. Brown, Benjamin Mann, Nick Ryder, Melanie Subbiah, Jared Kaplan, Prafulla Dhariwal, Arvind Neelakantan, Pranav Shyam, Girish Sastry, Amanda Askell, Sandhini Agarwal, Ariel Herbert-Voss, Gretchen Krueger, Tom Henighan, Rewon Child, Aditya Ramesh, Daniel M. Ziegler, Jeffrey Wu, Clemens Winter, Christopher Hesse, Mark Chen, Eric Sigler, Mateusz Litwin, Scott Gray, Benjamin Chess, Jack Clark, Christopher Berner, Sam McCandlish, Alec Radford, Ilya Sutskever, Dario Amodei
    venue: NeurIPs
    year: 2020
    type: paper
    url: https://arxiv.org/abs/2005.14165
  -
    title: Learning to Speak and Act in a Fantasy Text Adventure Game
    authors: Jack Urbanek, Angela Fan, Siddharth Karamcheti, Saachi Jain, Samuel Humeau, Emily Dinan, Tim Rocktäschel, Douwe Kiela, Arthur Szlam, Jason Weston
    venue: EMNLP
    year: 2019
    type: paper
    url: https://arxiv.org/pdf/1903.03094.pdf
  -
    title: Generating Interactive Worlds with Text
    authors: Angela Fan, Jack Urbanek, Pratik Ringshia, Emily Dinan, Emma Qian, Siddharth Karamcheti, Shrimai Prabhumoye, Douwe Kiela, Tim Rocktaschel, Arthur Szlam, Jason Weston
    venue: AAAI
    year: 2019
    type: paper
    url: https://arxiv.org/abs/1911.09194
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

In this homework, we're going to use OpenAI's API to generate text adventure game components automatically.
Starting with the [prompting ideas from class](https://laramartin.net/interactive-fiction-class/slides/lecture-04_output.pdf) and [generating descriptions using the Playground](https://laramartin.net/interactive-fiction-class/in_class_activities/openai-playground/room-descriptions.html), we'll show how to finetune models to perform specific tasks. In particular, you will generate room descriptions and item properties for text adventure games. 

## Learning Objectives
For this assignment, we will check your ability to:
* Use the OpenAI API for few-shot prompting GPT models
* Use the OpenAI API for finetuning GPT early models
* Setup data for finetuning
* Compare early finetuned output to modern few-shot output

## Getting Started

If you haven't already done so, please complete the in-class activity on [Generating Room Descriptions](https://laramartin.net/interactive-fiction-class/in_class_activities/openai-playground/room-descriptions.html). This will give you a good idea of how the model should be prompted without dealing with the API.

### Models

OpenAI has several different chat models.  You will probably see `gpt-4o` and `gpt-4o-mini`, but there are older models like `gpt-3.5-turbo` and `davinci-002` (GPT-3).  These differ from each other in several dimensions:
* The context length (how long each message can be, and how many messages of history the conversation can have)
* The number of model parameters (larger number of model parameters tend to result in higher quality output)
* The speed of the model (`gpt-3.5-turbo` generates output more quickly)
* The cost of the model (`gpt-4o` is more [expensive](https://openai.com/pricing))


## Prompt Design

You can design prompts to get GPT to do all sorts of suprising things.  For instance, GPT-3/4 can perform [few-shot learning](https://arxiv.org/abs/2005.14165).  Given a few examples of a task, it can "learn" a pattern very quickly and then be used for classification tasks.  It often times helps to tell the model what you want it to do. Use some of the tips and tricks we [talked about in class](https://laramartin.net/interactive-fiction-class/slides/lecture-04_output.pdf).


## Fine-Tuning

Next, we'll take a look at how to [fine-tune the OpenAI models](https://platform.openai.com/docs/guides/fine-tuning) to perform a specific task.  You can use few-shot learning when you have a few dozen training example, and you can use fine-tuning when you have several hundred examples. When we have a few hundred training examples, then it's not possible to fit them all into a prompt, since GPT-3 has a limit of 2048 tokens in the prompt.  

For your homework, you'll fine-tune GPT-3 to generate different parts of text adventure games.  Specifically we'll train GPT-3 to
1. Generate descriptions of locations
2. Predict an item's properties

## Data

We are going to use a text adventure that was developed by Facebook AI Research for their paper [Learning to Speak and Act in a Fantasy Text Adventure Game](https://aclanthology.org/D19-1062/).

Here's the paper's abstract:

> We introduce a large-scale crowdsourced text adventure game as a research platform for studying grounded dialogue. In it, agents can perceive, emote, and act whilst conducting dialogue with other agents. Models and humans can both act as characters within the game. We describe the results of training state-of-the-art generative and retrieval models in this setting. We show that in addition to using past dialogue, these models are able to effectively use the state of the underlying world to condition their predictions. In particular, we show that grounding on the details of the local environment, including location descriptions, and the objects (and their affordances) and characters (and their previous actions) present within it allows better predictions of agent behavior and dialogue. We analyze the ingredients necessary for successful grounding in this setting, and how each of these factors relate to agents that can talk and act successfully.

Their data is called the LIGHT dataset (Learning in Interactive Games with Humans and Text).  It contains 663 locations, 3462 objects and 1755 characters.  I have divided this data into training/dev/test splits.  We will use this data to fine-tune GPT-3 to generate descriptions of rooms and items.


## Colab Notebook

You will be working on this [Colab Notebook for Fine-Tuning/Prompting on LIGHT Enviroment Data]({{ site.baseurl }}/homeworks/generating-descriptions/hw2.ipynb).

*Remember to make a copy of the notebook into your own Drive by choosing "Save a Copy in Drive" from Colab's "File" menu.*

In addition to working your way through the Colab Notebook, I recommend reading the [OpenAI documentation](https://platform.openai.com/docs/overview), and trying the examples in the Playground.

## What to submit

You should submit your completed Colab Notebook to [Blackboard]({page.submission_link}).  You can work in pairs.

# Grading
<div class="alert alert-warning" markdown="1">
 * Run fine-tuning code for room descriptions (1 pt)
 * Fine-tune additional model for item properties
	* Setup training data (5 pts)
	* Finetune the model (5 pts)
	* Call the model (7 pts, one per property)
 * Call the few-shot model for item properties
	* Try multiple prompts (5 pts)
	* Zero-shot, One-shot, and Five-shot prompts -- prompt, output pairs (6 pts)
 * Evaluation 
	* Implement precision and recall using scikit (2 pts)
	* Run precision and recall over your fine-tuned item model (1 pt)
	* Run precision and recall over your one-shot item model (1 pt)
	* Comparison questions (6 pts)
 </div>
 
 
# Recommended readings

<table>
   {% for publication in page.readings %}
    <tr>
      <td>
	{% if publication.url %}
		<a href="{{ publication.url }}">{{ publication.title }}</a>
        {% else %}
		{{ publication.title }}
	{% endif %}
	{% if publication.authors %}	      
		- {{ publication.authors }}.
	{% endif %}
	{% if publication.year %}	
		{{ publication.venue }}  {{ publication.year }}.
	{% endif %}

	{% if publication.abstract %}
	<!-- abstract button -->
	<a data-toggle="modal" href="#{{publication.id}}-abstract" class="label label-success">Abstract</a>
	<!-- /.abstract button -->
	<!-- abstract content -->
	<div id="{{publication.id}}-abstract" class="modal fade" tabindex="-1" role="dialog" aria-labelledby="{{publication.id}}">
    <div class="modal-dialog" role="document">
      <div class="modal-content">
        <div class="modal-header">
          <button type="button" class="close" data-dismiss="modal" aria-label="Close"><span aria-hidden="true">&times;</span></button>
          <h4 class="modal-title" id="{{publication.id}}">{{publication.title}}</h4>
        </div><!-- /.modal-header -->
        <div class="modal-body">
        {{publication.abstract}}
        </div><!-- /.modal-body -->
	</div><!-- /.modal-content -->
	</div><!-- /.modal-dialog -->
	</div><!-- /.abstract-content -->
	{% endif %}
	{% if publication.bibtex %}
	<!-- bibtex button -->
	<a data-toggle="modal" href="#{{publication.id}}-bibtex" class="label label-default">BibTex</a>
	<!-- /.bibtex button -->
	<!-- bibtex content -->
	<div id="{{publication.id}}-bibtex" class="modal fade" tabindex="-1" role="dialog" aria-labelledby="{{publication.id}}">
    <div class="modal-dialog" role="document">
      <div class="modal-content">
        <div class="modal-header">
          <button type="button" class="close" data-dismiss="modal" aria-label="Close"><span aria-hidden="true">&times;</span></button>
          <h4 class="modal-title" id="{{publication.id}}">{{publication.title}}</h4>
        </div><!-- /.modal-header -->
        <div class="modal-body">
 	   <pre>{{publication.bibtex}}
           </pre>
        </div><!-- /.modal-body -->
	</div><!-- /.modal-content -->
	</div><!-- /.modal-dialog -->
	</div><!-- /.bibtex-content -->
	{% endif %}
</td></tr>
  {% endfor %}
</table>
