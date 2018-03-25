---
title: "Starting to Blog"
subtitle: "Working with Hugo and Netlify"
date: 2018-03-24T18:12:42-06:00
tags: ["hugo", "netlify"]
draft: true
---

Do we need a blank line before this text?

<!--more-->

## How About a Header

Some more text.

The following is a code sample using triple backticks ( ``` ) code fencing provided in Hugo. This is client side highlighting and does not require any special installation.

```javascript
    var num1, num2, sum
    num1 = prompt("Enter first number")
    num2 = prompt("Enter second number")
    sum = parseInt(num1) + parseInt(num2) // "+" means "add"
    alert("Sum = " + sum)  // "+" means combine into a string
```

Some more code:
```sh
# clone as follows with SSH for multiple GitHub accounts
> git clone git@losalamosal.github.com/losalamosal/losalamosal.me.git
> cd losalamosal.me
# Set email for SSH user
> git config user.email account-appropriate@email
# make new site in existing (non-empty) directory
> hugo new site --force .
> cd themes
> git submodule add https://github.com/halogenica/beautifulhugo.git
> cd ..
# edit config.toml to add theme = "beautifulhugo"
# add a post--contraty to Hugo docs, must be post directory for this theme
> hugo new post/starting-to-blog.md
# Check the site at localhost:1313
> hugo server -D
> ^C
# push it up to GitHub
```
