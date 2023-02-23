---
title: "About This Website's Content And Tech Stack"
date: 2023-02-23T11:30:03+00:00
weight: 1
aliases: ["/posts/tvap-for-plausible-analytics/"]
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: true
draft: false
hidemeta: true
comments: false
description: "What is the purpose of this blog? What tech stack am I using for this website?"
# canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: true
disableHLJS: false
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: false
ShowPostNavLinks: false
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
editPost:
    URL: "https://github.com/njts/blogoes/blob/main/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---
### Posts.
I usually have to do a lot of research when working on web development and cybersecurity tasks. Sometimes I find the information I'm looking for in the comments section of a website or on a personal blog, which saves me a lot of time. 
That's why I just openly share my own experiences, code snippets, and some notes here. I believe that some of the information I share will benefit someone and make their job easier. I don't put ads, paywalls, or other forms of monetization on my content. I don't create long, meaningless SEO content. I just post what I know, what I did to accomplish a certain thing, and what I'm thinking about something. 

### Tech Stack
In this blog, I use [Hugo](https://gohugo.io/) open-source static site generator and self-hosted [Plausible Analytics](https://plausible.io/).

#### Why Hugo?
I love Hugo because it's fast, easy to use, and less bloated. I've used a variety of CMSs in the past, including WordPress, Joomla, and Ghost, but when I met Hugo, I fell in love with it. Hugo may be the most underappreciated CMS. Hugo makes it extremely simple to make the entire website's code open source because there is no database or backend. This is exactly what I'm looking for. In addition, I take a lot of markdown notes. With Hugo, I can easily post them without modifying them. It's is the best match for my requirements.

#### Why Plausible Analytics?
Simply because I value my visitors' privacy and dislike Google Analytics and other similar services that collect a lot of information about them. I don't need 95% of the data Google Analytics collect. I don't care what model of smartphone my visitor is using, how old they are, what gender they are, and so on. I'm just curious about how many people read my articles. Knowing this encourages me to create more content. That's all. This is why I use Plausible Analytics. Plausible doesn't collect user IP, persistent identifiers, cross-site or cross-device tracking data, or any other kind of information I mentioned above. It simply functions as a page view and visitor counter. On my own VPS, I run my own Plausible Analytics instance. If that VPS is hacked, the hacker will be unable to extract any useful information about my visitors. All information is like "this article has been read X times", "that many visitors come from that country", and so on. There are no personal identifiers, etc.

To display the total number of visitors on my homepage, I use my custom-made express API [TVAP](https://github.com/njts/TVAP) (Total Visitors API for Plausible).

> This is my current tech stack. If I change the tech stack of this blog in the future, I'll update this article.