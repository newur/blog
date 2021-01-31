---
title: "Basic Blog Blocks - Caddy Web Server"
date: 2021-01-31T12:03:27+01:00
draft: false
tags: ["blog", "series", "caddy", "webserver"]
description: "Get your HTTPS certificate with zero effort."
ogImage: grind_finer.jpg
---

With a domain and a (virtual) server the foundation is ready, and we can start to serve some basic HTML to our readers. Therefore, we need a web server - meaning a software that can talk to browsers that call our domain. I went with [Caddy 2](https://caddyserver.com/), which is a rather new web server written in Go. The nice part of caddy is that it was developed with encryption via https in mind. So it comes with support for [Let's Encrypt](https://letsencrypt.org/) out of the box, no plugins needed. Neat! So how does it look in detail?

{{< img src="grind_finer.jpg" alt="RSS feed icon" loading="lazy">}}

The full caddy configuration for my blog looks like this:

``` bash
# /etc/caddy/Caddyfile

blog.ghostletters.xyz {
  root * /path/to/blog
  encode gzip
  file_server
  try_files {path}.html {path} {path}index.html index.html
}
```

Five lines of config, and the site is reachable via https. All the certificate negotiation with Let's Encrypt is done in the background. Only make sure you set up a proper DNS A Record for your domain (here for the `blog` sub domain), otherwise the whole magic won't work.

Let's have a closer look at each line. 

``` bash
blog.ghostletters.xyz {
...
}
```

This creates a config block that will be applied only to the sub domain `blog.ghostletters.xyz`. As said before, caddy will automatically try to organize a https certificate for this (sub) domain.

The following 3 lines are pretty self explaining.

``` bash
root * /path/to/blog
encode gzip
file_server
```

**(1)** We tell caddy where it finds the actual content of the blog. For testing you can place a text file with *Hello World* at that location. **(2)** Tell caddy to gzip the content before sending it to the browser. This configuration is optional, but will save our reader some bandwidth. **(3)** We want caddy to act as a file server - meaning it should hand out actual files (and not act like a reveres proxy).

The last line is the most interesting one.

``` bash
 try_files {path}.html {path} {path}index.html index.html
```

This tells caddy what it should do when there is no exact match for a given path. This is best explained with an example:
- a user clicks a link to this post, for instance: `blog.ghostletters.xyz/posts/2020-1-31_11-00/` The part after the first slash is called *path*.
- caddy looks for a file at `/path/to/blog/posts/2020-1-31_11-00/`
    - `/path/to/blog` is defined in our config
    - `/posts/2020-1-31_11-00/` is the *path* part of the link
    - `/path/to/blog/posts/2020-1-31_11-00/` leads to folder, not to a file!
- caddy applies the `try_files` rules from left to right
    - is there a file when we add `.html` to the path? - No.
    - is there a file at just the path? - No.
    - is there a file when we append `index.html`? - Yes!
    - fallback would be a redirect to the start page. Notice the last `index.html` is without a path. So this is a file at the top-level, directly in `/path/to/content`

So from a user perspective the following 3 links are identical, because they all lead to the same file
- [blog.ghostletters.xyz/posts/2020-1-31_11-00/](https://blog.ghostletters.xyz/posts/2020-1-31_11-00/)
- [blog.ghostletters.xyz/posts/2020-1-31_11-00/index](https://blog.ghostletters.xyz/posts/2020-1-31_11-00/index)
- [blog.ghostletters.xyz/posts/2020-1-31_11-00/index.html](https://blog.ghostletters.xyz/posts/2020-1-31_11-00/index.html)

In case you wonder why I always use the first version, check out this great post from the legendary Sir Tim Berners-Lee: [Cool URIs don't change](https://www.w3.org/Provider/Style/URI)

Bonus: This little config makes sure all requests to the domain without the `blog` sub domain get redirected to the blog. This might change in the future, but for now avoids request that go into void.

``` bash
ghostletters.xyz {
  redir https://blog.ghostletters.xyz{uri}
}
```

And that is all for today. Go away, now. 
