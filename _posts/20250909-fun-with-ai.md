---
title: Having fun with AI
date: 2025-09-07 15:40:00 +0200 #CET Summer Time
description: Using Gemini to build my private Website based on Chirpy
categories: [Story]
tags: [ai]     # TAG names should always be lowercase
published: false
---

# Tldr;
Here´s some know how I gathered today to manage my website.

This is how I basically do it:

* Use git and vs-code to manage files locally
* whenever I Change something for my website, vs-code updates the "github pages" website via git
* Updates from "Upstream" can be merged locally and after checking the changes -> committed and pushed to **github pages**

# Gather some knowledge?
I will skip this part, as I already knew that...
* Github Pags offers a free of charge possibility to host your own website
* you need to be familiar with jekyll and know what gibhub pages supports

But starting like "Show me free options to host a simple website" should lead you to Github and specifically to Github Pages.

# Choosing the right template
Asking for a nice, dark themed Github Pages template, Chirpy is the first option presented by Gemini.
Look no further ;)

[Chirpy-Starter](https://github.com/cotes2020/chirpy-starter) does a great job in bootstrapping the whole system into your own github repository.  
I recommend to set up a new repository for this!

# Creating a base Chirpy site

It´s a pretty straightforward process if you follow these steps

* Login to Github
* Open the [Chripy-Starter](https://github.com/cotes2020/chirpy-starter) page
  * Enter your repository name (ending with github.io)
  * Tell gibhub Pages to use this repository as "Website generator"
  * Optionally add your own domain to github pages
* Modify the _config.yml file
* Create and use a favicon
* Set your own Avatar

If you´re doing the whole editing directly in GitHub Pages, you should be aware that there´s a delay of approx 10 Minutes from changing a file to "seeing it live in the web".  
The build process on GitHub Pages is pretty quick, but that does not mean that your changes are "live" already.  
Be patient! :)

# Create a favicon
This is described on the [Chirpy Website](https://chirpy.cotes.page/posts/customize-the-favicon/)

# set your own avatar

# Create a "Hello world! article"

# Updating the template??
This is where Gemini shines (sort of).
If you ask Gemini how to update to upstream, it suggests to install not only git, but a whole development environment with jekyll and ruby.  
If you´re like me and do it with a minimal setup (editing everything with the github webpage), you don´t need it.

## Overview of the process
* Install Git for Windows
* download (pull) your files from github to your local workstation
* add the "upstream" repository, where all the development of the theme takes place
* merge the upstream with your local files
  * This is where the real work happens as you need to manually decide if you want to keep your own settings, or the default settings from "upstream".
* upload (push) your updated local files

## Detailled instructions

### Install Git for Windows
The most convenient way is to use **winget** on a terminal.  
`winget install Git.Git`  
will do the trick.

As we´re just talking about software: I strongly recommend to install **Visual Studio Code**, as it streamlines the whole Editing and git stuff.

`winget install Microsoft.VisualStudioCode`

You need to tell git who you are.
```
git config --global user.email "spam@haraldweber.net"
git config --global user.name "haraldweber1975"
```

### Download (clone) your files from github

`git clone https://github.com/haraldweber1975/haraldweber1975.github.io`

Change into the directory of your repository
`cd haraldweber1975.github.io`

### Add and check upstream repository

`git remote add upstream https://github.com/cotes2020/chirpy-starter.git`  
`git remote -v`

You should now see 2 repositories - your own and the upstream.

### Merge with upstream

Now get the latest updates from upstream  
`git fetch upstream`  

and merge them with your local configuration  
`git merge upstream/main --squash --allow-unrelated-histories`

This is what I got in return: Some conflicting files, meaning I changed them and of course they now differ from upstream.

```
Auto-merging _config.yml
CONFLICT (add/add): Merge conflict in _config.yml
Auto-merging _data/contact.yml
CONFLICT (add/add): Merge conflict in _data/contact.yml
Auto-merging _data/share.yml
CONFLICT (add/add): Merge conflict in _data/share.yml
Auto-merging _tabs/about.md
CONFLICT (add/add): Merge conflict in _tabs/about.md
Squash commit -- not updating HEAD
Automatic merge failed; fix conflicts and then commit the result.
```

So next you need to manually check / verify / modify all mentioned .md files!

Manually edit `_config.yml` 
You can see what changed from the `<<<<<<< HEAD, =======` and `>>>>>>> upstream/main` text

### upload the updates files to your github repository

```
git add .
git commit -m "feat: merge latest updates from Chirpy upstream"
git push
```
