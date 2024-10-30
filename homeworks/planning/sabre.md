---
layout: default
img: squirrel_plan.png
img_link: https://xkcd.com/1503/
caption: Squirrel Plan 
title: Creating Sabre Problems
type: Homework
number: 4
active_tab: homework
release_date: 2024-11-11
due_date: 2024-03-03 23:59:01EST
materials:
    - 
        name: Jupyter Notebook for Running Sabre
        url: IF_HW4_Running_Sabre.ipynb
    - 
        name: Homework 1 Notebook
        url: hw1.ipynb
readings:
    -
        title: "Sabre: A Narrative Planner Supporting Intention and Deep Theory of Mind"
        authors: Stephen G. Ware and Cory Siler
        url: https://ojs.aaai.org/index.php/AIIDE/article/view/18896
    -
        title: "Causal Necessity as a Narrative Planning Step Cost Function"
        authors: Stephen G. Ware, Lasantha Senanayake, and Rachelyn Farrell
        url: https://ojs.aaai.org/index.php/AIIDE/article/view/27511
    -
        title: A Collection of Benchmark Problems for the Sabre Narrative Planner
        authors: Stephen G. Ware and Rachelyn Farrell
        url: https://github.com/sgware/sabre-benchmarks/blob/main/report.pdf
submission_link: 
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
* Figure out how to write a problem for a planning program.
* Generate a planning problem using Github Copilot.
* Compare the processes of generating a planning problem by hand vs LLM

## Instructions
In this homework, we're going back to the beginning! 
Here's an overview of what you'll do:
1. Convert the Action Castle game from HW1 into [Sabre](http://cs.uky.edu/~sgware/projects/sabre/)'s syntax by hand.
2. Convert a WikiHow article into a Sabre problem using Github Copilot.
3. 

## Step 0: Setting up GitHub Copilot
You can find the instructions here: [https://code.visualstudio.com/docs/copilot/setup](https://code.visualstudio.com/docs/copilot/setup)

But it essentially is:
1. Get access to [GitHub Copilot](https://github.com/features/copilot), you can sign up for a [free student account](https://docs.github.com/en/education/explore-the-benefits-of-teaching-and-learning-with-github-education/github-education-for-students/apply-to-github-education-as-a-student) or do the 1-month free trial. It's usually $10/month.
2. Make sure to **block** suggestions matching public code and **uncheck** allowing GitHub to use your code snippets to train on.
 ![Removing training data and public code match.](copilot-access.png)
3. Install the extension on VSCode & link it to your GitHub account.

And you should be ready to go!



## Step 1: Make a Planning Problem by Hand

In this first step, you will be creating a planning problem following the syntax of Sabre and then running your problem through the Sabre planner.

Instead of looking for a plan that reaches a pre-defined goal like traditional planners, [Sabre](http://cs.uky.edu/~sgware/projects/sabre/) tries to find a story based on a set of limits.
It has three different types of limits:
* **author temporal limit**: "maximum number of actions in the author’s plan—that is, the actual actions that will be executed to raise the author’s utility" 
* **character temporal limit**: "maximum number of actions in a plan a character imagines when justifying an action"
* **epistemic limit**: "how deeply Sabre will search into a character’s theory of mind"

The above definitions and more information can be found in the report [A Collection of Benchmark Problems for the Sabre Narrative Planner](https://github.com/sgware/sabre-benchmarks/blob/main/report.pdf).

For this part of the homework, you should do the following:
1. Download one or a couple of the problems from the list [https://github.com/sgware/sabre-benchmarks/tree/main/problems](https://github.com/sgware/sabre-benchmarks/tree/main/problems) 
to use as reference.
2. Find your HW1 notebook. If you can't find your notebook from when you did HW1, here it is again: [Homework 1 Notebook](hw1.ipynb)
3. Note the syntax used in the example Sabre problems to make a planning problem for the first Action Castle game. Your plan should contain:
  * 
  * 
4. Download the [notebook for running Sabre](IF_HW4_Running_Sabre.ipynb) and test your file. You can also run one of the example files to see what a successful plan looks like.

## Step 2: Generate a Planning Problem
We'll now use GitHub Copilot to write a Sabre problem for a wikiHow article.  The goal for this is to start from something that describes proceedures and actions and is written in natural language, and then have Copilot translate it into the description language used for automated planning.

Here are a few wikiHow articles that I thought might be interesting since they had some elements that could make for interesting interactive fiction.  It's fine to pick your own article.   **You shouldn't translate the whole article, just a few steps, so you can pick out the parts that you think are most relevant/easiest to create a schema from.**

Survival Stories
* [How to Survive in the Woods](https://www.wikihow.com/Survive-in-the-Woods)
* [How to Survive in the Jungle](https://www.wikihow.com/Survive-in-the-Jungle)
* [How to Survive on a Desert Island](https://www.wikihow.com/Survive-on-a-Desert-Island
) 
* [How to Survive on a Deserted Island With Nothing](https://www.wikihow.com/Survive-on-a-Deserted-Island-With-Nothing)
* [How to Get Out of Quicksand](https://www.wikihow.com/Get-Out-of-Quicksand)
* [How to Open a Coconut](https://www.wikihow.com/Open-a-Coconut)
* [How to Test if a Plant Is Edible](https://www.wikihow.com/Test-if-a-Plant-Is-Edible)
* [How to Find True North Without a Compass](https://www.wikihow.com/Find-True-North-Without-a-Compass)
* [How to Survive a Wolf Attack](https://www.wikihow.com/Survive-a-Wolf-Attack)

Detectives
* [How to Make a Detective Kit](https://www.wikihow.com/Make-a-Detective-Kit)
* [How to Disguise Yourself](https://www.wikihow.com/Disguise-Yourself)
* [How to Make a Hidden Camera](https://www.wikihow.com/Make-a-Hidden-Camera)
* [How to Hide Money](https://www.wikihow.com/Hide-Money)
* [How to Spy on People](https://www.wikihow.com/Spy-on-People)
* [How to Hack](https://www.wikihow.com/Hack)
* [How to Make a Grappling Hook](https://www.wikihow.com/Make-a-Grappling-Hook)
* [How to Open a Locked Door](https://www.wikihow.com/Open-a-Locked-Door)
* [How to Create a Secret Society](https://www.wikihow.com/Create-a-Secret-Society)

Dystopian Futures
* [How to Survive a Comet Hitting Earth](https://www.wikihow.com/Survive-a-Comet-Hitting-Earth)
* [How to Survive an EMP](https://www.wikihow.com/Survive-an-EMP)
* [How to Survive a Nuclear Attack](https://www.wikihow.com/Survive-a-Nuclear-Attack)
* [How to Build a Fallout Shelter](https://www.wikihow.com/Build-a-Fallout-Shelter)
* [How to Survive a Riot](https://www.wikihow.com/Survive-a-Riot)
* [How to Survive Under Martial Law](https://www.wikihow.com/Survive-Under-Martial-Law)
* [How to Avoid Danger During Civil Unrest](https://www.wikihow.com/Avoid-Danger-During-Civil-Unrest)
* [How to Thwart an Abduction Attempt](https://www.wikihow.com/Thwart-an-Abduction-Attempt)
* [How to Make Papyrus](https://www.wikihow.com/Make-Papyrus)


As an example, I'll pick the [How to Survive in the Woods](https://www.wikihow.com/Survive-in-the-Woods) article, and show you how part of the schema might look.  Here is step 1 from that article: 


<center>
<img src="Survive-in-the-Woods-Step-1.jpg" class="img-responsive" alt="Search for a source of fresh water. (Creative Commons License)"/>
</center>


> ### Finding Drinking Water
> Search for a source of fresh water.[1]  The first thing that you'll need in order to survive in the woods is water that you can drink. Look for signs of fresh water nearby like areas of green foliage that indicate water is nearby, low-lying areas where water could be collected, and signs of wildlife like animal tracks. It could mean that a creek, stream, or pond is nearby. While finding water is important for survival, be aware some water sources will not be safe - if possible treat all drinking water before using it. [2]
If there are mountains nearby, look for water collected at the foot of the cliffs.
> * The presence of insects like mosquitoes and flies means that water is nearby.
> * Water from heavily oxygenated water (such as from a big waterfall or rapids) typically is safer than that from a slow or still water source.
> * Freshwater springs are typically safer water sources, although these can be contaminated by mineral or bacteria as well.
> * Remember that all untreated water must be considered risky unless treated. Even crystal clear water can harbor diseases and be dangerous if consumed.

My Sabre problem for this might look like this:

I would declare some types.
```LISP
  type location;
  type type : location;
  type player : location;
  type attribute : entity;
  type water: entity;
  type status;
``` 
And some entities.
```LISP  
  entity Bugs : player;
  entity Treated : attribute;
  entity Foot : type;
  entity Fresh : type;
  entity Moving : type;
  entity Chesapeake : location;
  entity Lake : location;
  entity Water : water;
  entity Player : player;
```
And properties.
```LISP
  property is(location : location, attribute : attribute) : boolean;
  property has_water(location : location) : boolean;
  property at(type : type) : location;
  property at(player : player) : location;
  property from(water : water) : location;
  property safe(water : water) : boolean;
  property has(player : player, water : water) : boolean;
  ...
```

Then we need some starting facts.
```LISP
  at(Foot) = Lake;
  at(Bugs)= Lake;
  !has(Player, Water);
  at(Player) = Chesapeake;
  has_water(Chesapeake);
  ...
```
And actions.
```LISP
  action get_water(player : player, water : water, location : location) {
     precondition:
		has_water(location) &
		at(player) == location;
     effect:
		!safe(water) &
		has(player, water);
  };
```
Any potential triggers. That is, things that should occur but don't neccessarily have an event that starts it.
```LISP
  trigger know_water_source(player : player, other : player, water : water, location : location) {
	precondition:
		at(player) != location &
		from(water) == location &
		has(other, water);
	effect:
		believes(player, safe(water));
  };
```
Finally, some utility. This is how you want the planner to weight effects.
```LISP
  utility(Water):
	if(safe(Water))
		2
	elseif(is(Water,Fresh) & is(Water,Moving))
		1
	else
		0;
```

### Using GitHub Copilot
1. Download an example problem from [https://github.com/sgware/sabre-benchmarks/tree/main/problems](https://github.com/sgware/sabre-benchmarks/tree/main/problems) (or use the same one you've used in Step 1).
2. Import the problem file in VSCode.
3. Create a new .txt file for the problem you plan to generate.
4. Open the file and press CTRL + I to open Copilot.
5. Add the example problem file as an attachment in the prompt.
![Attach the planning problem to your prompt.](attach-copilot.png)
6. Write your prompt.


## What to submit

You should submit the following:

* A set of PDDL files, one PDDL file for your domain, and one PDDL file for each of the problems.   Your domain definition should have 
1. at least 10 action schemas beyond the ones that we defined for action castle, 
2. relevant types for your problem, 
3. predicates defined with their types and comments describing them.  
* Your problem definitions should 
1. cover at least 3 problems, 
2. give initial states and goals for each, and 
3. ensure that the goal can be reached from the initial state using your action schema. 
* A JSON file containing your annotations that map from the elements in your PDDL domain onto phrases in the wikiHow article that you selected.  You can  use this [Colab to annotate your PDDL elements with mentions from your WikiHow article]({{page.materials[1].url}}).
* A PDF file containing your writeup.  You should include at least 1 paragraphs for each of the following topics:
1. What wikiHow article did you pick and why?
2. What portions of the article did you select to translate to PDDL?
3. Give some example of the actions, types, and predicates you used in your domain.
4. Explain what goal you selected for your problem, and give the inital state and solution that you created.
5. What limitations of PDDL did you encounter that makes it difficult to precisely convert a wikiHow description into PDDL?
6. Could your PDDL be used as an interesting challenge for a text-adventure-style game?  If so, how?  If not, what would needed to create an interesting challenge?
7. Discuss how you might use GPT-3 to automatically or semi-automatically convert a wikiHow article to PDDL?

Submissions should be done on [Gradescope]({{page.submission_link}}).


## Grading
<div class="alert alert-warning" markdown="1">
* Domain Definition - 10 points
* Problem Definition - 5 points
* JSON with Annotations - 3 point
* Questions - 1x7 = 7 points
* -0.5points for not specifying why you picked the given wikihow article
</div>

{% if page.readings %} 
## Recommended readings
{% for reading in page.readings %}
* {{ reading.authors }}, <a href="{{ reading.url }}">{{ reading.title }}</a>.  <i>{{ reading.note }}</i>
{% endfor %}
{% endif %}
