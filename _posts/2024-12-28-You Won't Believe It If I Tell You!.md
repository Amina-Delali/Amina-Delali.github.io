---
layout: post
title: "You Won't Believe It If I Tell You!"
subtitle: "This is How Images Can Be Displayed in Small Size in a Dataview Table"
date: 2024-12-28 05:06:00 -0109
background: /img/posts/01.png
---

# What I Am Talking About

We use the **Dataview** plugin in **Obsidian** to display information, and meta data about the notes availables in our vault. But sometimes, these notes may contain links (or even transclusions) of images. 

So first, I am going to confirm that yes, it is possible to display a preview of an image inside a **Dataview** table. But not only that, you can also display a resized preview of it. 

Right now, I had found two cases in which we can manipulate these kinds of links:
- You have a bulleted list in your note, and one of the items of that list contains a link (or a transclusion) of an image available inside your vault.
- You have a YAML property defined in your note that may contain links to images in your vault

In this post, we are going to talk about the second case: links in a **frontmatter** property.

# This Is How It Works
First, there are two **Dataview Obsidian** functions that we will use in our query:
- *link*: generates a link from a given file's path or name.
- *embed*: converts a link into an embedded link.

The goal is to display a table in a particular note of the small preview of images links defined in the frontmatter of several different notes available in our vault. 
So, this is what we are going to do inside our query:
- create a link from this frontmatter property by calling the *link* function, but we add an other parameter to specify the size in witch we are going to display the preview. In the code snippet below, these parameters are **property_value**, and **size**
- then we pass the result to the the embed function. 


<img src="/img/posts/dataview obsidian query code snippets for displaying a resized image.png" width="100%" height="100%" alt="tdataview obsidian query code snippets for displaying a resized image">


# A Simple Example
I have the note "*Images Listing Example*", in which I am going to Display the images defined in other notes two YAML properties:
- *originalfile*: a list of items that will contain only one link of an image available in the vault
- *processedfile*: a list of items that will also contain only one link of the corresponding processed image (also from the vault)

So, I have a list of notes that describe images. Each note, has in its frontmatter a link to an image (the original property), and an other  link  corresponding to its processed image (the processed property).

So, in our case, the  **property_value** will be **originalfile[0]** for one column, and **processedfile[0]** for the second displayed column. 

The first column will simply display the links to the corresponding notes.

Note that I didn't have to use a list to define links, I could have just used a *text property*. But this is the way I prefer defining links 🙂.

Now here is the query:

````
```
table without id
file.link as "The Images Notes",
embed(link(originalfile[0],"100")) as "Original",
embed(link(processedfile[0],"100")) as "Processed"
from #attachement and !"Itinerary/Kit/Templates"
where originalfile[0] 
```
 
````

For a bit of context:
- The **from** section, consider the notes tagged with #attachement and that are not a template note.
- The **where** section, select the notes that have the **foriginalfile** property set.
- The "100" parameter will correspond to the chosen size.

 And here is a preview of the result:


<img src="/img/posts/dataview obsidian size preview image.png" width="100%" height="100%" alt="the display of a dataview table containing a small preview of images">

# An Unexpected Bonus 

If you install the **Image Toolkit** plugin, you can click on the images when you hover over them, and you can see a detached, bigger size preview of them:

<img src="/img/posts/zoomed preview of an obsidian dataview image link.png" width="100%" height="100%" alt="the display of a zoomed preview of an obsidian dataview image link.png">