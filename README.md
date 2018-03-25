# losalamosal.me
Static blog and JAMstack site

Create repo on GitHub first.

```sh
# clone as follows with SSH for multiple GitHub accounts
> git clone git@losalamosal.github.com/losalamosal/losalamosal.me.git
> cd losalamosal.me
# make new site in existing (non-empty) directory
> hugo new site --force .
> cd themes
> git submodule add https://github.com/halogenica/beautifulhugo.git
> cd ..
# edit config.toml to add theme = "beautifulhugo"
> hugo new posts/starting-to-blog.md
# Check the site at localhost:1313
> hugo server -D
> ^C
# push it up to GitHub
```
