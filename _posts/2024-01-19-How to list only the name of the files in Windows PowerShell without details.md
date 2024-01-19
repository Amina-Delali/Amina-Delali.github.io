---
layout: post
title: "Listing Files with PowerShell"
subtitle: "I don't want to see all the details!"
date: 2024-01-19 19:47:00 -0109
background: '/img/posts/01.png'
---





# Used when

I wanted to list the **PNG** and **SVG** files I have just created while working on the new design of my other website, but the default command *dir* will list the files with other details.

So, to run the command, I just clicked on **Open in Terminal** from the *Images* folder, and it opened the **PowerShell** automatically:

<img src="/img/posts/How to list only the name of the files in Windows PowerShell without details-20240113121908819.webp" width="100%" height="100%" alt="opening a folder in a powershell">

 From the image below, you can see all the extra details added with the names of the existing files:

 <img src="/img/posts/How to list only the name of the files in Windows PowerShell without details-20240113122109714.webp" width="100%" height="100%" alt="default dir command in powershell">



# The Solution
  knowing that my *Images* folder didn't contain any sub folder, and from a **StackOverflow** answer available [here](https://stackoverflow.com/a/71554161){:target="_blank"} , I run the following command (and it worked):


```PowerShell
dir *.png | % Name
```

  And here is the result:
<img src="/img/posts/How to list only the name of the files in Windows PowerShell without details-20240113122453418.webp" width="100%" height="100%" >


# Original Answer

In the original **StackOverflow** [question](https://stackoverflow.com/q/71554087){:target="_blank"}, the user wanted to list *recursively* its **TXT** files from the *command prompt* without listing the **parent folders**. And the following [answer](https://stackoverflow.com/a/71554161){:target="_blank"} was given to him:

- **PowerShell Command**

```powershell
 dir *.txt -r | % Name
```


- **CMD Command**

```bash
 PowerShell -Command "dir *.txt -r | % Name"
```
