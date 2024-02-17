---
layout: post
title: "Automatically Centering Elements Horizontally with CSS"
subtitle: "Maybe it's not so hard!"
date: 2024-02-17 16:19:00 -0109
background: '/img/posts/01.png'
---


# Block Elements

If you always struggled with alignment in your **html**, and corresponding **CSS** code, especially with horizontal alignment, this may be helpful to you.

The key idea is how to center horizontally any html element on a web page, without setting exact positioning values, in order to provide a responsive design. Knowing that the width of these elements is considered to be smaller than the viewport width. 

I discovered these two key elements to easily accomplish this alignment:
- The display property of the html element
- The margin of those elements

If you have **block** elements, all you have to do is to set their left and right margin properties to *auto*.

For example, a **div** can be centered as follow:

```css
div {
  width: 35%;
  margin: auto;
}
```

In the code above, I set all the margin values to **auto**.

# Inline Elements

If you have **inline** elements,  just change their **display** property to *block*, then set the corresponding **left** and **right** margins to auto.
The example  below is an example of how to center an **img** *horizontally*:

```css
img {
  width:90%;
  display: block;
  margin: 10px auto;
}
```


In the code above, I also set; at the same time, the **margin-top** and **margin-bottom** to *10px*.

# The Special Case of Text Elements

For **block text elements**, like **headers** and **paragraphs** consider two situations:
- The text will have no particular background, and no specific width (the default values will be applied)
- The text will have a width smaller than its parent element, and a specific background color

In the first case, all you have to do, is to set the **text-align** property to *center*.

 ```css
p {
  text-align:center;
}
```

For the second case, you have also to set the **margin-right** and **margin-left** properties to *auto*.

```css
p {
  text-align: center;
  background-color:#98817b;
  color:white;
  width: 50%;
  margin: 10px auto;
}
```
 


For the **inline text** element, you have to first set their **display** property to *block*, then consider the previously cited cases:
- If they have no particular background color and no specific small width, just set their **text-align** element to center:

```css
span{
  text-align:center;
  display:block;
}
```
 
- In the other hand, if you want to have a background color and a particular width, you must also set the **margin-left** and **margin-right** to *auto*:

```css
span{
  text-align:center;
  display:block;
  background-color:#6d9a79;
  width: 50%;
  color: white;
  margin: 10px auto;
}
```
 
# My Use Case

I combined different types of elements, and centered all of them horizontally applying the rules I talked about above, and here is the result:


<img src="/img/posts/result-align-horizontal.png" width="100%" height="100%" alt="Centering horizontally different html elements">


The corresponding code can be found here. I added to enhance the responsiveness of the display, **minimum-width** values for most of the elements. The **image** element being automatically resized according to its parent **div** element.
<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="zYbeVzG" data-user="aminaAIM" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/aminaAIM/pen/zYbeVzG">
  Center an Image Horizontally</a> by Amina (<a href="https://codepen.io/aminaAIM">@aminaAIM</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
