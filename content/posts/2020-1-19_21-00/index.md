---
title: "Basic Blog Blocks - Part 2"
date: 2021-01-19T20:46:12+01:00
draft: false
tags: ["blog", "setup", "basic", "series"]
description: "Summary which building blocks powers a custom blog."
ogImage: thinking_bird.jpg
---

As outlinde in the last post, having a server that is reachable by a custom domain is very nice. However, having a server and having a blog are still two different kettles of fish. One needs at least some kind of web server that hands (preferably) HTML files to each visiting browser. Good, web server software is free and plentiful. HTML is easy to write even with the dumbest text editor. So my first impulse was to actually write *all* pages by hand.

{{< img src="thinking_bird.jpg" alt="a wild bird" loading="lazy">}}

 A fully manual approach provides maximum control, even about *invisible* stuff like the source formatting, which I weirdly care about (more on that later).
While already planning a simple CSS grid layout in my mind, I remembered a painful lesson that every let's-write-each-site-by-hand tryhard experiences sooner or later: changing the **common parts** will drive you nuts.
You will always have some common layout pieces like the header, footer and meta data. As soon as you fall into the trap of hard wiring your content into this layout and start copying these files, you are doomed. With each new article changing the common parts becomes more painful, error prone and time consuming. In the end you will most likely drop all changes that are not absolutly required (read: all) and sleep very bad because you fear that it is still not consistent across all pages. Do not go down this path.

Like many typical problems, there is a time tested and elegant remedy to this problem: templating. Templates define the common parts at *one* central location and provide some placeholders for the variable parts - like the content of each blog post. There are more than enough templating processors (I assume no programming language exists without at least 2) out there, so I simply went with the last one I heard about and could remember by name: Hugo. So I just had to learn the basic folder structure of Hugo, separate my common HTML parts into the appropriate places (I like the default files/locations that Hugo provides for each part) and write my content in markdown files. In the end Hugo processes the all the pieces and spits out a bunch of static HTML files. Neat.

So coming back to the beginning - one just needs a web server and some HTML files, right? With HTML off the list the only missing part is the web server. Again my mental selection algorithm worked liked for templating processor, but in the end I did not choose the famous nginx (man, it took long till I understood this is pronounced as 'engine x'), but tried out caddy server. I saw it mentioned on a Mastodon toot (like a Twitter tweet, but with an elephant instead of a bird) and while struggling a bit in the beginning, I am very happy with the end result. I will write more about caddy in the next post.

I also plan to include a bit more technical stuff in the upcoming posts. It is always just one more fluffy post away. :D

To the space ships!