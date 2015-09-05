---
title: How to Reset a PC’s Master Password
author: logan
layout: post
date: 2012-12-14
url: /2012/12/how-to-reset-a-pcs-master-password/
categories:
  - Projects
tags:
  - bios
  - linux
  - reuse
---
I inherited a _broken_ PC, a Toshiba Satellite M305D, from family. The machine is only a few years old and still functions fine. The problem was that a password was being required after the BIOS loaded (before Windows Vista). I did not have a rescue disk and the pc would not boot off of a Windows or Live Ubuntu disk (CD or USB). I followed trails around the internet to reset the password and found that by pulling the CMOS battery off of the motherboard would reset the passworld&#8230; and reset it did!

Here&#8217;s the steps that I took to reset the master password:

  1. Remove the battery and case components.
  2. Remove the hard drive (and RAM, possibly)
  3. Remove the screws from the bottom side of the laptop
  4. Remove a small cover on the north side of the keyboard. Remove the respective screws and detach the ribbon cable from the motherboard.
  5. Remove the battery. ON this machine, it looked like a sealed disk with 2 leads which attached to the motherboard via plug.
  6. Due to time, I waited till the next day to plug the battery back in, but 30 minutes is a good recommendation.
  7. Re assemble pc.

At this point I had already formatted the hard drive since I was planning on installing Ubuntu on it. Plug in a bootable drive (make sure the BIOS boot order has USB or CDROM appear before the HDD). It worked like a charm and I wrote this post on a rescued machine destined for the trash&#8230;or recycling center.