---
layout: post
title: Installing Git Autocomplete
date: 2016-11-26 03:10:31 +0100
tag:
- tech
- github
- Web engineering
blog: true
comments: true
author: kofi
categories: Tech
description: How to install Git bash-completion
redirect_from: "/how-to-install-git-autocomplete/"
permalink: "/blog/:categories/:title/"
keywords: github, how to install autocomplete mac, tutorial, bash-completion

---
Now lets get started... :D

I am a mac user so this tutorial will be for mac:

I am going to assume you have Homebrew installed, if not I recommend you do.
Otherwise as at the time of writing this post this is the source file from the official git repo
<br>
`curl -O https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash`
<br>
....and github, since you have read this far.

now to install bash-completion run
<br>
<br>
`brew install bash-completion`

this should take a couple of seconds, then you need to add bash-completion to your \~/.bash_profile file

`if [ -f $(brew --prefix)/etc/bash_completion ]; then . $(brew --prefix)/etc/bash_completion fi`

For the sake of everyone out there we can take a look at how to edit your .bash_profile

On your terminal run
'nano .bash_profile'
This should open up the .bash_profile document on your with the Nano text editor. A new one will be created if one doesnt already exist

Now copy the code above and post if into the editor

Use \[Ctrl + o\] to save your changes and press return.

Now you can exit with \[Ctrl + x\]

run `source .bash_profile` to save your changes.

Now you can cd into a folder with git and see how your life just got way easier. You are absolutely welcome