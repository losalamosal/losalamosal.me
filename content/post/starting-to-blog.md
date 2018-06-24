---
title: "Starting to Blog"
subtitle: "Static Site Generators for the Win"
date: 2018-04-04
lastmod: 2018-06-20
tags: ["hugo", "netlify", "static-site", "jamstack"]
---

Now that I've retired from Los Alamos (partially anyway) and I have a bit of
free time, I've decided to start blogging. I'm not writing to bare my soul or
discuss my political views &mdash; that's just navel gazing. No, my motivation
for blogging comes from a much deeper place. I want to build a side project
&mdash; **The Killer App**&trade; &mdash; and make a ton of money!

<!--more-->

Unfortunately, as of now, I have no idea what this killer app might be. This
blog's focus is on documenting my *technical preparation*, so that when the
idea for the killer app does materialize, I can build and deploy it as fast as
possible. I'll talk more about potential killer apps and the technologies
required to build them in future posts. For now though, I need to stand up a
blog.

There are many ways to publish a blog. You could use a fully hosted blogging
platform like [Medium](https://medium.com/) or
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
on your end results and total control of your own content. The downside is
that you must manage the infrastructure yourself.

## Static Site Generators

Yet another option, and the one that appeals the most to me, is to use a static
site generator. Before I talk about why I find this approach appealing, we need
to define what it is. Let's do that in two parts: **static** and **generator**.

On a *static site*, the content of the pages is fixed and all users see the
same thing when visiting a page. These pages are written with HTML (and styled with CSS) and don't use a *back end* server to populate the page with
content. Dynamic sites essentially have *holes* in the pages that are *filled
in* dynamically by executing a process (and potentially querying a database) on
a remote server. Benefits of static sites include performance (the site is
pre-built and doesn't need to be constructed in real time), reliability (there
is no dependence on back end systems), and security (the lack of back end
servers, processes, and databases reduces the *attack surface*).

Static sites are easily built by hand. Code up some HTML/CSS pages, place them
in a directory that a web server can access, and voil&agrave;: you've got a
static site. Of course, for anything but the most basic site, building by hand
is a drag. This is where static site *generators* come in. Static sites can
also have *holes* for content (e.g. posts). Like dynamic sites, these holes are
filled in by the static site generator. This happens when the site is *built*, not
when it's accessed by a visitor.

I like the static site generator approach to blogging because it fits into my
comfort zone as a developer. Even though I spent many years designing and
developing user interfaces (back in the day), I don't much like using them if I
can avoid it. I'm much more comfortable in an editor (emacs), a shell (ZSH),
and git. This environment is right in the wheelhouse of site generators, which
are essentially compilers. The site's *source code* (on GitHub of course)
consists of templates that represent the structure of the site (pages, etc.), a
theme that describes the look (and, to some extent, the feel) of the site, and
the content itself (posts, etc.). You run the generator to *compile* all of this
into the HTML files that represent your site.

### Choosing a Static Site Generator

There are [a lot](https://www.staticgen.com/) of static generators to choose
from. I restricted my search to three of the more popular ones:

* [Jekyll](https://jekyllrb.com/) is a well-established, Ruby-based, static
site generator. It has lots of themes and a large community. Unfortunately, I
have a completely irrational and unjustifiable aversion to installing and
using Ruby. Also, it's known to be a bit slow on sites with a very large number
of posts.
* [Gatsby](https://www.gatsbyjs.org/) is the new hotness, and it
seems like all the cool kids are using it. It looks awesome, but might be a bridge
too far for me with all of the new technology it uses (e.g. React, GraphQL,
etc.). I may decide to give it another look someday.
* [Hugo](https://gohugo.io/) is a static site generator written in Go. It's
simple, fast, and is growing a large community around it.

I've chosen Hugo mostly because of its speed and simplicity. To get started all
I had to do was install a single Go binary on my Mac (via Homebrew). The Hugo
documentation is also excellent and made getting started painless. You can examine the source code for this site at my GitHub [repository](https://github.com/losalamosal/losalamosal.me).

## Beyond Static: JAMstack

As an old guy with a limited event horizon, I'm all about leveraging. So, when
choosing a technical solution or approach to a particular problem, I try to
keep one eye the prize &mdash; **The Killer App**&trade;. Could static site
technology be useful as the basis for a possible killer app? On the face of it,
no. Even the simplest app would likely need some dynamic behavior. An app might
need to authenticate users, take payments (for sure!), accept data from forms,
store information in a database, etc. I just got through telling you that
static sites don't do any of this. That's where the JAMstack comes in.

[JAMstack](https://jamstack.org) is an extension to static sites that adds
dynamic functionality in a fundamentally different manner than traditional back
end-based approaches. The &lsquo;**M**&rsquo; in JAMstack represents the
markup, or template, of the site that is filled in by the static site
generator's compilation process (as described above). Dynamic behavior is
provided by client-side &lsquo;**J**&rsquo;avaScript interacting with external
services through abstract &lsquo;**A**&rsquo;PIs. If your app needs a service,
there's probably a
[provider](https://cloudcannon.com/tips/2014/12/12/the-ultimate-list-of-services-for-static-websites.html)
for it. I'm looking forward to integrating JAMstack features into this blog and
developing JAMstack prototypes of future apps. More on that in future posts.

## Choosing a Hosting Provider

Like all web sites, a static or JAMstack site must be be hosted
somewhere if you want others to be able to access it. As with the site generators
themselves, there are many options for hosting static sites. I'll highlight a few that I've used or investigated:

* [Dreamhost](https://www.dreamhost.com/) has been my hosting service and domain registrar for many years. I've always been happy with their service and could easily host my site there, but it's just old to me and I want to try something new.
* [GitHub Pages](https://pages.github.com/) would probably be the smart choice at this point in time. It's well-supported by Hugo, free, and tightly bound to the source repo for the site. But, the new hotness beckons&hellip;
* [Netlify](https://www.netlify.com/) is a relatively new service dedicated to hosting static sites. In addition to static sites, they recently announced support for the 'JA' portion of JAMstack by providing native support for AWS lambda functions, user authentication, and form handling (and lots of other [cool stuff](https://www.netlify.com/features/)). This fits well with the type of killer app I have in mind, and I think a little extra up front learning will pay off in the future. Besides, it's **hot**!

## TODO

So, there you have it: the first post on my new blog. It's stored on GitHub, built
with Hugo, and deployed on Netlify. It's a start, but there are a few things
missing that might be useful on a blog:

* **Search**: For small sites, search probably isn't very useful. Though I
don't think it's a hard requirement, I don't see a downside to adding a search
capability to larger blogs. Google Custom Search is always an option, but along
the lines of JAMstack services, [Algolia](https://www.algolia.com/) looks like
an interesting alternative.
* **Branding**: I'm currently using the [Beautiful
Hugo](https://themes.gohugo.io/beautifulhugo/) theme to style my blog. I don't
know about beautiful, but I think it looks pretty good (or maybe just OK). At
some point I may want to "brand" my site to distinguish it with its own look. This
would need to coincide with the development of my own Hugo theme. That looks
like a major task, so I probably won't tackle it for quite some time. It's just
not on the fast path to **The Killer App**&trade;.
* **Comments**:  I would certainly like to hear
what people have to say about my content, but I'm not sure whether traditional blog
comments are the best venue. Hugo does support comment systems such as
[Disqus](https://disqus.com/) and [Staticman](https://staticman.net/) but I
don't like how they look out of the box. Plus, there's the management
overhead. They attract a lot of junk and probably need to be moderated; otherwise, the
useless content will remain tied to your blog for all time. For now, I think
Twitter might be the best place for comments on my posts. Even if it gets ugly,
the comments are not attached to the blog.

I'd really like to hear your feedback. Please add your comments to [my
tweet](https://twitter.com/LosAlamosAl/status/1009663862193336320) that
announced this post.
