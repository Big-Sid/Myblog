+++ 
date = "2023-01-29"
title = "HCI Lab1 - Create My Personal Webite"
description = "This is about how I created my own personal page and the questions that arose during my creation process"
authors = "Xuefeng Wei"
slug = "HCI Lab1"
+++

This article is divided into three parts, the first part is how I created my website locally, the second part is how I published the website stored locally to the Internet, and the third part is the problems I encountered in the process of creating the web page and how I solved them
<!--more-->

## 1. Create a personal blog on local compuuter
find a convenient location on the local computer to store web files, in this lab, I used Hugo to build my web page, which is a very convenient static web page building tool, because it has a large number of open source web templates, which allows us to quickly deploy a well-designed web page，I chose to create my web files under /Users/Documents/. By using the commands below.

```html
cd /User/Documents/
hugo new site myblog
git init
git submodule add https://github.com/luizdepra/hugo-coder themes/hugo-coder
cp themes/hugo-codr/exampleSite/* -rf ~/User/Documents/myblog/
```

    If the above steps are successful, these files will appear under that folder：
    
![](images/image.JPG)

    Now I have done with the page locally! Go through the hugo server command and visit http://localhost:1313/. I can access the site I just created locally!

## 2. Post Blog on Internet through Github Pages
Now we're going to publish the page we just created to the Internet via github,First I create a hidden folder .github in my personal web local directory and create a folder in the hidden folder and name it workflows and then create a folder named gh-pages.yml under that folder. In Mac OS, the shortcut to show hidden folders is :

```html
shift+command+.
```

Then write the following in the gh-pages.yml file you just created, which is the key to driving github pages.

```html
name: github pages

on:
  push:
    branches:
      - main  # Set a branch that will trigger a deployment
  pull_request:

jobs:
  deploy:
    runs-on: ubuntu-22.04
    steps:
      - uses: actions/checkout@v3
        with:
          submodules: true  # Fetch Hugo themes (true OR recursive)
          fetch-depth: 0    # Fetch all history for .GitInfo and .Lastmod

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: 'latest'
          # extended: true

      - name: Build
        run: hugo --minify

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        if: github.ref == 'refs/heads/main'
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

Once you're done, go to your own github and create a repo, then return to your local terminal and enter the following command：

```html
git status
git add .
git commit -m "first commit"
git branch -M main
git remote add origin [your github repo's address]
git push -u origin main
```

After success, go to the general option of actions in github and select gh-pages, then you can access my blog in the Internet!

## 3. Problem I met durng this lab 
This lab was a challenge for me because I had never created a web page before, and the most error-prone thing was that I created the site in the wrong place locally so that I couldn't access it easily, and when I got familiar with it I fixed the page where I created the web page.
The second problem was that during the deployment of the web page, when I accessed my web page, the page was displayed incorrectly because I used the wrong command during the creation of the web page, and the wrong order also caused the web page creation to fail.
The third problem is that when I put the pages on giithub, I need to change the pages to gh-pages in actions-general, only then the site will be effective.
In short, as long as the steps are followed carefully, there will be no problem.
