---
layout: post
title: "Progress bar in a Dataview Obsidian Table"
subtitle: "It's So Simple!"
date: 2024-09-05 14:09:00 -0109
background: /img/posts/01.png
---





# How to Set Up

Imagine you have in your **Obsidian** note two **YAML** fields: 
- target: that represents the number of tasks you will work on
- value: that represents the number of the completed task

You want to use a **Dataview** block to generate a table about information on your progress. You can simply display the values, and calculate the progress in percentage. But you can also add a **beautiful** visualization for your progress: display a **progress bar**.

When you set up your **progress bar**, you must consider these two parts:
- the actual **progress bar**
- the label (progress value) to add to your progress bar.

The actual progress bar is defined by two values:
- the maximum value. In our case, the maximum number of tasks.
- the value of progress In our case, the number of completed tasks.

To define these values, you use this formula in the **Dataview** block:

````
```
"<progress max=" + target + " value=" + value + "> </progress> " 
```
````


To define the label to add, you simply calculate the value of the progress:

````
```
	round(value/target*100) +  "%"
```
````


# The Example

In our case, we can have this entire **dataview** formula:

````
```dataview
table without id
file.link as "Example",
value as "Value",
target as "Target",
round(value / target * 100)+"%" as "Advancement",
"<progress max=" + target + " value=" + value + "> </progress> " 
+ round(value/target*100) +  "%" as "Progress"
from #task
where file.name=this.file.name
```
````

An here is what you can have, if the **target** value is equal to **15**, and the **actual value** of completed task is equal to: **5** :


<img src="/img/posts/progress bar in dataview obsidian.png" width="100%" height="100%" alt="the display of a progress bar in an obsidian dataview table">

 
One more thing to consider, is that you must ensure that your **properties fields** are of type **number**. If it is not the case, you will have to use in the formula the **number** convert method, to convert them to numbers.