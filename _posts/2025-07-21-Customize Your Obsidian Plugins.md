---
layout: post
title: How to customize Your Obsidian Plugins
subtitle: An example with the Auto Card Link plugin
date: 2025-07-21 10:46:00 -0109
background: /img/posts/01.png
---

# The Appearance of Your Obsidian Vault

You can change the appearance of your *Obsidian* vault by selecting and installing a *theme*.

One of the most known and customizable one is the **AnuPpuccin** theme

<img src="/img/posts/AnuPpuccin-Theme.png" width="100%" height="100%" alt="Themes in Obsidian - AnuPpuccin">

To be able to customize it as you wish, you have to install an other plugin: **Style Settings**:

<img src="/img/posts/Style Settings-Plugin.png" width="100%" height="100%" alt="Style Settings Obsidian Widget">

So you open the **style settings view** from the command palette, you go to the **AnuPpuccin** section, 
an you make the changes you want.

<img src="/img/posts/AnuPpuccin customization.png" width="60%" height="60%" alt="AnuPpuccin customization section">

You can for example override the default colors, and set yours (the section is highlighted in the image above). 

One of the colors that you can change is the **Mantle** color. It will affect the interface of most of your installed plugins:


<img src="/img/posts/Mantle.png" width="50%" height="50%" alt="Mantle Color in Style Settings Widget">


Now, imagine that you selected the color shown on the image above, you will have that color applied to some of your installed plugins, like the **Auto Card Link** plugin.

# Auto Card Link Plugin

This is an amazing *Obsidian* plugin. You copy a link, then you paste it using either defined *hotkeys*, or the command palette, and it will extract information from you link, to create a card, like the one in the example below:

<img src="/img/posts/auto card link card.png" width="100%" height="100%" alt="Mantle Color in Style Settings Widget">

You can see that the text is barely visible, so this is how you can fix it.

# Customize the Auto Card Link Appearance

If you access the stylesheet of the plugin from this path:

```
Your Vault's Folder Path\.obsidian\plugins\auto-card-link\styles.css
```
 
You can see that the customization of the card is done in this class:

<img src="/img/posts/auto card link plugin code.png" width="100%" height="100%" alt="The code of the auto card plugin">

So, all you have to do is to create a **css** file, name it as you wish (in this example, it is *custom-auto-card-link.css*) , and put it in your vault snippets folder:

```
Your Vault's Folder Path\.obsidian\snippets\custom-auto-card-link.css
```

In that file, you change the background colors, as follow:


<script src="https://emgithub.com/embed-v2.js?target=https%3A%2F%2Fgithub.com%2FDigitalCreationsLibrary%2FCODE%2Fblob%2Fmain%2FObsidian%2520Styling%2Fcustom-auto-card-link.css&style=default&type=code&showBorder=on&showLineNumbers=on&showFileMeta=on&showFullPath=on&showCopy=on"></script>

 

Then, in your *Obsidian*, you open **settings**, you go to **Appearance**. You go to the **CSS snippets** section, and you toggle on the switch next to the **css file** you have just created:


<img src="/img/posts/toggle on snippet.png" width="100%" height="100%" alt="the toggle switch to activate a style snippet">

And you get the following results:

- The card background color in normal state.
 

<img src="/img/posts/new card background color.png" width="100%" height="100%" alt="auto card link with a new background color">

- The card background color in hover state:

<img src="/img/posts/new card hover background color.png" width="100%" height="100%" alt="auto card link with a new hover  background color">

Now, you can do that to any widget you wish to customize. It is much better to do it that way, than making changes directly in the code files of the widgets.