---
title: "Starting to Blog"
subtitle: "Working with Hugo and Netlify"
date: 2018-04-04
tags: ["hugo", "netlify"]
draft: true
---

After many years of procrastination I've decided to start blogging. Retiring
from Los Alamos has removed the last excuse not to blog. Even partial
retirement generates a lot of spare time. I have some hobbies (Go Cubs!), and I
like to travel with my beautiful wife, but I still feel a need to exercise
what's left of the old gray matter. Somewhat surprisingly, after a 37-year
career as a computer scientist, I find that I still like to hack code.

<!--more-->

The main purpose of this blog is to document how I prepare myself technically
should I ever come up with an idea for **The Killer App**. My current skills
and software stack expertise (C/C++, OpenGL, MPI, etc.) won't do me much good
when it comes time to build applications for today's cloud-based environment. Of
course, my computer science training and experience are still useful, but I
need to learn an entirely new stack to work in this area. This is what I call
"prepping for the killer app" (_#KillerAppPrepper_, _#KAPrepper_) which I'll
document in a future post. For now though, I need to get started with a simple
blog.

## Going with JAMstack

I'm a command line guy and am comfortable editing text files. I don't need or
want a content management system with a pretty user interface to create and
store my content.

Static
[sites](https://medium.com/@borisschapira/back-to-static-a-paradigm-shift-for-better-ux-and-web-performance-56f4199d74ff),
especially for blogs, are all the rage.

Compile your site. All pages are *pre-rendered* during the compilation
process. That's what makes the site *static*. Your files are the copied to a
host that serves them up directly with no processing (e.g. PHP, database
lookups, template handling, etc.) on the back end. This makes the site
fast---no work on the baqck end to build your pages. Static sites can also be
safer---there
are no databases or back end languages to hack into. 

What if you do need some interactivity and processing on your site? That's
where JAMstack comes in.

Want to do a static site. There are [a lot](https://www.staticgen.com/) of
static generators. I want a [JAMstack](https://jamstack.org/) site. Totally
rubbery Goldilocks approach to technology selection but I've learned not to
engage in too much analysis paralysis---pick something and go.

* **Too Cold**: [Jekyll](https://jekyllrb.com/) is a well established, Ruby-based, static site generator. It has lots of themes and a large community. I have a completely irrational, and unjustifiable, aversion to installing Ruby on my Mac. Also, it's known to be a bit slow if I ever get to a large number of posts.
* **Too Hot**: [Gatsby](https://www.gatsbyjs.org/) is the new hotness and it seems like all the cool kids are using. It looks awesome, but might be a bridge too fare for me with all the new technology (e.g. React, GraphQL, etc.). Maybe someday.
* **Just Right**: [Hugo](https://gohugo.io/) is a static site generator written in Go. All I have to install on my machine is the Go binary. Hugo is fast and basic, which seems like a perfect middle ground to start on.

## Setting up Hugo

Installing Hugo and setting up the initial site was pretty easy. I'll run through the steps I used but your best reference is the Hugo [documentation](https://gohugo.io/getting-started/). I will point out a few things I learned that either weren't in the Hugo documentation or that I found confusing.

I'm on a Mac, so I install Hugo using [homebrew](https://brew.sh/).

```sh
> brew install hugo
```

With Hugo installed we can start to create and populate the new site.

```sh
> hugo new site losalamosal.me    # this will be your GitHub repo name
> cd losalamosal.me
> git init                        # add your repo to GitHub in the usual way
> git submodule add https://github.com/halogenica/beautifulhugo.git themes/beautifulhugo
```

I'm using the [Beautiful Hugo](https://github.com/halogenica/beautifulhugo)
theme. Eventually, I may try and develop my own "branded" theme, but this theme
is perfectly serviceable for now. If you're on GitHub ([as I
am](https://github.com/losalamosal/losalamosal.me)), be sure to add the theme as
a [submodule](https://blog.github.com/2016-02-01-working-with-submodules/) (as
shown above). This will allow you to pull a new version of the theme when it's
updated and integrate more easily with your hosting provider.

Now edit `config.toml` and make the following changes.

```toml
baseURL = "/"
languageCode = "en-us"
title = "Los Alamos Al"
theme = "beautifulhugo"
```

In particular, note that `baseURL` is set to `/`. I've experimented quite a bit with this particular setting and still don't totally understand it.

To add a new post.

```sh
> hugo new post/starting-to-blog  # not 'posts' as shown in Hugo docs
```

## Hosting on Netlify

As with the site generators themselves, there are many options for hosting static sites. In this case, I've decided to take on a little extra learning in the hopes of better supporting the killer app.

* **Too Cold**: [Dreamhost](https://www.dreamhost.com/) has been my hosting service and domain registrar for many years. I've always been happy with their service and could easily host my site there. But, it's just old to me and I want to try someting new.
* **Just Right**: [GitHub Pages](https://pages.github.com/) would probably be the smart choice at this point in time. It's well supported by Hugo, free, and tightly bound to the source repo for the site. But, the new hotness beckons.
* **Hot, Hot, Hot**: [Netlify](https://www.netlify.com/) is a relatively new service dedicated to hosting static sites. In addition to static sites, they recently announced support for the 'JA' portion of JAMstack by providing native support for AWS Lambda functions, user authentication, and form handling (and lots of other [cool stuff](https://www.netlify.com/features/)). This fits well with the type of killer app I have in mind and I think a little extra up front learning will pay off in the future. Besides, it's **hot**!

## Saved for Later...

Many things not addressed in the first site that will like eventually need to be done (especially if anyone starts reading the blog).

* **Performance**: Not at all. Page load. Images. Yada.
* **Search**: I could use Algolia.
* **Branding**: Design my own theme. Make it small and fast.
* **Comments**: A real doozie. An [old post](https://dsandler.org/wp/archives/2009/02/26/twitter-comments) but still useful. Some say that Disqus is injecting ads now.

For now, if you have questions, either email me or tweet me at @LosAlamosAl
using one of these hash tags to refer to this post: *#KillerAppPrepper000* or
*#KAPrepper000*. Sprinkle in one of these tags on ant tweet unrelated to a
specific post: *#KillerAppPrepper* or *#KAPrepper*.

