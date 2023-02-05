---
title: "Can Open Service Subdaos Bring Back Helium's Glory Days?"
date: 2022-09-01T11:30:03+00:00
# weight: 1
# aliases: ["/first"]
tags: ["web3"]
author: "Nijat"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: true
draft: false
hidemeta: false
comments: false
description: "In this article, I explain why open service subdaos are very sound idea"
# canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: "/img/meson-helium5g.jpg" # image path/url
    alt: "Meson Network" # alt text
    caption: "Meson Network" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/njts/blogoes/blob/main/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---
When it comes to the decentralized web, decentralization has always been a source of contention. Some believe that the decentralized web is truly decentralized, while others believe that it is unrealistic. To be honest, I believe in second thoughts as well. One of the primary reasons for this is that decentralized web infrastructure continues to rely heavily on centralized infrastructure. Many DAPPs are still hosted on servers provided by major cloud providers such as Amazon and Google, as I mentioned in my previous article.

I saw [HIP 68](https://github.com/helium/HIP/blob/main/0068-open-service-subdao.md) recommended on Helium's Github a while ago, and it inspired me to write this article. There was a section in HIP 68 that suggested running the Meson Network CDN nodes on Helium hotspots. I'll explain why, this is a very sound idea.

> Note 1: All opinions expressed in this article are my personal opinions. I'd like to state right away that this article is also about missing pieces of some Web3 projects. But that doesn't mean I don't like them. I support and appreciate every project working to decentralize the internet. I believe they will overcome the issues mentioned here.

Let's get started.


### Why Helium?

Why does integrating Meson into the Helium network make more sense when there are such good and decentralized server/node infrastructure examples like Akash and Flux available today?

The two biggest players in the decentralized cloud industry are Akash and Flux. They're doing an excellent job of developing the decentralized clouds. However, there are some parts that I believe are missing. They have a long way to go in terms of distribution, despite how good they are at decentralization.

![Flux Providers](/img/flux-providers.jpg)

There are three basic types of providers in Akash and Flux.

#### Data centers

As their names indicate, data centers that provide the basic processing power are not much different from the data centers we are accustomed to.

#### Secondary market vendors

Secondary market vendors are users who sell computing power from major central cloud providers such as AWS, GCP, and Hetzner on Akash and Flux. While the processing power still comes from large central data centers, it is more decentralized as it is provided by a large number of users.

#### Home providers

It is the rarest but most valuable type of user. Home users contribute to the network with the servers they host in their own homes and play a major role in the decentralization of the network.


The first two types of providers provide the majority of the processing power in decentralized clouds. As far as I can see, Akash is currently working to increase home providers. One of these works was the Akash Supermini device. The Supermini can be thought of as a home server. This was a great idea, but unfortunately it's been postponed for now.

![supermini](/img/akash-supermini.webp)

Furthermore, these two decentralized cloud providers can only run Docker containers and do not offer IPv4 or IPv6 addresses.


### What makes Helium unique?

Helium is inherently distributed. It's not a good idea to put together and run a bunch of helium hotspot miners in one room. Each Helium hotspot must be at least 300 feet apart from the others. This ensures complete dispersion. As a result, the Helium Network has the potential to create sub-networks that operate in highly distributed networks.

![Helium Map](/img/helium-map.png)

### What types of sub-networks are possible?

VPN, CDN, ping server and other sub-networks that require less processing power can be created.
For the rest of this article, I'll go over the Meson CDN example. Meson CDN is a promising project that aims to build a decentralized CDN for Web 3.0.


### What are the advantages of running the Meson CDN on Helium nodes for the Helium network?

#### 1. It has the potential to reduce the number of offline hotspots in the Helium network.

At the moment, 35% of the Helium network's total hotspots are offline, and this figure is increasing by the day. Low hotspot earnings are one of the main reasons for such a high offline hotspot rate. Some hotspots' earnings no longer motivate people to operate them. One of the most significant benefits of Meson Network is that it will strengthen the revenue model for Helium hotspot owners. People who run Meson CDN on their hotspots will be able to earn extra HNT. Furthermore, Meson CDN will increase overall data credit utilization in the helium network. This will help in keeping more hotspots online. On the other hand, Meson CDN nodes consume very few resources on the host machine, which means they can run on any hotspot.

#### 2. Meson can improve the performance of the 5G network.

Helium strives to become one of the biggest players in the global 5G market. At the time of writing this article, there are 2644 5G hotspots connected to the network, and it continues to increase every day.

If Meson CDN nodes are installed in these hotspots, users connecting to the internet using Helium 5G can achieve faster web performance than 5G provided by other traditional mobile providers. Of course, this performance increase will be valid for websites where Meson CDN is used, but considering that Meson has the potential to become one of the largest CDNs in the world, this is not a big problem.

### How it will improve the performance of the 5G network? 

Hotspots/modems are the first points of contact between the user and the destination server. Furthermore, these are the closest possible points to install CDN servers. Traditional CDN providers are unable to easily install CDN servers at these points. If Helium and Meson collaborate to accomplish this, it may start a new era in the CDN and 5G industries.

> Server-side caching
![server-side](/img/server-side-cache.jpg)

> Traditional CDNs
![Traditional CDNs](/img/traditional.jpg)

> Meson + Helium 5G
![Meson + Helium 5G](/img/meson-helium5g.jpg)


|                   | Costs | Server load | Latency |
|-------------------|-------|-------------|---------|
| Server-side      | High  | High        | High    |
| Traditional CDNs  | Low   | Low         | Median  |
| Meson + Helium 5G | Low   | Low         | Low     |

In this day and age, using server-side caching is something I think you should only use if you're also high. I know, your latest and greatest WordPress server-side caching plugin functions like a magic.
Hovever, this method has repeatedly been shown to be ineffective when subjected to high loads. You'll need an offsite cache solution. 


#### 3. In 5G hotspots, it economizes bandwidth coming from outside to the hotspot.

When a user connects to the internet via Helium 5G hotspot and logs into a website that uses Meson CDN, if the hotspot is running a Meson CDN node, the hotspot can use its own local cache instead of requesting data from another server each time. In this way, that hotspot can save the internet bandwidth it spends requesting data from servers around the world


I have covered the three most important topics above. Of course, there are other topics to consider.  The most important of these is interoperability.  Instead of each project working separately, if they collaborate and develop compatible software with each other, they can accelerate web3 adoption and provide a better environment for developers and users. Only by considering the web 3.0 as a whole can we produce something useful. Despite the fact that we all work on different projects and follow different paths, our ultimate goal is the same. A better Internet for a brighter future.
If you have something to say or discuss about it, you can write it under this Twitter post. I'm curious about your thoughts too. I have not activated the comment feature here. Let's run like this for a while)
