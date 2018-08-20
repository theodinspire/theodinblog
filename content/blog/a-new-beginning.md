---
title: "A New Beginning"
date: 2018-05-07T20:12:10-05:00
draft: false
---

This is too ominous title for such a simple prospect. And I probably do this
every time I start a new blag.

However, I do want to get better at writing, and sadly, the only way to do this
is to write. I also want to get better at website building, and in this
particular iteration, get better at [Hugo](https://gohugo.io/); thus I suppose
the only way to get better at this is to use Hugo and build a site.

I might as well use this to document the steps I used to create this site.

### 1. Install Hugo
This is very easy to do and is explicitly laid out [here on Hugo's site](https://gohugo.io/getting-started/installing/).
I do not really need to elaborate further. And to be honest, I did it a few
months ago when I was setting up my portfolio site when I was looking for work;
I don't remember much about it other than what is documented there.

However, I have been thinking about writing a blog ever since I read [Joel Spolsky's four-part article on writing specs](https://www.joelonsoftware.com/2000/10/02/painless-functional-specifications-part-1-why-bother/), especially that bit where he said he got over his fear
of writing by having to write a three to five page essay every week for school.
I don't think I'll be attacking that any time soon, but maybe a couple blog
posts a week will help. I just need somewhere to put it, hence this site.

### 2. Start a New Site!
This one is also easy. Go to your repositories folder and enter

``` shell
hugo new site <sitename>
```

Oh cool! I have a new site put together. Let's run it!

``` shell
hugo server -D
```

And when I go to the landing page, look how wonderful, nothing's there! At least
it's a blank page and a not a "This site cannot be reached" page. That means
something, right?

### 3. Start a new blog post
Hugo does it's magic based on archetypes and whatnot. But we don't have any of
that yet. Luckily when you generate a site, it builds a default template file at
`\archetypes\default.md`.

``` markdown
---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true
---
```

One just runs the command

``` shell
hugo new <section> <post-name>.md
```

And hugo will copy the default, filling in the the post name and date, into
`content/<section>/<post-name>.md` It has been in this generated file that I
am typing this very post.

### 4. But where's the page
I haven't set up a layout page for this yet though, so no matter how much
serving I do, I will not be able to see my work until I set one up. To make this
quick for myself, I just dropped the default, list and single page templates
[as suggested by hugo on their site](https://gohugo.io/templates/base/).

### 5. Not so stylish.
Dren, the site appears, but it also appears that it just fell out of 1996. It
doesn't have any styles. Shame.

However, I can just whip some styles into a style sheet and link them in my
default layout file. (I make this sound simpler than it is, but even stealing
styles (like Github's) for use can take some time).

### 6. Uh-oh, Syntax Highlighting
You've noticed how in the last two sections have syntax highlighting. I still
have to set that up. Hugo does come with [syntax highlighting built in](https://gohugo.io/content-management/syntax-highlighting/#generate-syntax-highlighter-css)
But there's some set up to that:

``` shell
mkdir static/styles
hugo gen chromastyles --style=friendly > static/styles/syntax.css
```

`/static` is where one puts static files like CSS, JavaScript or
images, basically everything that Hugo doesn't govern. However, the templates
I've used don't link to this immediately.

### 7. Finally
Now I've got a site built and looking fine. This post is currently the only
thing on it, and the styles are really basic. But it works, and I'll have
something to build off of in the future.
