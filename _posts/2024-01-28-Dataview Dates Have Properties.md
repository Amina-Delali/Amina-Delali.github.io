---
layout: post
title: "Dataview Date Fields Have Properties"
subtitle: "I didn't Know Until Now!"
date: 2024-01-28 12:57:00 -0109
background: '/img/posts/01.png'
---


# A Date Data type

One of the most interesting **Data type** related to **[Dataview](https://blacksmithgu.github.io/obsidian-dataview/) Fields** in **Obsidian** are **dates**.

 The **[Dataview](https://blacksmithgu.github.io/obsidian-dataview/)** I am talking about is the **[Obsidian](https://obsidian.md/)** plugin that allows you to query data from your **Obsidian** notes using the **Dataview Query Language**.
 
 The *data* is extracted from your notes **frontmatter**, from your **inline fields**, or from **implicit fields** related to your notes. To learn more about this *data*, you can check the following **[documentation](https://blacksmithgu.github.io/obsidian-dataview/annotation/add-metadata/)** page.

And if you don't know, **Obsidian** is a note taking app that uses **Markdown** markup language for text formatting. It allows you to take notes, easily link between them, automatically generate a **graph** displaying all the connection available between your notes, and install powerful **plugins** that allow you to transform your notes, and automate your workflow while using the app.


**Dates** types are objects that can be created from  text formatted using the [*ISO8601*](https://en.wikipedia.org/wiki/ISO_8601)  notation.  But when displaying their values, **Dataview** will render them in a human readable format .



<img src="/img/posts/date values example.png" width="100%" height="100%" alt="Dataview Date values example">


# What I discovered

You can access a particular **date** or **time** information from the **date** object itself, by accessing its properties. For example, to get the **month** corresponding to a particular **date field**, all you have to do is to use the **dot** notation with the **date field** in question.

For example, let say you want to display the **month** property value of the **creation date** field (*ctime*) of a particular note, so you can just write:


```
file.ctime.month
```
 

There are multiple **date** and **time** properties that you can access the same way:

|      | 
| ----------- | 
|`file.ctime.year`|
|`file.ctime.month`|
|`file.ctime.weekyear`|
|`file.ctime.week`|
|`file.ctime.weekday`|
|`file.ctime.day`|
|`file.ctime.hour`|
|`file.ctime.minute`|
|`file.ctime.second`|
|`file.ctime.millisecond`|



 
For example, right now, I am writing this post on Obsidian. And, if I want to display the *day* and the *hour* of the date corresponding to the creation of the  note I am writing, I can simply use the following **Dataview** expression:


````
```dataview
table file.ctime.day as "📅 Day",
file.ctime.hour as "⏰" 
where file =this.file
```
````
  
And the result would be:

<img src="/img/posts/The Result.png" width="100%" height="100%" alt="The result of a dataview query on dates fields properties">




# How I used it


I wanted to display the **tasks** planned in a particular *week*, and the formula I was writing was already long enough, so the use of the **date property** was really useful to **shorten** the expression:

````
```dataview
table without id file.link as Tasks,
map(filter(file.tasks, (x)=>padleft(string(x.scheduled.weekyear),2,"0")=substring(split(this.file.name,"-")[1],1)),(x)=>x.text  +" - ("+dateformat(x.scheduled,"EEE")+")") as steps
from "Execute/Projects"
where file.name[3]="-"
and length(filter(file.tasks, (x)=>padleft(string(x.scheduled.weekyear),2,"0")=substring(split(this.file.name,"-")[1],1)))>0
```  
````

<img src="/img/posts/the property.png" width="100%" height="100%" alt="How a dataview date field property was used">


The expression was written inside a **weekly note** with a name formatted as follow:

4 digits representing the year+"-W "+ 2 digits representing the week number ("yyyy-'W'WW"). For example the **weekly note** of the  *week 4* is named: *2024-W04*


Here a portion of the result:

<img src="/img/posts/The resutl.png" width="100%" height="100%" alt="A use case result from my personal Vault">
