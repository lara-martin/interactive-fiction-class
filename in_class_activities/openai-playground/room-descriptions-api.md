---
layout: default
img: openai-logo.png
img_link: https://platform.openai.com/playground
caption: Generating Room Descriptions
title: Use GPT to Write Descriptions for Text Adventure Game Rooms
type: in-class
active_tab: homework
materials:
    - 
        name: OpenAI Assistant API Colab
        url: https://colab.research.google.com/drive/1S9PPZkU1JGOOkGZXNBIpzGydyeVpCh_E?usp=sharing
readings:
    - 
        title: OpenAI Prompt Examples
        url: https://platform.openai.com/examples
        type: documentation
    - 
        title: Thinking Inside the Box - How To Write Boxed Text for Your Favorite RPG
        url: https://dscryb.com/thinking-inside-the-box/
        type: documentation

    - 
        title: Let’s Design an Adventure - Boxed Text
        url: https://www.dndbeyond.com/posts/625-lets-design-an-adventure-boxed-text
        type: documentation

    - 
        title: Dungeon Mastering 101 - Mastering the Boxed Text
        url: https://dmsworkshop.com/2019/09/27/dm-101-boxed-text-mastering/
        type: documentation

    - 
        title: How much description should a dungeon key include?
        url: https://dmdavid.com/tag/tag/boxed-text/
        type: documentation
    
    -
       title: A Recipe For Arbitrary Text Style Transfer with Large Language Models
       authors: Emily Reif, Daphne Ippolito, Ann Yuan, Andy Coenen, Chris Callison-Burch, Jason Wei
       venue: ACL
       type: conference
       year: 2022
       website: https://bit.ly/3fLDuci
       video: https://aclanthology.org/2022.acl-short.94.mp4
       url: https://www.cis.upenn.edu/~ccb/publications/zero-shot-arbitrary-text-style-transfer.pdf
       page_count: 12
       id: zero-shot-arbitrary-text-style-transfer
       data: 
       abstract: In this paper, we leverage large language models (LMs) to perform zero-shot text style transfer. We present a prompting method that we call augmented zero-shot learning, which frames style transfer as a sentence rewriting task and requires only a natural language instruction, without model fine-tuning or exemplars in the target style. Augmented zero-shot learning is simple and demonstrates promising results not just on standard style transfer tasks such as sentiment, but also on arbitrary transformations such as "make this melodramatic" or "insert a metaphor."
       bibtex: |
          @inproceedings{Reif2022-style-transfer,
            title={A Recipe For Arbitrary Text Style Transfer with Large Language Models},
            author={Emily Reif and Daphne Ippolito and Ann Yuan and Andy Coenen and Chris Callison-Burch and Jason Wei},
            booktitle={Proceedings of the 60th Annual Meeting of the Association for Computational Linguistics (ACL 2022)},
            address={Dublin, Ireland}
            year={2022}
          }
    -
       title: Wordcraft&colon; a Human-AI Collaborative Editor for Story Writing
       authors: Andy Coenen, Luke Davis, Daphne Ippolito, Emily Reif, Ann Yuan
       venue: IUI
       type: conference
       year: 2022
       url: https://arxiv.org/abs/2107.07430
    -
       title: Chain of Thought Prompting Elicits Reasoning in Large Language Models
       authors: Jason Wei, Xuezhi Wang, Dale Schuurmans, Maarten Bosma, Brian Ichter, Fei Xia, Ed H. Chi, Quoc V. Le, Denny Zhou
       venue: NeurIPS
       type: conference
       year: 2022
       url: https://dl.acm.org/doi/10.5555/3600270.3602070    
submission_link: https://blackboard.umbc.edu/ultra/courses/_82444_1/outline/assessment/test/_7122999_1?courseId=_82444_1&gradeitemView=details
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



In Class Activity: Using GPT to Write Descriptions for Text Adventure Game Rooms
=============================================================

Today in class you will get an introduction to the OpenAI Developer's Playground. You can work on this activity by yourself or in pairs.  You're welcome to use GPT-4o-mini since it is currently free to use.


## Developer Playground

We will start by looking into different ways of prompting in order to write evocative descriptions for the location and items in your text adventure games. You will be running the OpenAI API using the colab notebook linked to above. Use your UMBC account to see the notebook. An Assistant pipeline has been setup for you.
<div class="alert alert-info">
Please be sure to copy your API key from this page: [https://platform.openai.com/api-keys](https://platform.openai.com/api-keys)
and put it into block 7.
</div>
There are three important components:
 * __assistant__: The assistant object. Here you can set the initial attributes of your model. There are a [variety of model settings that you can adjust](https://platform.openai.com/docs/api-reference/assistants/createAssistant), including *Temperature*, *Maximum length*, *Stop sequences*, *Top P*, *Frequency penalty* and *Presence penalty*, but we will stick with the defaults for now.
   * __instructions__: This contains instructions on how you'd like GPT to behave.  By default, its instructions are "You are a helpful assistant".
   * __model__: This is where you specify what type of model you want to use. You can find the list of available models here: [https://platform.openai.com/docs/models](https://platform.openai.com/docs/models)
 * __message__: Under the "content" attribute, this is where you put your initial task or question that you want the model to answer.
 * __client.beta.threads.runs.stream__: This starts the model up.
   * __instructions__: This is where you can add specific information about the user for the model to use.

Current LLMs like ChatGPT have been fine-tuned to follow instructions.  This means that we can give them instructions in English, and they do a fairly good job of interpreting and following our instructions.  

These instructions can go in the System field. You can read through [examples prompts from OpenAI](https://platform.openai.com/examples) to see how they prompt the system to do a wide range of tasks including:
* [Grammar correction](https://platform.openai.com/playground/p/default-grammar?mode=chat) where they use the system prompt *You will be provided with statements, and your task is to convert them to standard English.*
* [Tweet classifier](https://platform.openai.com/playground/p/default-tweet-classifier?mode=chat) where they use the system prompt *You will be provided with a tweet, and your task is to classify its sentiment as positive, neutral, or negative.*
* [Lesson plan writer](https://platform.openai.com/examples/default-lesson-plan-writer?mode=chat) where they use the system prompt *Generate a lesson plan for a specific topic.* and they give the sample user input *Write a lesson plan for an introductory algebra class. The lesson plan should cover the distributive law, in particular how it works in simple cases involving mixes of positive and negative numbers. Come up with some examples that show common student errors.*  (I didn't use this to write today's lesson)
* [Convert natural language into SQL queries](https://platform.openai.com/examples/default-sql-translate) where they use the system prompt *Given the following SQL tables, your job is to write queries given a user’s request.*
```    
    CREATE TABLE Orders (
      OrderID int,
      CustomerID int,
      OrderDate datetime,
      OrderTime varchar(8),
      PRIMARY KEY (OrderID)
    );
    
    CREATE TABLE OrderDetails (
      OrderDetailID int,
      OrderID int,
      ProductID int,
      Quantity int,
      PRIMARY KEY (OrderDetailID)
    );
    
    CREATE TABLE Products (
      ProductID int,
      ProductName varchar(50),
      Category varchar(50),
      UnitPrice decimal(10, 2),
      Stock int,
      PRIMARY KEY (ProductID)
    );
    
    CREATE TABLE Customers (
      CustomerID int,
      FirstName varchar(50),
      LastName varchar(50),
      Email varchar(100),
      Phone varchar(20),
      PRIMARY KEY (CustomerID)
    );
```

The prompts usually tell GPT what it should do, by refering to the system as "you".  Prompts can get quite complicated.  Some of my favorite complex prompts were developed by Lilach Mollick and Etan Mollick from the Wharton School in thier YouTube series ["Practical AI for Instructors and Students"](https://youtu.be/t9gmyvf7JYo?si=Qg5y8F8RywcPdPyT). Here are two of their prompts:


Prompt for teachers to use:

> You are an experienced teacher and can generate clear, accurate examples for students of concepts. I want you to ask me two questions. What concept do I want explained. Wait for me to answer before asking me the second question. Who is the audience for the explanation? Then look up the concept and examples of the concept. Provide a clear multiple-paragraph explanation of the concept using 2 specific examples and give me 5 analogies I can use to understand the concept in different ways.


Prompt for students to use:

> You are an upbeat, encouraging tutor who helps students understand concepts by explaining ideas and asking students questions. Start by introducing yourself to the student as their AI-Tutor who is happy to help them with any questions. Only ask one question at a time. First, ask them what they would like to learn about. Wait for the response. Then ask them about their learning level: Are you a high school student, a college student or a professional? Wait for their response. Then ask them what they know already about the topic they have chosen. Wait for a response. Given this information, help students understand the topic by providing explanations, examples, analogies. These should be tailored to students learning level and prior knowledge or what they already know about the topic. Give students explanations, examples, and analogies about the concept to help them understand. You should guide students in an open-ended way. Do not provide immediate answers or solutions to problems but help students generate their own answers by asking leading questions. Ask students to explain their thinking. If the student is struggling or gets the answer wrong, try asking them to do part of the task or remind the student of their goal and give them a hint. If students improve, then praise them and show excitement. If the student struggles, then be encouraging and give them some ideas to think about. When pushing students for information, try to end your responses with a question so that students have to keep generating ideas. Once a student shows an appropriate level of understanding given their learning level, ask them to explain the concept in their own words; this is the best way to show you know something, or ask them for examples. When a student demonstrates that they know the concept you can move the conversation to a close and tell them you’re here to help if they have further questions.


Clearly a lot of thought went into the prompt design!  The process of iterating through different prompts to find one that causes the LLM to perform well on your task is sometimes called "prompt engineering".

## Part 1: Narration Prompts


Using the OpenAI playground, create 5-8 different system prompts to generate room descriptions. These can be the same rooms from the game you made in Homework 1 or new rooms.   We will ask you to upload your system prompts to Blackboard, and to save and upload a link to your playground.  For each of your prompts, click the "Save" button on the OpenAI playground, and turn on the toggle button so that "Anyone with the link can view".  You can then get a sharable link using the "Share" button. 

Try to create interesting variation in the narration.   You can do this by changing the system prompt anyway that you like.  You can change the identity that I gave it "You are the narrator for a text adventure game." or the writing instructions "You create short, evocative descriptions of the scenes in the game." or the style "Use the style of a fairy tale."  Feel free to vary it however you would like.  If you wanted to create a prompt for a different game with a different setting – let’s say sci-fi versus medieval  – what would you do?

You should test your prompts on several turns in a text adventure game. You can use Action Castle for the game, or you can use your own game.  Your code should have the __assitant__ setup (model attributes, etc.), a __message__ input (the user's command like "get pole"), and another set of  __instructions__ that tells the model information about the user.

[Here are the first few turns of Action Castle](action_castle.txt) for you to copy and paste into the Playground (feel free to use your own game instead).  For the next homework assignment, you’ll use the API, rather than copying and pasting into the playground.  Using the OpenAI playground is a good way to do your prompt engineering.  Once you find a good system prompt, then you can implement it in code via the API.



### Hints

Check out some of the links at the bottom of the page which give guidance to dungeon masters on how to write evocative text for games.

Here's a cool experiment from a text generation system called sudowrite that shows off some of the sensory aspects of things that you could encourage GPT to descirbe. 

<center>
<img src="sudowrite.png" class="img-responsive"/>
</center>





## Part 2: Analyzing Elaborations

LLMs have the tendency to "hallucinate" meaning that they generate things that aren’t factually accurate.  In the case of creative writing and fiction this can be an asset rather a liability.  

Pick 5 of your narrator’s outputs for different game locations, and say what things it added that weren’t present in the input.

For example, for the game input:

```
You are standing in a small cottage.
Exits:
Out to Garden Path
You see:
 * a fishing pole
 * a poisonous potion
```

One of my system prompts generated: 


> You find yourself in a quaint, rustic cottage. The room is filled with the scent of pine and old books. A crackling fire in the stone hearth casts dancing shadows on the wooden walls. A worn, but comfortable-looking armchair sits invitingly near the fire. On a small table next to the chair, there's a fishing pole. A single window reveals a lush garden path outside. The only exit appears to be a sturdy wooden door leading out to the garden path.

This adds several new elements that were’t in the input:
* stone hearth with a fire
* armchair 
* small table
* also technically, walls, a window, and a door (these are great commonsense things since I said we were 'inside a cottage', but they weren't mentioned in my input).

One problem with these elaborations is that they aren’t currently objects in the game, and we therefore cannot track state properly.  E.g. there’s no way of adding them to our inventory.  





## What to submit

You should upload a few of your best prompts and your worst prompts (according to your own judgement) and their outputs from Part 1 to [the Blackboard assignment]({{ page.submission_link }}), plus publicly shared links to your developer playgrounds for each of your prompts that demonstrate its outputs.

Also, you should:
1. Explain why you like the "best" ones that you picked.
2. Analyze these outputs using the description for Part 2.


 
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
