---
title: "Wordpress Website, But Without PHP"
date: 2022-10-18T11:30:03+00:00
# weight: 1
# aliases: ["/first"]
tags: ["web development"]
author: "Nijat"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: true
draft: false
hidemeta: false
comments: false
description: "Easy-to-use of wordpress and speed of static website.
In this short article, I explain how I serve my new Meson.guru Wordpress websites without PHP."
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
    image: "./img/wordpress-without-php.jpg" # image path/url
    alt: "Wordpress" # alt text
    caption: "Wordpress" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/njts/blogoes"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---
### What is Meson Guru? 

Meson.Guru is  a semi-automatic news aggregator for Meson Network. You can find all the latest news, tweets, and videos about Meson Network in one place. We do not republish or store any material on our server. We simply provide a link to the relevant content.

![meson.guru](/img/mesonguru.png)
 

### Backed

When the idea of creating such a website came to me, I decided to build my own little CMS with node.js. After writing the first hundred lines of code, I realized it wouldn't be as simple as I thought and decided to use one of the popular CMSs. I chose Wordpess because it provides numerous options and flexibility. But there was a problem. I don't like PHP. it's slow and outdated. You understand what I mean. Meanwhile, I decided to deliver this site to the end user without any PHP runtime. Clean and fresh.. 👌

### How it works

WordPress 6.0 is installed on the internal network of my super private server. I'm still building the website with Wordpress. I set up a few cron jobs with a five-minute interval loop. First cron job is for Simply Static plugin and GitHub pushes. Simply Static plugin generates a new static version of the wordpess generated website every five minutes and saves it to my super secret server's /static directory. Following that, the second github push code runs and uploads that static files to my Github repo, sends a telegram notification, chekcs the server state etc.
That is all. Our website is now static.

![backend](/img/archt.jpg)

- Auto static website build, github push and telegram notification
```
#!/bin/bash
start=`date +%s.%N`
cpuload=$(top -bn1 | grep load | awk '{printf "%.2f%%\t\t\n", $(NF-2)}')
ramload=$(free -m | awk 'NR==2{printf "%.2f%%\t\t", $3*100/$2}')

# Build static website
cd /var/www/html
wp cron event schedule simply_static_site_export_cron --allow-root
wp cron event run --due-now --allow-root
cd /var/www/static
status=$(git diff --name-only)

# Time stamp
builddate() {
  date +"%Y/%m/%d %H:%M:%S"
}
end=`date +%s.%N`
buildtime=$( echo "$end - $start" | bc -l )
echo "$(builddate) buildTime ${buildtime}         cpuLoad: ${cpuload} ramLoad: ${ramload}"  >> logs.txt
sed -e 's/\s\+/,/g' logs.txt > logs.csv

# Github push
git add .
git commit -m "$(builddate) UTC  auto commit"
git push -u origin main --force


# Telegram notification
/var/www/private-sripts/telegram-notf.sh "
|--------------changes-----------|
${status}
                       |
|---------------system------------|
| build time ${buildtime}
| cpu load: ${cpuload}
| ram load: ${ramload}
                       |
|------------build date----------|
| $(builddate)
|--------------------------------------|
"
/var/www/static/custom-scripts/mem-check.sh
responsetime=$(curl -H 'Cache-Control: no-cache, no-store' -s -w '\nLookup time:\t%{time_namelookup}\nConnect time:\t%{time_connect}\nPreXfer time:\t%{time_pretransfer}\nStartXfer time:\t%{time_starttransfer}\n\nTotal time:\t%{time_total}\n' -o /dev/null "https://meson.guru/?$(date +%s)")
results="$(builddate) ${responsetime}"
echo ${results} > responsetime.temp
```

- Telegram notification handler
```

#!/bin/bash
    
GROUP_ID=<group_id>
BOT_TOKEN=<bot_token>

# this 3 checks (if) are not necessary but should be convenient
if [ "$1" == "-h" ]; then
  echo "Usage: `basename $0` \"text message\""
  exit 0
fi

if [ -z "$1" ]
  then
    echo "Add message text as second arguments"
    exit 0
fi

if [ "$#" -ne 1 ]; then
    echo "You can pass only one argument. For string with spaces put it on quotes"
    exit 0
fi

curl -s --data "text=$1" --data "chat_id=$GROUP_ID" 'https://api.telegram.org/bot'$BOT_TOKEN'/sendMessage' > /dev/null
```
![tg](/img/tg.png)
- Memory check
```
#!/bin/bash

memlimit=50000 # in KB

# Reboot if memeory is lower than memory limit
mem=$(cat /proc/meminfo | egrep "^MemFree" |awk '{print $2}')
if (( mem <= $memlimit )); then
/var/www/private-sripts/telegram-notf.sh "Free memory is $(($mem/1024)) MB and it's lower than $(($memlimit/1024)) MB limit, so we restart the system"
/var/www/static/custom-scripts/reboot.sh
else
/var/www/private-sripts/telegram-notf.sh "Memory is fine. $(($mem/1024)) MB is free"
fi
```

- Cron tab
```
@reboot /var/www/static/custom-scripts/cron.sh
*/5  * * * * tmux send-keys -t 0 "/var/www/static/custom-scripts/auto-git.sh" Enter
0 */4 * * * /var/www/static/custom-scripts/reboot.sh
55 23 * * * /var/www/private-sripts/tg-file.sh
```
Full code is on https://github.com/njts/mesonguru
### Public hosting.

Now we need a hosting to host our static files. Most people will most likely consider Netlify as a solution for this. It's fast and free. However it doesn't fit in this situation. Netlify provides 300 minutes free build time each month. As I mentioned above, we rebuild meson.guru website every 5 minutes, and each rebuild takes about 10 seconds. A quick calculation reveals that we need approximately 1.4k minutes of build time each month. Extra 1000 minutes in Netlify cost about $14 per month.

There are few cheap alternatives to host and deploy a static website. CDN store buckets like BunnyCDN, S3 free tier and self-hosted solutions. 
I like self-hosted solutions because I have more control over them. I chose [Coolify](https://coolify.io) to host my website. Coolify is a self-hosted Heroku/Netlify alternative with a ton of great features. It has an auto deploy feature, so whenever my cron job pushes a new version of meson.guru to github, it will deploy the new versions automatically.

I rented a VPS from Hetzer for $5 per month, installed Coolify on it, and used Coolify to deploy the static version of Meson.guru. It is less expensive than Netlify, and I can run a lot of other applications on the same vps.

![coolify](/img/coolify-1.png)
![coolify](/img/coolify-2.png)

This was also a fun experience. I learned a lot of new things and shared some of them with you.
End of the day, this is my simple solution to serve WordPress websites without PHP runtime.

Thanks for reading.