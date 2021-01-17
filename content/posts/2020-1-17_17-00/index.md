---
title: "Basic Blog Blocks"
date: 2021-01-17T00:17:00+01:00
draft: false
tags: ["blog", "setup", "basic", "series"]
description: "Summary which building blocks powers a custom blog."
ogImage: tool.jpg
---

When you want to host your own blog there is a bunch of ingredients you will need. While you can always go more low level (wanna write an own web server?) the general parts are somewhat fixed. You will need a domain, a server, a web server and some content. Oh, and you need to wire it all together, because each part on its own is as helpful as an unassembled Ikea shelf.

{{< img src="tool.jpg" alt="screw tool" loading="lazy">}}

In my case the setup went along the following steps:

* buy a **domain** from a domain registrar (~5 Euro per year)
    - finding a nice name that is affordable is great fun. :D The first couple of searches will result in the desired name is either registered already and used for something, or the name is registered and up for sale, but for a ridiculous amount of money. Anyway, in the end you will find more interesting and fun names than you can use.
* rent a **server** (~5 Euro a month)
    - renting an own dedicated server (read: some bare metal machine that is used by your blog exclusively) might be overkill for the beginning, so I went with a virtual server which is a lot cheaper
    - for a purely static site one could also go with some web space (imagine like a online hard drive where you can place files, but not install any application), but web space puts rather hard limits on what you can do with it and therefore is less fun ;)
* wire the domain and your server together via a **DNS entry** (free)
    - your server will have an IP address that is only numbers (and dots). So the DNS entry (called A Record) will connect the domain (your-domain.com) to a server IP like 23.65.75.88
* install a **web server** on your (virtual) server (free)
    - web server here means an application. Without this application your server does not know what it should do when a potential reader visits your domain
* put an **HTML file** (or a plain text file for the moment) on your server and BOOM you have a blog
    - okay no sane person would call it a blog, yet, but belief me, the first time you type your domain into your phone, and it returns _something_ fell like magic :))
    
These are the basic steps to publish stuff into the world wide web. Congratulations, now you are free to write whatever is on your mind. Besides the law and your reputation no one can command you differently (puh, that sounds not as cheerful as I thought in 2021... anyway, you get the message). I plan to continue this post with the juicy parts like setting up https encryption, having an actual blog, that looks decent and follows some best practices or what I deem best practices.

Stay tuned.
