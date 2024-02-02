---
layout: post
title: "They Are Called Dataview Literals"
subtitle: "And I like using Them!"
date: 2024-02-02 13:21:00 -0109
background: '/img/posts/01.png'
---


# What Are Dataview Literals

You can find their official definition from the **Dataview** [**Documentation website**](https://blacksmithgu.github.io/obsidian-dataview/reference/literals/), but this is how I am going to describe them: they are the values that you use inside your **Dataview** query, and that have no related **data**. As a reminder, the **data** is the information extracted from your notes frontmatter, your inline fields, and your notes implicit fields.

For example, values represented in the form of **numbers**, **text**, or **dates** are literals:


{: .table-bordered .table-striped .table-dark}
|&nbsp; Literal Examples |
|-----------------|
| &nbsp;25 |
| &nbsp;"This a Text" |
| &nbsp;date (2024-02-02) |




In the example above, a **date** function was used to generate a **literal** **Date Object**

# How Are They Used

Imagine you have to extract all the notes that their names contain the word "*Definition*". So you will use the literal "*Definition*" that is of type **String**. As you may notice,  the word "*Definition*" doesn't refer to any particular **data** from the notes.

So, you can simply write the following **query**:

````
```dataview
Table 
where contains(file.name, "Definition")
```
````
  
Here, I used the **literal** inside the **Dataview function** *contains*.

There are different types of literals that you can use in your queries:

{: .table-bordered .table-striped .table-dark}

| &nbsp;Dataview Literals&nbsp;  |&nbsp;  Example &nbsp; | &nbsp; Meaning &nbsp; |
|----|----|----|
|  &nbsp;Numbers  |&nbsp; 65  |&nbsp;The number 65  |
| &nbsp;Text |&nbsp; "This is actually a String" |&nbsp; The text "This is actually as String" |
| &nbsp;Links |&nbsp; \[[This is a Note\]] |&nbsp; A link to the note: This is a Note |
| &nbsp;List |&nbsp; ["word", "letter", "phrase"] |&nbsp; A list containing 3 string elements |
| &nbsp;Objects |&nbsp; {key1: 5 , key2: "A Test" } |&nbsp; An object with 2 keys (key1 and key2) and their corresponding values |
| &nbsp;Dates | &nbsp;date (today) | &nbsp;The date of today |
| &nbsp;Durations | &nbsp;dur (3 m)  | &nbsp; 3 Minutes duration |

In the table above, two different **functions** where used: *date* and *dur* to genereate two different types of literals: **date** and **duration** respectively.

The detailed list of **literals** and their possible **values** can be found in the [**Dataview Literal Documentation Page**](https://blacksmithgu.github.io/obsidian-dataview/reference/literals/)
# This How I used Them

In my **daily note**, I wanted to automatically highlight the due tasks with a specific indicator that is corresponding to their due dates.
So first, I list only the tasks that are due before or at the **note's date**, and I **group** them by their **due** dates. Then, according to how far the due date of these tasks is from **today's date**  , a **colored square emoji** is added to corresponding group:

🟩: they are due at or after the **today's date** (the **today's date** can be different from the **note's date**).<br>
🟨: they are due **1 day** or more than **1 day**  before the **today's date**. But, less than **3 days**.<br>
🟧: they are due **3 days** more than **3 days**  before the **today's date**. But, less than **7 days**.<br>
🟥: they are due **7 days**  or more than **7 days**  before the **today's date**.<br>



<img src="/img/posts/The use of dataview literals example.png" alt="The use of dataview literals example" width="100%" height="100%" >

Of course, I used other literals to add other indicator, specifically related to my **Obsidian** vault, as well as to specify the **folder** from which to extract these tasks.

Here is the entire  **Dataview query** that I am using right now:

````
```dataview
task from "Execute/Projects" where !completed 
and due <= date(this.file.name)
sort time asc
group by  due +" " + truncate(substring(file.name,4),30)+" "+file.tags[0]+ choice(file.frontmatter.status[0]="progress"," 🧩","") +
choice(contains(file.folder,"Support")," 🧰",choice(contains(file.folder,"Action")," 🎬"," 📖"))+" "+
choice(date(today)-due>=dur("7 days"),"🟥", choice( date(today)-due>=dur("3 days")  ,"🟧",choice(date(today)-due>=dur("1 days") ,"🟨", "🟩" )  ))
```
````
  
And here an extract of the result:

<img src="/img/posts/The Use of Dataview Literals Results.png" alt="The use of Dataview Literals Results"  width="100%" height="100%">
