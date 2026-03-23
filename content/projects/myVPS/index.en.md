---
title: "Setting up and hardening my VPS"
date: 2026-03-20T10:00:00+02:00
draft: true
toc: false
images:
tags:
  - Linux
  - Interests
---
I’ve been toying with the idea of getting a VPS for hosting servers [Mumble, etc.] or quickly setting something up at home when I’m away, but mainly to bypass my internet provider’s NAT. This problem has been haunting me since childhood, when I wanted to set up a Minecraft server and play with friends, but the ever-present "port forwarding" was the stumbling block to all my efforts.

## Why
I always like to start by explaining why I’m doing these things in the first place. Here it’s clear: the main goal is essentially a proxy—simply to bypass NAT. Just what I wrote above, but that’s not all. 

I see this as an opportunity to get my hands on the actual administration of a Linux server that isn’t tucked away in a closet at my place, where the only threat is a power outage. As a Linux user who likes FOSS and the like, I want to get a feel for real Linux server security. By that, I don’t just mean turning on UFW and then spending half an hour figuring out why I can’t SSH in. I’ve heard about fail2ban, knockd, and the like more than once, and their operating principles fascinated me; and actually revealed how server protection can be intimidating, but also very educational. I personally didn’t expect it to be so easy (within the context of a home lab/home setup.. certainly not in a professional environment ;) ).

I’d say my biggest inspirations were the “Welcome to the Game” series and the MSI router I got from a teacher in high school. In both cases, I encountered “time-limited access”. Whether in the game, where players could only connect to certain pages at specific times, or that old router, which had a "from when to when" port permission option in its web GUI.

That router in particular caught my attention. It’s a damn old MSI <add name>, which sometimes goes into a "half-dead" state and I have to reset it to factory settings. Then that knowledge spilled over into that game, where I've realized that the "bad guys" don’t actually wait until exactly 3:00 PM to manually run `ufw allow X/Y`, but simply set up some rule, whether in a some network device or some systemd timer.

## Choosing a Hosting Provider [No Sponsorship]
I’m human, which means I’m lazy, and I like to tinker with automation, which means I’m extra lazy.

I went to CZ.NIC and checked if my domain was available. I immediately looked at the registrars and picked the “best” one. That led me to ZONER, aka czechia.com, aka ZONER CLOUD—call it what you will.

I bought the volchar.dev domain on czechia.com and a VPS Basic on ZONER CLOUD. I don’t get the disorganization in the names...

## Battle Plan for Operation "VPS"

I won't lie, despite me being extremely lazy, I'm also extremely paranoid. So before even turning on the VPS, I looked online and on YouTube to see how to thoroughly secure it. Based on the basic information I gathered, I decided on the following:

  - 'Create a non-root user in the SUDO group as quickly as possible'

    - So that I can disable logging in as ROOT via SSH

  - 'Create PUB and PRIV keys for SSH; password-less login per device'

    - So if someone wants to connect, they must have a key and I can disable password logins
  
  - 'Change the ports on the services I will be providing'

    - SSH isn’t on 22, so WG isn’t on default port, etc., but this isn’t a hard rule.

  - 'UFW will ignore pings—it can’t be seen, it doesn’t respond, as if it wasn't there in the first place'

  - 'Fail2ban, knockd, disable ports I’m not currently using'

  - 'Automatic updates for security-related packages'

With this setup, I have a fortress that can only be accessed if you: have a valid key, are on the guest list, and don’t ban yourself after a few failed attempts.

#### A Little Look into the Future

---

Continuing with this metaphor, other paths aren’t obvious, if they even exist. Only SSH is open 24/7, and I enable the services I occasionally use via on/off scripts before and after use.

---

#### A Look Back

This might seem excessive, even paranoid to some, but I’m doing this just in case I forget about the VPS later or don’t have time to manage it properly, so that it’s as secure as possible from the very start and is effectively impenetrable when idle.

## First connection to the VPS