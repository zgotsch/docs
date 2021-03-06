---
navhome: /docs
sort: 1
title: A simple blog
next: true
---

# A simple blog

Publishing markdown using Urbit is really easy.  Here we'll create a
very simple blog and publish our first posts.

First, let's setup a desk to serve our posts from:

    |merge %site ~your-urbit %home

Then let's mount that desk to unix:

    |mount /=site=

You should now be able to find a `/site` folder inside of your pier
directory (either `comet/` or `your-urbit/`).  

To begin serving files from this new desk use `|serve`:

    |serve %site

First let's create the landing page for our blog.  Create the file
`site/web/blog.md`:

    ---
    anchor: none
    ---

    # Hello

    This is a simple blog I built on Urbit.

    <list dataType="post"></list>

Try viewing this file at `http://your-urbit.urbit.org/blog`.  The only
special thing about this page is the `anchor: none` YAML which simply
turns off the Tree navigation.  Normally Tree gives navigation
controls for walking around the filesystem, but taking them away makes
the page seem more like a landing page.

The page looks pretty boring now.  Let's add our first post.  From
unix run `mkdir your-urbit/site/web/blog; touch
your-urbit/site/web/blog/post-1.md`. (Currently [there's a
bug](https://github.com/urbit/urbit/issues/321) that prevents empty
directories from getting created, so we have to `touch` a file inside
them first.)  In `blog/post-1.md` let's add some filler content:

    ---
    date: ~2016.4.20
    title: My first post!
    type: post
    navhome: /blog
    ---

    Is this a decentralized Medium?  Let's find out.  

    But first, how about a long quote from Paramenides:

    > True, he said; and therefore when ideas are what they are in
    relation to one another, their essence is determined by a relation
    among themselves, and has nothing to do with the resemblances, or
    whatever they are to be termed, which are in our sphere, and from
    which we receive this or that name when we partake of them. And
    the things which are within our sphere and have the same names
    with them, are likewise only relative to one another, and not to
    the ideas which have the same names with them, but belong to
    themselves and not to them.

    Good to get that out of the way.



You should be able to view this file at:
`http://your-urbit.urbit.org/blog/post-1.md`.  You'll also notice that
now the list of posts here: `http://your-urbit.urbit.org/blog` has
updated.

Here we use two pieces of YAML worth noting: `type` and `navhome`.  

- `type` implies that the page has some special handling by Tree.  
When `type` is `post` we automatically put in the `date`, `title`
and `author` when they're specified and add some styles.

- `navhome` sets the path used by the home button (the circle in the
 top left).  Since we want to send people back to the root of our
 blog, we set this to `/blog`

Adding posts is as easy as dropping markdown files into the `blog/`
directory.  Pretty easy!
