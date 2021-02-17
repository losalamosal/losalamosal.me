# losalamosal.me
Static blog and JAMstack site

To clone and build this site:

```sh
# clone as follows with SSH for multiple GitHub accounts
> git clone git@losalamosal.github.com/losalamosal/losalamosal.me.git
> cd losalamosal.me
# Set email for SSH user
> git config user.email account-appropriate@email
> cd themes
> git submodule init
> git submodule update
# add a post--contraty to Hugo docs, must be post directory for this theme
> hugo new post/starting-to-blog.md
# Check the site at localhost:1313
> hugo server -D
> ^C
# push it up to GitHub
```
