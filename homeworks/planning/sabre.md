---
layout: default
img: squirrel_plan.png
img_link: https://xkcd.com/1503/
caption: Squirrel Plan 
title: Creating Sabre Problems
type: Homework
number: 4
active_tab: homework
release_date: 2025-10-29
due_date: 2025-11-14 23:59:01EST
materials:
    - 
        name: Jupyter Notebook for Running Sabre
        url: IF_HW4_Running_Sabre.ipynb
    - 
        name: Homework 0 Notebook
        url: hw0.ipynb
    -
        name: Sabre Technical Report
        url: sabre-report.pdf
    -
        name: Example Sabre Problems
        url: https://github.com/sgware/sabre-benchmarks/tree/main/problems
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
        url: sabre-report.pdf
submission_link: https://blackboard.umbc.edu/ultra/courses/_96140_1/outline/assessment/test/_7963045_1?courseId=_96140_1&gradeitemView=details
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

<div class="alert alert-info">
Submission link:
<a href="{{page.submission_link}}">{{ page.submission_link }}</a>

</div>

{{page.type}} {{page.number}}: {{page.title}}
=============================================================
## Learning Objectives
* Figure out how to write a problem for a planning program.
* Determine how utility functions within Sabre.
* Compare and contrast the planner's behavior to when the game is played by a human.

Extra Credit:
* Generate a planning problem using a code-based LLM.
* Compare the processes of generating a planning problem by hand vs LLM

## Introduction
In this homework, we're going back to the beginning! 
Primarily, you will be converting the Action Castle game from HW0 into [Sabre](http://cs.uky.edu/~sgware/projects/sabre/)'s syntax by hand.


## Working with Sabre
In this first part, you will be creating a planning problem following the syntax of Sabre and then running your problem through the Sabre planner.

[Sabre](http://cs.uky.edu/~sgware/projects/sabre/) tries to find a story based on a set of limits.
It has three different types of limits:
* **author temporal limit**: "maximum number of actions in the author’s plan—that is, the actual actions that will be executed to raise the author’s utility" (`-atl` flag)
* **character temporal limit**: "maximum number of actions in a plan a character imagines when justifying an action" (`-ctl` flag)
* **epistemic limit**: "how deeply Sabre will search into a character’s theory of mind" (`-el` flag)

Whether a limit is reached is calculated by looking at the **utility** of the overall problem (`utility()`) or the utility of a particular character's perspective (e.g., `utility(Princess)`).

The above definitions and more information can be found in the report [A Collection of Benchmark Problems for the Sabre Narrative Planner](sabre-report.pdf). You can also find a partial example of a problem that I made in [the Extra Credit](#example).

### Part 1: Make a Planning Problem by Hand
The skeleton of a problem has been provided to you in [this notebook]({{page.materials[0].url}}). Again, you can open this notebook in [Colab](https://colab.research.google.com/), [Deepnote](https://deepnote.com/), or VSCode.
You might notice that there are some variations from Action Castle. I've simplified a few things: the rose is just in the garden (no rosebush) and there is no "Death" room or path from the tree.

<div class="alert alert-info">
I've set up everything so that you just need to implement the parts in the string that say "TODO". No need to try to convert the Sabre code into Python or Java. Also, note that I have already declared all of the types, entities, properties, and starting state conditions for you.
</div>


To write a problem for Sabre, do the following:
1. Download one or a couple of the problems from the list [https://github.com/sgware/sabre-benchmarks/tree/main/problems](https://github.com/sgware/sabre-benchmarks/tree/main/problems) 
to use as reference.
2. Find your HW0 notebook. If you can't find your notebook from when you did HW0, here is the empty one again: [Homework 1 Notebook]({{page.materials[1].url}}).
3. Note the syntax used in the example Sabre problems to make a planning problem for the first Action Castle game. You will implement the **Actions** from Action Castle in your plan. There are 11 of them in total.
4. Download the [notebook for running Sabre]({{page.materials[0].url}}) and test your file. You can also run one of the example files to see what a successful plan looks like.
5. Iterate until Sabre can *solve* your problem. **Tip: To debug your problem once your syntax bugs are fixed, you can try changing your utility to a smaller problem until you know the paths are available. For example, set your utility to `location(Player) == GardenPath` if you're trying to make sure your walk action works.**
Also, the deeper the goal is, the longer the planner is going to take to run.


<div class="alert alert-info">
Important notes:
<ul>
<li>Do not use the "consenting" and "observing" components. This makes the problems difficult to debug.</li>
<li><code>null</code> in Sabre is <code>?</code></li>
</ul>
</div>


### Part 2: Experiment with Utility
1. (2 pts) Set your `utility()` as the following block:
```
utility():
	if(royal(Player)) 1 else 0;
```
run it and collect the plan you get (for context this utility takes my solution about 3 minutes to plan through),
and then replace it with
```
utility():
	if(inv(Crown) == Player) 1 else 0;
```
and run that and collect that plan.
	* Copy and paste each plan that you get (printed at the end of the output when you run the Java command) into a word document.
	
2. (2 pts) Do the above plans differ a lot from the actions someone would take when playing the interactive fiction version of Action Castle? (1-3 sentences)
4. (2 pts) Change the `walk()` action to allow all characters to walk around, not just the Player.
	* Copy and paste the 2 resulting plans & share your impressions on how the story has changed.
5. (2 pts) Does allowing the other characters to walk around result in a more interesting story? If so, why? If not, why not? (2-3 sentences)
6. (2 pts) In addition to your new `walk()` action, change the `utility()` functions from 2.1 to be for any character, not just the Player.
  * Copy and paste the 2 resulting plans & share your impressions on how the story has changed.
7. (2 pts) Traditional planners require a *pre-specified goal* that the system tries to find a path toward. How does Sabre compare to more traditional planners? (1-3 sentences)



## Extra Credit: Use GitHub Copilot (or other code-based LLM) for Problem Creation

### Setting up GitHub Copilot
You can find the instructions here: [https://code.visualstudio.com/docs/copilot/setup](https://code.visualstudio.com/docs/copilot/setup)

But it essentially is:
1. Get access to [GitHub Copilot](https://github.com/features/copilot), you can sign up for a [free student account](https://docs.github.com/en/education/explore-the-benefits-of-teaching-and-learning-with-github-education/github-education-for-students/apply-to-github-education-as-a-student) or do the 1-month free trial. It's usually $10/month.
2. Make sure to **block** suggestions matching public code and **uncheck** allowing GitHub to use your code snippets to train on.
 ![Removing training data and public code match.](copilot-access.png)
3. Install the extension on VSCode & link it to your GitHub account.

And you should be ready to go!

### Generating a Planning Problem from wikiHow
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

### Example

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

I would declare some types that would be relevant. These are like listing variable.
```LISP
  type location;
  type type : attribute;
  type player : location;
  type attribute : entity;
  type water: entity;
  type status;
``` 
And some entities -- specific instances of the types above. These are like the characters and things in your story.
```LISP  
  entity Bugs : player;
  entity Treated : attribute;
  entity Fresh : type;
  entity Moving : type;
  entity Salt : type;
  entity Chesapeake : location;
  entity Lake : location;
  entity Water : water;
  entity Player : player;
```
And properties -- what types of what attributes entities might have and the relations they have with each other.
```LISP
  property is(location : location, attribute : attribute) : boolean;
  property has_water(location : location) : boolean;
  property is(location : location) : type;
  property at(player : player) : location;
  property from(water : water) : location;
  property safe(water : water) : boolean;
  property has(player : player, water : water) : boolean;
  ...
```

Then we need some starting facts -- what state things are in at the beginning of the story.
```LISP
  at(Foot) = Lake;
  at(Bugs)= Lake;
  !has(Player, Water);
  at(Player) = Chesapeake;
  has_water(Chesapeake);
  ...
```
And actions -- things that move the story along.
```LISP
  action get_water(player : player, water : water, location : location) {
     precondition:
		has_water(location) &
		at(player) == location;
     effect:
		!safe(water) &
		has(player, water);
  };
  ...
```
Any potential triggers -- things that should occur but don't neccessarily have an event that starts it.
```LISP
  trigger know_water_source(player : player, other : player, water : water, location : location) {
	precondition:
		at(player) != location &
		from(water) == location &
		has(other, water);
	effect:
		believes(player, safe(water));
  };
  ...
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
   ...
```

#### Using GitHub Copilot
1. Download an example problem from [https://github.com/sgware/sabre-benchmarks/tree/main/problems](https://github.com/sgware/sabre-benchmarks/tree/main/problems) (or use the same one you've used in Part 1).
2. Import the problem file in VSCode.
3. Create a new .txt file for the problem you plan to generate.
4. Open the file and press CTRL + I to open Copilot.
5. Add an example problem file as an attachment in the prompt (as shown in image).
![Attach the planning problem to your prompt.](attach-copilot.png)
6. Write your prompt.
7. Save the file and [run it through Sabre]({{page.materials[0].url}}).
8. If it is close, count the number of edits you need to make to get it to run. If it's pretty far off from what you wanted, generate it again.

In order to get the full 5 points, you need:
* Sabre to be able to find a solution in the generated problem.
* To provide the list of changes you made to the generated code to get it to work.




## What to submit
You should submit the following:

* A Jupiter notebook with your completed planning problem.
* A PDF file containing your answers to Parts 2 & 3.
* If you did the extra credit:
	* A PDF called "extra-credit.pdf" containing 1) the original text of your prompt and 2) what problem file you used as input.
	* A txt file called "generated.txt" of the generated problem.


Submissions should be done on [Blackboard]({{page.submission_link}}).


## Grading
<div class="alert alert-warning" markdown="1">
* Part 1 - 22 points (2 points per action)
* Part 2 - 12 points
* Extra credit - 5 points
</div>

{% if page.readings %} 
## Recommended readings
{% for reading in page.readings %}
* {{ reading.authors }}, <a href="{{ reading.url }}">{{ reading.title }}</a>.  <i>{{ reading.note }}</i>
{% endfor %}
{% endif %}
