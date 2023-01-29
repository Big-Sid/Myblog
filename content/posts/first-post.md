+++ 
date = "2023-01-29"
title = "HCI Lab1 - Create My Personal Webite"
description = "This is about how I created my own personal page and the questions that arose during my creation process"
authors = "Xuefeng Wei"
slug = "HCI Lab1"
+++

This article is divided into three parts, the first part is how I created my website locally, the second part is how I published the website stored locally to the Internet, and the third part is the problems I encountered in the process of creating the web page and how I solved them
<!--more-->

## Create a personal blog on local compuuter
1, find a convenient location on the local computer to store web files, in this lab, I used Hugo to build my web page, which is a very convenient static web page building tool, because it has a large number of open source web templates, which allows us to quickly deploy a well-designed web page，I chose to create my web files under /Users/Documents/. By using the commands below.

```html
cd /User/Documents/
hugo new site myblog
git init
git submodule add https://github.com/luizdepra/hugo-coder themes/hugo-coder
cp themes/hugo-codr/exampleSite/* -rf ~/User/Documents/myblog/
```

    If the above steps are successful, these files will appear under that folder：
![](/static/images/HCI1-1.png)
    Now I have done with the page locally! Go through the hugo server command and visit http://localhost:1313/. I can access the site I just created locally!
