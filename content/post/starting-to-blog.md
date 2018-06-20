---
title: "Starting to Blog"
subtitle: "Working with Hugo and Netlify"
date: 2018-04-04
lastmod: 2018-06-19
tags: ["hugo", "netlify", "static-site"]
draft: true
---

Now that I've retired from Los Alamos (partially anyway), and I have a bit of
free time, I've decided to start blogging. I'm not writing to bare my soul or
discuss my political views &mdash; that's just navel gazing. No, my motivation
for blogging comes from a much deeper place. I want to build a side project
&mdash; **The Killer App**&trade; &mdash; and make a ton of money!
Unfortunately, as of now, I have no idea what this killer app might be. This
blog's focus is on documenting my *technical preparation*, so that when the
idea for the killer app does materialize, I can build and deploy it as fast as
possible. I'll talk more about potential killer apps and the technologies
required to build them in future posts. For now though, I need to stand up a
blog.

<!--more-->

## Leverage the JAMstack

There are may ways to publish a blog. You could use a hosted (by someone other
than you) blogging platform like [Medium](https://medium.com/) or
[Blogger](https://www.blogger.com). These solutions are usually free and
provide a low barrier of entry. Set up an account, enter your content with a
beautiful user interface, pick a theme, and publish to the web. Some possible
downsides include limited control of all aspects of your site, potential
inability to use a custom domain (e.g. `www.mydomain.com`), and the fact that
your content resides on their servers.

Another option is self-hosted solutions, such as the venerable
[WordPress](https://wordpress.org/) platform (WordPress also offers a [hosted
solution](https://wordpress.com)). Self-hosted solutions require a bit more
work on the part of the potential blogger. For example, hosting
(e.g. [Dreamhost](https://www.dreamhost.com)) must be procured, a database and
WordPress must be installed, a domain name needs to be purchased and made to
point at your site, an acceptable theme configured (lot of great themes at
[Theme Forrest](https://themeforrest.net)), etc. Hosting companies often
provide canned procedures and scripts to simplify many of these configuration
tasks. The upside of this approach is that you have much more influence
on your end results and total control of your own content.

Yet another option, and the one that appeals the most to me, is to use a
[static site generator](https://www.staticgen.com). Before I talk about why I
find this approach appealing we need to define what it is. Let's do that in two
parts: **static** and **generator**.

On a *static site*, the content of the pages is fixed and all users see the
same thing when visiting a page. These pages are written with HTML (and CSS for
styling) and don't use a *back end* server to populate the page with
content. Dynamic sites essentially have *holes* in the pages that are *filled
in* dynamically by executing a process (and potentially querying a database) on
a remote server. Benefits of static sites include performance (the site is
pre-build and doesn't need to be constructed in real time), reliability (there
is no dependence on back end systems), and security (the lack of back end
servers, processes and databases reduces the *attack surface*).

Static sites are easily built by hand. Code up some HTML/CSS pages, place them
in a directory that a web server can access, and voil&agrave;: you've got a
static site. Of course, for anything but the most basic site, building by hand
is a drag. This is where static site *generators* come in. Static sites can
also have *holes* for content (e.g. posts). Unlike dynamic sites, these holes
are filled in at *compile time* by the static site generator.

Static
[sites](https://medium.com/@borisschapira/back-to-static-a-paradigm-shift-for-better-ux-and-web-performance-56f4199d74ff),
especially for blogs, are all the rage.


As an old guy, with a limited event
horizon, I'm all about leveraging. goes in to creating and publishing a blog should be at least
partially useful down the road when building the killer app.

I'm a command line guy and am comfortable editing text files. I don't need or
want a content management system with a pretty user interface to create and
store my content.


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

