---
layout: post
title: A Dataview Table in a Callout
subtitle: How it is easy to combine the two
date: 2025-07-16 18:32:00 -0109
background: /img/posts/01.png
---

# A Callout

A *callout* in **Obsidian** is that particular block of text in a note that allow you to:
- put your text in a sort of titled box with an icon
- the title and the text are highlighted and distinguished from the rest of the text of the note
- you have the option to customize the title icon
- you also have 3 type of *callouts*:
	- a simple block: the text and the title are displayed.
	- a *callout* created with the  **plus**  sign: the text and the title are by default displayed. But if you click on the **arrow** button, it will close the callout, and you will see only the title.
	- a *callout* created with the  **minus**  sign: only the title is displayed by default. But if you click on the **arrow** button, it will open the callout, and you will see the text too..

The 3 types of *callouts* are shown in the pictures below:

<img src="/img/posts/simple callout.png" width="100%" height="100%" alt="tdataview obsidian query code snippets for displaying a resized image">

<img src="/img/posts/callout with plus sign.png" width="100%" height="100%" alt="tdataview obsidian query code snippets for displaying a resized image">

<img src="/img/posts/callout with minus sign.png" width="100%" height="100%" alt="tdataview obsidian query code snippets for displaying a resized image">

You do not have to install anything to use *callouts*. They are an embedded feature in **Obsidian**

# A Dataview

A *Dataview*  is a community **Obsidian** plugin that you have to install it on top of **Obsidian** to be able to use it. It allows you to summarize data from your notes in *4 forms*:
- A table with customizable columns of the data selected.
- A column of data displayed as a list.
- A list of tasks, extracted from all the notes available in the **Obsidian** vault.
- A calendar with dots indicating notes.

To use the plugin you have to write a query inside a *Dataview* block. The block starts with **3** backticks followed by the word **dataview**, and closed by other **3** backticks. As shown below:

````
```dataview

```  
````

The query is used to select the data to display,  and to define how to display this data.

But sometimes, you want to hide the result, and to see it only when needed. This is when you can use *callouts*.

# How to add a Dataview query to a callout
 
 It's a simple trick:  you write your query first, then you copy all of it, but not the *closing* **backticks**. Then you paste everything into the *callout*. And if there are any blank lines in your **dataview** block, delete them.

For example, let's have this query that list the *notes* in the vault that are created today:

```dataview
table without id
file.link as "**Note**",
tags as "Tags"
where file.cday = date(today)
```
  
And here is the resulting table:

<img src="/img/posts/dataview table.png" width="100%" height="100%" alt="tdataview obsidian query code snippets for displaying a resized image">


And this how you put it in the following *callout*:

```
> [!list]- Notes Created Today
> ```dataview
table without id
file.link as "**Note**",
tags as "Tags"
where file.cday = date(today)                
```

This is the result (when the *callout* is open, and when it is *closed*)

<img src="/img/posts/a dataview inside a callout.png" width="100%" height="100%" alt="tdataview obsidian query code snippets for displaying a resized image">

