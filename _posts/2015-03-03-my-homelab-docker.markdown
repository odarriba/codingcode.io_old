---
layout: post
title:  "My homelab server and why I'm using docker"
date:   2015-03-03 13:00:00
author: odarriba
comments: true
image: /assets/posts/docker.jpg
tags: homelab hp microserver gen8 docker virtualization
---

**I've ever had a do-it-yourself mind.** And according to that and my love for sysadmin stuff, I've ben running my own homelab server since approximately a year and a half ago.

Recently i've moved to a brand new [HP Microserver Gen8][hpmicro], which is curruntly running in my home. The main features with which it is currently running are:

* **Intel Celeron G1610T** ([specs][celeronspecs])
* **10 GiB of DDR3 RAM**, ECC Unbuffered ([Amazon ES][ramlink])
* Two RAID1 mirrors of **250GiB** and **1TiB**.
* 2 network connections (one for **iLO** and another to provide connectivity service).

Despite the fact that I plan to upgrade the processor in a future, it's currently running low profile services, so at the moment it's enought for me.
<!--more-->
As for the software, it's running an **Ubuntu Server** distribution, in which top has a **Docker** server providing the virtualization required to provide several services without having problems, because as long as **the containers provide isolation**, the base operating system remains untouched.

<img title='An HP Microserver Gen8' src='/assets/posts/microserver.jpg' class='center-block md-size' />

## Why Docker?
<img title='Docker' src='/assets/posts/docker.jpg' class='pull-right sm-size' />
In the past I used to run virtualized machines in order to be able to *'disconnect'* a service when I want, but thanks to the recomendations of my friend [Daniel][demil133], I decided to spend some time learning how **Docker** works, and implementing it as my *service isolation solution*.

Nowadays I'm running a **Time Machine service** inside it's own docker container ([here is my repo][timemachine-repo]), but I'm planning to run a LAN streaming service with *Plex* and a container to run my degree's final project. But these are just future plans.

An important fact about Docker is that it has an **incredibly huge community** which uploads their docker containers to [Docker Hub][docker-hub], so you can take previously made containers to use them in your machine.

**If you want to run virtualization and Docker isn't enough**, my recommendation is to have in mind what you need and what don't. For example, ESXi provides a better virtualization infrastructure, but it's free client is outdated and doesn't receive maintenance, so may be it's a bad option (especially if you have a *non-Windows* machine). In my case, before changing to Docker I was running the machines under Windows Server 2012, but just because of the RDP facilities.

[celeronspecs]:	http://ark.intel.com/products/71074/Intel-Celeron-Processor-G1610T-2M-Cache-2_30-GHz
[hpmicro]:	http://www8.hp.com/uk/en/products/proliant-servers/product-detail.html?oid=5384977&jumpid=reg_r1002_uken_c-001_title_r0002
[ramlink]:	http://www.amazon.es/gp/product/B008LMNHB8
[demil133]:	https://github.com/demil133
[timemachine-repo]:	https://github.com/odarriba/docker-timemachine
[docker-hub]: https://hub.docker.com/