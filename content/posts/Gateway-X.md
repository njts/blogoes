---
title: "Gateway X - Even Better Web 3.0"
date: 2023-04-16T11:30:03+00:00
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
description: "In this article I offer a series of quick-start tips and an analysis comparison of Gateway X with its competitors."
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
    image: "/img/gatewayx.jpg" # image path/url
    alt: "Meson Network" # alt text
    caption: "Meson Network" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/njts/blogoes/blob/main/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---

## Thinking Simple
The web is essentially a conduit for transmitting files from somewhere to somewhere. The internet has evolved significantly in recent 10-15 years. However, executing this easy approach well is the most significant aspect of the current web.

## Not That Simple
Sending files from one location to another may appear to be simple, but doing it with a large number of users and terabytes of bandwidth is not, especially in Web3. Many Web3 infrastructure solutions have been created in recent years. However, there is still a gap in the bandwidth area.

According to [Grand View Research](https://www.grandviewresearch.com/industry-analysis/web-3-0-blockchain-market-report), the global Web 3.0 blockchain market size was USD 1.73 billion in 2022 and is expected to expand at a compound annual growth rate (CAGR) of 47.1% from 2023 to 2030. 

Another research by [Emergen Research](https://www.emergenresearch.com/industry-report/web-3-market), indicates 81.5 billion USD market size in 2030, CAGR of 43.7% market growth for Web3 industry.

As a result, we believe the Web3 infrastructure, particularly the bandwidth market, will expand significantly in the next years, beginning this year. When we consider how much data is produced in the new generation web, we see how important it is to deliver it to end users in a fast and durable manner.
Every day, users create tens of thousands of NFTs and upload hundreds of gigabytes of data to Arweave. As a leading Web3 storage solution, Arweave's size passed 125TB.
![backend](/img/arweave-weave.png)
 Web3 is growing at the fastest possible speed. In such a circumstance, it is vital to deliver a high-quality service to all users while still being able to extend the service linearly and decentralizedly as needed.

## Potential solution
Today I'll just explain and compare [Gataway X](https://docs.meson.network/mcloud/gatewayx.html). Gateway X is a CDN/Bandwidth layer for Web3 infrastructures such as IPFS and Arweave. It was created by Meson Network with the goal of resolving bandwidth scaling challenges with old and modern Web3 storage/infrastructure systems. Meson Network is a pioneer in the decentralized CDN and bandwidth market. Meson Network has a significant edge over their competition by being one of the first movers in this industry. This advantage allows us to establish our brand and market position ahead of our competitors, greatly increasing our chances of long-term success. I have a detailed article about [Meson Network](https://ntmv.net/posts/my-thoughts-and-experiences-on-meson-decentralized-cdn-network/). 

## What is Gateway X exactly? 
Meson Team used a traffic jam and satellite city comparison to explain the Gateway X in this fantastic [blog article](https://blog.meson.network/blog/2023-04-06-meson-gateway-x). **"This situation is like the traffic problem on a highway. There is only one route to deliver goods to IPFS city (ipfs.io). No matter how much the road is widened, congestion will occur when the demand for goods increases. Meson, on the other hand, is like building numerous satellite cities around the world. Users don't have to take the ipfs.io highway; they can directly go to Meson's satellite cities to collect goods."**
![backend](/img/subcity.jpg)
I think this analogy explains Gateway X very well. The satellite city analogy here also explains very nicely how Web3 storage services can be decentralized and improved using Gateway X. This new service by Meson Network can eliminate the single point of failure, make Web3 storage services even more sovereign, and can make them faster and more reliable by distributing their content all over the world using Meson 3.0 CDN's highly distributed 30k+ nodes. 

There are some compatibility issues between Web3 services nowadays. When we consider how far Web 2 services have come in terms of integrity, the shortcomings of Web3 in this regard are even more glaring. Gateway X opens a new door in this area as well. It offers great interoperability and compatibility with Web 3.0 storage services. Users and service providers can easily integrate Gateway X to their products. I think the launch of Gateway X service is one of the most important steps in Web 3 interoperability.

Rather than providing an extensive overview of Gateway X, as it has already been thoroughly explained in a separate article, this piece will instead offer a series of quick-start tips and an analysis comparing Gateway X with its competitors.

## Gateway X quick start guide 

_(This product is still in beta. You may need to ask for whitelist)_

First of all, you need a Meson Network account to use Gateway X.  If you don't have one, you can create one [here](https://dashboard.meson.network/).

![backend](/img/dashboard-gateway-x-1.png)
> Click Gateway X

![backend](/img/dashboard-gateway-x-2.png)
> New Gateway > Choose IPFS > Enter a tag > Create

![backend](/img/dashboard-gateway-x-3.png)
> Wait a few minutes

![backend](/img/dashboard-gateway-x-4.png)
> Click edit
![backend](/img/dashboard-gateway-x-5.png)

Now your very own gateway is ready. To use it, go back to Upload > Upload to Cloud

![backend](/img/dashboard-gateway-x-6.png)

Open your dashboard, click files, upload a file and get your URL

![backend](/img/dashboard-gateway-x-7.png)
> That's it!

## Brief Comparison
As the Web3 industry continues to gain popularity, companies are introducing more products in this sector. In such a competitive market, delivering creative and superior services is crucial to building brand awareness.

Our competitors include Pinata, Filebase, and Web3.storage. While our product shares some benefits with them, it also has unique features that set it apart.

One of the most notable benefits is its vendor-agnostic design, which allows it to be used with local storage. This means that a client can be installed on a storage VPS and used to utilize its storage capacity. Additionally, we provide a managed cloud service, which is a plug-and-play solution.

Another important feature is its 1GB file cache, enabling us to deliver high-quality video files quickly. It's powered by over 30k Meson 3.0 nodes distributed worldwide, allowing us to deliver files to millions of users in seconds through our CDN node network, which is continuously expanding, with an uptime rate nearing 99.9%.

We also offer file replication to Filecoin, a dedicated upload gateway, dedicated gateway bandwidth, limitless requests, and other features.

All things considered, our product is one of the most innovative in its sector, well-positioned for the future.