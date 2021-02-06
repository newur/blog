---
title: "Basic Blog Blocks - HTML Shell"
date: 2021-02-04T19:06:53+01:00
draft: false
tags: ["blog", "series", "html5", "shell"]
description: "Simple, beautiful, semantic HTML shell."
ogImage: card_house_one.jpg
---

The domain is connected to the (virtual) server, the web server software is idling for requests. So finally, we are ready to write our content, aren't we? Not quite. We still lack the basic HTML that structures our content. Otherwise, we might just hand out plain text and that is something nobody likes. Plain text tends to be hard to parse for machines and for humans, as well (kind of).

{{< img src="card_house_one.jpg" alt="RSS feed icon" loading="lazy">}}

I refer here to the general surrounding of the content as *shell*. This term is used for Progressive Web Apps (PWAs), and is described as

> The app "shell" is the minimal HTML, CSS and JavaScript required to power the user interface [..]

{{<source "developers.google.com" "https://developers.google.com/web/fundamentals/architecture/app-shell">}}

I will come back on the CSS part in a later post. For now, let us focus on the HTML topic. We want to have nice, semantic elements that structure each site. Thanks to HTML 5 we can avoid semantic-less `div`s completely for the shell.

Okay, enough with the foreplay, show me the code!

``` html
<!DOCTYPE html>
<html>
   <head>
      meta data will go here - static + dynamic
   </head>
   <body>
      <header>
         page header will go here - static
      </header>
      <main>
         actual content - dynamic
      </main>
      <footer>
         page footer will go here - static
      </footer>
   </body>
</html>
```

Even if you do not know anything about HTML, one can probably make some sense of this structure. Quickly going through it  from top to bottom

- all HTML pages must start with a `DOCTYPE`. The doc type is not an HTML tag, but a ["information" to the browser about what document type to expect](https://www.w3schools.com/tags/tag_doctype.asp). 
- all tags are wrapped into an `html` element.
- the `head` part contains meta information so other machines can make sense of your page. Meta information is often related to SEO (Search Engine Optimization), but is not limited to it. For instance, to get a nice preview picture on your mastodon toot, you want to put some special tag in the `head`.
- the `body` contains the actual content of your page. These are also the parts that will be visible to your readers.
- `header` refers to the actual page header.
- `main` will be different on each page (otherwise your page would be pretty boring :D) and contain the actual content, like a blog post
- `footer` might contain a copy left/right statement and a way to get in contact or an imprint. This is normally the same on each page.

And that's it. In the next post we will fill each part with live. And we will talk about the nerdy beauty contest of the web: the [Lighthouse](https://web.dev/measure/) measure and how to score 💯 at it.

Whoop whoop.