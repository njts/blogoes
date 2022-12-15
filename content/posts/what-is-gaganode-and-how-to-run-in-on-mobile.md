---
title: "What is GaGaNode And How To Run It On Mobile, Windows pc, Linux Servers (Summarized)"
date: 2022-12-14T11:30:03+00:00
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
description: "GaGaNode Quick-Start Guide for Mobile, Desktop and Linux Devices"
# canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: "./img/gaganode-center.c7715456.jpeg" # image path/url
    alt: "Meson Network" # alt text
    caption: "Meson Network" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/njts/blogoes/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---
### What is gaganode?

GaGaNode is a Decentralized Residential IP + Bandwidth Marketplace. With Web3.0 technology, it aims to alleviate the global shortage of IPv4 addresses. Users can participate in the Web3 network at home using Idle Electronics even if they do not have a public network IP address. Future technologies that require home bandwidth for development can obtain real home bandwidth resources via GaGa Node.

### What are the advantages of running GaGaNodes?

To earn GaGaNode Credits, you simply need an idle Android phone, as well as a tvbox, Raspberry Pi, computer, or other electrical equipment.
Users do not need to invest in additional mining machines; instead, they simply donate their home broadband resources to earn GaGaNode Credits.

### Let's start

### Before you start, you need to register [HERE](https://out.nijatoes.com/GaGaNode-register) and create a GaGaNode account.

- https://out.nijatoes.com/GaGaNode-register

![](/img/screenshot.png)

## Runnig GaGaNode on Android phone

- Download and Install [GaGaNode](https://assets.coreservice.io/public/package/32/gaganode/1.0.3/gaganode-1_0_3.apk) android app

> Copy your token
![](/img/install_run.c4bd2c82.png)

> Start android app and enter your token
 ![](/img/android-03.5ff0f04c.jpeg)

 ### Enable Auto-starting

 > Set 'No restrictions' when start.
 ![](/img/android-01.cbbe2b89.png)

 > Enable Autostart.
![](/img/android-02.47e56405.png)

## Runnig GaGaNode on Windows PC

### Open PowerShell in Windows

- Use the “Run” window to open PowerShell
You can open Windows PowerShell with administrator privileges from Run. A quick way to launch this window is to press the `Win` + `R` keys on the keyboard. Then, type `powershell` and press Enter or click OK.

![](/img/windows-03.c050e0c7.png)

Switch from PowerShell to PowerShell Admin. If you’re already working in PowerShell but you need to switch over to `admin` mode, you can do so without closing PowerShell. Just run this command:

- `start-process powershell -verb runas`

![](/img/windows-04.6eb30a24.png)

####  1.Download & Install

`wget -Uri "https://assets.coreservice.io/public/package/20/app/1.0.3/app-1_0_3.tar.gz" -OutFile "app-windows-amd64.tar.gz" ; tar -zxf app-windows-amd64.tar.gz ; rm -Force app-windows-amd64.tar.gz ; cd ./app-windows-amd64 ; ./app.exe service install`

#### 2.Start Service

`./app.exe service start`

#### 3.Set Token

` ./apps/gaganode/gaganode.exe config set --token=your_token_here`

#### 4.Restart APP

`./app.exe restart`

#### 5.Check APP Status

`./app.exe status`

> After 1-3 minutes, you will have a new terminal record at terminals open in new node.
![](/img/windows-06.0d8b27e5.png)


## Runnig GaGaNode on Linux VPS and Desktops

### Install Dependencies Packages

`sudo apt-get update -y && sudo apt-get -y install curl tar ca-certificates`

#### 1.Download & Install

`curl -o app-linux-amd64.tar.gz https://assets.coreservice.io/public/package/22/app/1.0.3/app-1_0_3.tar.gz && tar -zxf app-linux-amd64.tar.gz && rm -f app-linux-amd64.tar.gz && cd ./app-linux-amd64 && sudo ./app service install`

#### 2.Start Service

`sudo ./app service start`

#### 3.Check APP Status

`./app status`

console output:
>`meson@meson-server:~/app-linux-amd64$ ./app status
[gaganode]:		local version:[1.0.3] latest version:[1.0.3] status:[DOWNLOADED]`

#### 4.Set Token

`sudo ./apps/gaganode/gaganode config set --token=your_token_here`

#### 5.Restart APP

`./app restart`

> ### Terminal Rsecording
[![asciicast](https://asciinema.org/a/545183.svg)](https://asciinema.org/a/545183)

> ### Notice:
>This article is a summary of the [official documentation](https://docs.gaganode.com/). I strongly recommend looking through the official documentation for more in-depth information and installation instructions









