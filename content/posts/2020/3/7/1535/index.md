---
title: "BBB - Head Meta"
date: 2021-03-07T15:37:25+01:00
draft: false
tags: ["blog", "series", "meta", "preview"]
description: "Feeding the machine"
#ogImage: grind_finer.jpg
---

Habe a closer look at a rather minimal, but stylish `head` section in my HTML documents.

```html
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">

<link rel="stylesheet" type="text/css" href="/css/style.css">
<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">

<meta property="og:image" content="{{ $ogImg }}">
<meta name="description" content="{{ $description }}">

<title>{{ $title }}</title>
```

As you can see, I grouped the `head` content into 4 parts. Let's break them down.

### Text Encoding

```html
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
```

The first group in line `1` and `2` is purely technical and helps your browser to display the text properly. I dunno why `UTF-8` is not assumed as default, but maybe in other parts of the world another text encoding dominates web pages. Picking the wrong (or no encoding) at all was a popular mistake that transformed non ASCII characters into the replacement character �. This char (U+FFFD) is [used to replace an unknown, unrecognized or unrepresentable character](https://en.wikipedia.org/wiki/Specials_(Unicode_block)). I forgot where I picked up the second line (so it was probably from [lighthouse](https://web.dev/measure) to push my score).

### Visual Appearance

```html
<link rel="stylesheet" type="text/css" href="/css/style.css">
<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
```

The second group deals with visual stuff, like how the pages looks in a _normal_ browser. So if you are a hard core minimalist that counts every byte and/or targets terminal browsers (which might ignore CSS styling completely, like [w3m](http://manpages.ubuntu.com/manpages/bionic/man1/w3m.1.html)), you might want to skip this part completely. For the rest, I highly recommend having some basic styling in one common `.css` file.

While modern CSS is often deemed highly confusing - or a total mess - you can ignore most of it in the beginning. The following parts should be sufficient to get started and have a decent layout and look:

- build 3x3 layout with CSS grid. Period. Grid is by far the greatest layout system I have seen so far (ping me on Mastodon if you know a better). Use a [generator](https://grid.layoutit.com/) and read [Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/) and you are good to go.
- copy styling from other websites that you like. Right click and `Inspect` an element you like, and the browser will show its CSS properties.
- start small and add more when needed. It is okay to look crappy in the beginning. Once you want to support mobile devices like phones and tablets check out [media queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries). They work great together with CSS grid.

You might have stumbled over articles advocating for inline CSS which is supposed to be 'faster' and less likely to break in unexpected ways. Don't listen to this. Inlining style will have a similar effect like writing each HTML page fully by hand: you become unable to keep it consistent in no time, because it is scattered across all your pages. Just don't do it. Each decent web server will cache the file and serve it to each visitor only once (and again after you changed it). This is by far the best compromise of speed and maintainability one can ask for.

The two lines after the style sheet link are for nice little favicons, which are the little pictures on browser tabs or bookmarks. There is a whole world regarding favicons and how many you 'must' provide. Check [this article](https://sympli.io/blog/heres-everything-you-need-to-know-about-favicons-in-2020/) in case you want to know more. I created just 1 very high resolution one and fed it into one of the many favicon generators you find online. I then picked a larger one for tablet users and one rather small one for all the rest. Just try to find an icon that is somewhat recognizable for 16x16 and 180x180 pixels.

### Sharing Meta

I first called this part 'Social Media' but social media gained a rather bad connotation in some circles. _Sharing_ is still accepted as something nice, so let's go with this term.

```html
<meta property="og:image" content="{{ $ogImg }}">
<meta name="description" content="{{ $description }}">
```

You probably want to share your latest blog post (for instance on social media), and many platforms provide some nice preview picture and/or text. This is especially important when you follow the approach of [never changing URIs](https://www.w3.org/Provider/Style/URI) - meaning they do not contain a title.

Which link looks jucier, waiting for your click? This sad bare bone...

{{< img src="no_preview.png" alt="screenshot of mastodon post without preview pic" loading="lazy">}}

...or this bad boy?

{{< img src="with_preview.png" alt="screenshot of mastodon post with preview pic" loading="lazy">}}

Again there is a whole lot more behind the `og:` tags. Check out [this guide](https://css-tricks.com/essential-meta-tags-social-media/) if you want to have the best experience on different platforms like twitter, facebook, etc.

### Title

```html
<title>{{ $title }}</title>
```

This one is pretty straight forward. Each valid HTML document [requires](https://www.w3schools.com/tags/tag_title.asp) a title. It is shown on the browser tab, used by search engines and god knows what. Just have it. :)

And that's it for the HTML `head`. The `body` is up next. 

See you soon!





