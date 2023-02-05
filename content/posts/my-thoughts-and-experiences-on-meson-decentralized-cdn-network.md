---
title: "My Thoughts and Experiences On Meson - Decentralized CDN Network"
date: 2022-07-16T11:30:03+00:00
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
description: "This is my first blog post on my decentralized blog and it is about the decentralized web:)"
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
    image: "/img/meson.png" # image path/url
    alt: "Meson Network" # alt text
    caption: "Meson Network" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/njts/blogoes/blob/main/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---
The Web is going to be decentralized. Must be. Wait, what do we need to achieve a fully decentralized future? Of course, decentralized computing and edge infrastructure. When we're talking about Web3, there is always a silent moment for backend infrastructures. Most dapps, swaps, and even nft marketplace websites are running on big corporation-owned centralized datacenters like AWS, Google, and Azure/Microsoft. 

[Meson](https://meson.network) is a blockchain project working to fill part of that gap. Meson is a decentralized CDN run by people for people. It already has 30k+ edge nodes worldwide so far.
 I'm also running over 108 Meson 3.0 servers/nodes in 17 counties and 27 different cities worldwide. 
 
 ![map-1](/img/map-1.png)
 
 My total effective bandwidth is ~71 Gbps.
 It's inspiring to be a part of this amazing network. My next article will be about installing nodes for Meson Network and my experiences as a node runner. Wait for it.

Meson Network has two different CDNs. Meson 3.0 and m-cdn. M-cdn is a hybrid multi-cdn that uses a lot of third-party CDN services. Meson 3.0 is what I was looking for. It is a truly decentralized CDN with 30K nodes globally. So I decided to do some tests with it.

First of all, I've spun up a VM with an NGINX server. Later, I created a simple web page by forking [this](https://codepen.io/suez/pen/ZEqxBb) codepen repo. Uploaded to server. Now we have a running website. Let's connect it to Meson.

### Starting with Meson 3.0
Meson's dashboard has a user-friendly and easy-to-understand UI.
First, go to your DNS provider's dashboard, and create an A-record that points to your web server. Later, open dashboard.meson.network, create an account, > pull zones, > create pull zone.

![meson-dash](/img/meson-dash.png)

Enter your domain name without https. You can start using Meson for free. There is a $5 credit for new users. Give it a [try](https://dashboard.meson.network).
 
### My testing and comparisons
First, I've tried to connect my website directly to see what the end point is. Cdn redirected me to a URL. I found an IP in my country after pinging that URL's sub-domain. 
Then I noticed that the IP belongs to one of my servers, which I'm running for the Meson network. That was a fascinating moment.
Then I also connected to another node's IP, which is run by my close friend. It's amazing.

![browser-1](/img/browser-1.png)
![terminal-1](/img/terminal-1.png)
![nodes-1](/img/nodes-1.png)

### Test 2: Coverage 
I've spun up 9 VMs in 7 different cities and sent a get request to https://pz-dzulrd.meson.network to see where I will be redirected.
Results👇
![multissh](/img/multissh.png)
- Paris 🇫🇷 (a1) - Paris 🇫🇷 (51.178.161.211)
- Seul 🇰🇷 (a10) - Seul 🇰🇷 (20.41.117.166)
- Sydney 🇦🇺 (a11) - Sydney 🇦🇺 (20.211.98.179)
- Hong Kong 🇭🇰 (a12) - Hong Kong 🇭🇰 (20.187.102.213)
- Hong Kong 2 🇭🇰 (a14) - Hong Kong 🇭🇰  (20.187.147. 38)
- Hong Kong 3 🇭🇰 (a16) - Hong Kong 🇭🇰  (20.187.147.38) 
- Oslo 🇳🇴 (a13) - Oslo 🇳🇴  (51.13.112.214)
- Chennai 🇮🇳 (a15) - Pune 🇮🇳 (20.219.147.47)
- Virginia 🇺🇸 (a17) - Montreal 🇨🇦 (51.222.210.164)

### Test 3: Gtmetrix one-to-one comparison
I ran this test on two identical copies of this page. One copy is running on my single VPS, the other one is served by Meson Network. The results say everything. Meson is the clear winner.

![compare-1](/img/compare-1.jpg)
[Report link](https://gtmetrix.com/compare/3ojoLI6g/azZfx8uM)

----
There is only one red column, and it's because of redirecting. I will explain how this problem can be solved with anycast shortly. 

As you saw, I didn't compare Meson with other CDN providers like Cloudflare, Bunnycdn, and Cloudfront because I don't think it's fair to compare them yet. However, I will when the time comes. At the end of the day, it works well.

### Stability
I did not encounter any performance issues during the period I tested. There were a few connection drops for some specific locations, for example, Hong Kong and Shenzen, but generally, I can say that Meson has reliable service. 

### Pricing

The pricing is really simple. $0.01/Gb.
  
It's cheap compared to other alternatives. However, I think it will be a little cheaper in the future.
 
### What I think is missing in this project
I think they must build their own anycast network asap.

 
Anycast is a network addressing and routing methodology in which a single destination IP address is shared by devices in multiple locations. The nearest device responds to requests, giving end users access to fast service without the high latency issues that can be caused by traditional geo-location solutions. This reduces latency as well as packet loss rates because data can travel on routes that are optimized for speed and not just the shortest distance. 
> Meson 3.0 current architecture
![meson-netw](/img/meson-netw.png)

> Anycast example (google.com architecture)
![google-anycast](/img/google-anycast.png)

Anycast network will increase the CDN performance tremendously. They are currently using a single VM to share the network traffic. That VM might be powerful and well-located, but it's still a single point of failure. That's why I think anycast is so important in the future of Meson.
 
### Future
Nobody knows what will happen in the future. But I think Meson Network can be the next Airbnb for the CDN industry.
 
Fun fact: This website is also powered by Meson and Akash.

..Akash? Yes, my next post will be about it :)
