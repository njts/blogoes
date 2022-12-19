---
title: "Linux Təməlli Serverlərin Təhlükəsizliyinin Yüksəldilməsi"
date: 2022-12-18T11:30:03+00:00
# weight: 1
# aliases: ["/first"]
tags: ["linux"]
author: "Nijat"
# author: ["Me", "You"] # multiple authors
showToc: false
TocOpen: false
draft: false
hidemeta: false
comments: false
description: ""
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
    image: "./img/background-g80913faae_640.jpg" # image path/url
    alt: "Meson Network" # alt text
    caption: "Meson Network" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/njts/blogoes/blob/main/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---

#### 1.Yeni istifadəçi yaratmaq
```
useradd <user>
```

#### 2.İstifadəçiyə sudo icazəsi vermək
```
usermod -aG sudo <user>
```
```
passwd <user>
```

#### 3.SSH key yaradılması

RSA
```
ssh-keygen
```

ED25519 (Tövsiyyə olunan):
```
ssh-keygen -t ed25519
```

#### 4.SSH public keyi serverə kopyalamaq
```
ssh-copy-id -i <key> user@host
```

#### 5.Serverin ssh portunu dəyişmək və şifrə ilə girişi bağlamaq üçün sshd_config faylında dəyişikliklər etmək

Orijinal faylı saxlamaq:
```
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.orig
```

sshd_config faylını nano text editor ilə açmaq:
```
sudo nano /etc/ssh/sshd_config
```

#### 6. Avtomatik yenilənmələri açmaq 
```
sudo apt install unattended-upgrades
```

```
dpkg-reconfigure --priority=low unattended-upgrades
```

#### 7.UFW firewall aktivləşdirmə
```
sudo apt install ufw
```

```
ufw allow <port>
```

```
sudo systemctl enable ufw && ufw enable
```

#### 8.Echo istəkləri (ping) bağlamaq
```
sudo nano /etc/ufw/before.rules
```

```
-A --ufw-before-input -p --icmp-type echo-request -j DROP
```

#### 9.Fail2Ban
``` 
sudo apt install fail2ban 
```
```
sudo nano /etc/fail2ban/jail.d/sshd.conf
```
```
[sshd]
enabled = true
port = ssh
filter = sshd
logpath = /var/log/auth.log
maxretry = 3
bantime = 120
ignoreip = whitelist-IP
```
```
sudo reboot
```
