---
title: "GaGaNode Nedir, Nasıl Kurulur - Android, Windows, Linux Hızlı Kurulum Kılavuzu"
date: 2022-12-14T11:30:03+00:00
# weight: 1
# aliases: ["/first"]
tags: ["web3"]
author: "Nijat"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "GaGaNode Hızlı Kurulum Kılavuzu"
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
    image: "./img/gaganode-center.c7715456.webp" # image path/url
    alt: "Meson Network" # alt text
    caption: "Meson Network" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/njts/blogoes/blob/main/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---

### Gaganode nedir?

GaGaNode, Merkezi Olmayan Bir Konut IP + Bant Genişliği Pazar Yeridir. Web3.0 teknolojisi ile IPv4 adreslerinin küresel eksikliğini azaltmayı hedefliyor. Kullanıcılar, genel bir ağ IP adresine sahip olmasalar bile boşta kalan elektronik cihazları kullanarak evde Web3 ağına katılabilir. Geliştirme için ev bant genişliği gerektiren gelecekteki teknolojiler, GaGa Düğümü aracılığıyla gerçek ev bant genişliği kaynakları elde edebilir.

### GaGaNode'ları çalıştırmanın avantajları nelerdir?

GaGaNode Kredileri kazanmak bir Android telefon, tvbox, Raspberry Pi, veya bir bilgisayar kullanılabilir.
Kullanıcıların ek madencilik makinelerine yatırım yapmasına gerek yoktur; bunun yerine, GaGaNode Kredileri kazanmak için evdeki geniş bant kaynaklarını kullanırlar.

### Hadi başlayalım

### Başlamadan önce [BURAYA](https://out.nijatoes.com/GaGaNode-register) kaydolmanız ve bir GaGaNode hesabı oluşturmanız gerekir.

- https://out.nijatoes.com/GaGaNode-register

![](/img/screenshot.png)

## GaGaNode'u Android telefonda çalıştırma

- [GaGaNode](https://assets.coreservice.io/public/package/32/gaganode/1.0.3/gaganode-1_0_3.apk) android uygulamasını indirin ve kurun

> Tokeninizi kopyalayın
![](/img/install_run.c4bd2c82.png)

> Android uygulamasını başlatın ve tokeninizi girin
 ![](/img/android-03.5ff0f04c.jpeg)

 ### Otomatik başlatmayı etkinleştir

 > Başlatırken 'Kısıtlama yok'u ayarlayın.
 ![](/img/android-01.cbbe2b89.png)

 > Otomatik Başlatmayı Etkinleştir.
![](/img/android-02.47e56405.png)

## GaGaNode'u Windows PC'de Çalıştırma

### Windows'ta PowerShell'i açın

- PowerShell'i açmak için "Çalıştır" penceresini kullanın
Çalıştır'dan yönetici ayrıcalıklarıyla Windows PowerShell'i açabilirsiniz. Bu pencereyi başlatmanın hızlı bir yolu, klavyedeki "Win" + "R" tuşlarına basmaktır. Ardından, "powershell" yazın ve Enter'a basın veya Tamam'ı tıklayın.

![](/img/windows-03.c050e0c7.png)

PowerShell'den PowerShell Yöneticisine geçiş yapın. Halihazırda PowerShell'de çalışıyorsanız ancak "yönetici" moduna geçmeniz gerekiyorsa, bunu PowerShell'i kapatmadan yapabilirsiniz. Sadece bu komutu çalıştırın:

```
start-process powershell -verb runas
```

![](/img/windows-04.6eb30a24.png)

#### 1.İndirin ve Kurun

```
wget -Uri "https://assets.coreservice.io/public/package/20/app/1.0.3/app-1_0_3.tar.gz" -OutFile "app-windows-amd64.tar.gz" ; tar -zxf app-windows-amd64.tar.gz ; rm -Force app-windows-amd64.tar.gz ; cd ./app-windows-amd64 ; ./app.exe service install
```

#### 2.Servisi Başlatın

```
./app.exe service start
```

#### 3.Tokeninizi girin

```
./apps/gaganode/gaganode.exe config set --token=your_token_here
```

#### 4.Servisi yeniden başlatın

```
./app.exe restart
```

#### 5.Servis Durumunu Kontrol Edin

```
./app.exe status
```

> 1-3 dakika sonra websitesi üzerinde bir terminal kaydınız olacaktır.
![](/img/windows-06.0d8b27e5.png)

## GaGaNode'u Linux VPS ve Masaüstü Bilgisayarlarda Çalıştırma

### Gereksinim Paketlerini Kurun

```
sudo apt-get update -y && sudo apt-get -y install curl tar ca-certificates
```

#### 1. İndirin ve Kurun

```
curl -o app-linux-amd64.tar.gz https://assets.coreservice.io/public/package/22/app/1.0.3/app-1_0_3.tar.gz && tar -zxf app-linux-amd64.tar.gz && rm -f app-linux-amd64.tar.gz && cd ./app-linux-amd64 && sudo ./app service install
```

#### 2.Servisi Başlatın

```
sudo ./app service start
```

#### 5.Servis Durumunu Kontrol Edin

```
./app status
```

Terminal çıktısı:
>`meson@meson-server:~/app-linux-amd64$ ./app status
[gaganode]:		local version:[1.0.3] latest version:[1.0.3] status:[DOWNLOADED]`

#### 3.Tokeninizi girin

```
sudo ./apps/gaganode/gaganode config set --token=your_token_here
```

#### 4.Servisi yeniden başlatın

```
./app restart
```

> ### Terminal Kaydı
[![asciicast](https://asciinema.org/a/545183.svg)](https://asciinema.org/a/545183)

> ### Bilgilendirme:
>Bu makale [resmi kurulum kılavuzunun](https://docs.gaganode.com/) bir özetidir. Daha ayrıntılı bilgi ve kurulum talimatları için kurulum kılavuzuna bakmanızı tavsiye ederim.






























