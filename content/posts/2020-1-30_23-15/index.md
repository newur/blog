---
title: "Basic Blog Blocks - RSS Feed"
date: 2021-01-30T23:15:44+01:00
draft: false
tags: ["blog", "basic", "series", "rss", "feed"]
description: "Adding an RSS feed is super easy with Hugo."
ogImage: feed-icon.png
---

The plan for today was writing about the setup of my caddy  web server. However, a wild private message appeared on Mastodon and asked me: why does your blog lack an RSS feed? Good question why did it? And what could I do about it? 

{{< img src="feed-icon.png" alt="RSS feed icon" loading="lazy">}}

Asking for an RSS feed was an excellent question for several reasons:
- I knew many people at mastodon like RSS and organize the blogs they follow via feeds. So it was somehow "on the list" anyway.
- I knew nothing about RSS beyond the bare minimum, like it is some XML subscription format, and the nerds are angry because google killed it kind of. As I said, I do not know much about it.

So the question was the perfect trigger to start learning at least a bit about RSS. The first pleasant surprise was, that I already have an RSS feed! Hugo (the static site generator I use for this blog) generates one by default. I just had no idea about it and it was not linked anywhere, but the XML file was there all the time. Anyone familiar with Hugo could have guessed the location.

Second goodie was, the Hugo documentation was very clear on how to add it to the page. Just copy and paste a few generic lines into the `head` part of the HTML and RSS reader find it automatically. I verified with two different readers that everything works as expected, and it did. Nice.

I asked the people of mastodon if they prefer a visible link as addition on the page, and they affirmed. So I followed their wisdom and added [the 'new' feed](https://blog.ghostletters.xyz/index.xml) to the start page. Overall it was very easy, basically zero work, and I learned something new. Since I have now RSS readers on my phone and in my desktop browser I might start using them for other blogs.

Drop me a message on mastodon and share which RSS feeds you consider a good reading source. Surprise me with your selection. :)

Saddle the horses!