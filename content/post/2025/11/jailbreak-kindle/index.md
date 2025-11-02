---
date: '2025-11-01T13:53:54-04:00'
title: 'Jailbreaking a Thrifted Kindle'
categories:
  - projects
  - thrifting
tags:
  - kindle
  - jailbreak
  - calibre
weight: 1
---

## Today I Decided to Jailbreak a Kindle

After finding a Kindle at a thrift store today, I decided to try something out that I've been seeing online recently:
Kindle jailbreaking. I saw a video about it months ago, but I didn’t have a Kindle that I was willing to try it on.

{{<youtube Qtk7ERwlIAk>}}

The thrifted Kindle was a little bit of a gamble because it was completely dead, and I wasn’t sure if I was going to be
able to disassociate the Kindle from its previous owner. But at $10, potentially bricking a Kindle was worth it. I
brought it home, plugged it in, said a little prayer, and half hour later came back to a charging Kindle! There was no
passcode on it (score!) and it appeared to be a Kindle Paperwhite.

Before I could get started on the fun, I needed to register the Kindle to my Amazon account. In order to log into my
account, I had to manually update the firmware for the Kindle as it is way passed its over the air update lifecycle. I
was able to do that by following the instructions
[here](https://www.amazon.com/gp/help/customer/display.html?nodeId=GFAE5G5UGCYA25DW). Found the latest firmware
[here](https://www.amazon.com/gp/help/customer/display.html?nodeId=GKMQC26VQQMM8XSW). And I used
[this](https://www.amazon.com/gp/help/customer/display.html?nodeId=GK33S847NN4V6Y83) guide to identify which Kindle I
had.

I was able to determine that I had a Kindle Paperwhite from the device info (see below), but I had to do some detective
work to figure out which generation of the Paperwhite I had. From the charging cable the device used (micro-usb) and by
how much storage the Kindle had (~1.43GB available according to my Mac) I had two options: Gen 5 or Gen 6 Paperwhite. My
last clue was the active firmware version (5.7.4). That's greater than the last supported version for the 5th Gen, so it
looked like I had a 6th Gen Kindle Paperwhite on my hands!

{{< gallery >}}

    {{< figure src="./images/old-firmware.jpg" caption="Old Device Information" alt="Old Device Information" width="300px" >}}

    {{< figure src="./images/new-firmware.jpg" caption="New Device Information" alt="New Device Information" width="300px" >}}

{{< /gallery >}}

Once the latest firmware was installed and the Kindle was registered to my account, I got started with the fun bit:
jailbreaking. Since this was an older model (using firmware version <= 5.18.0), the WinterBreak mod was still viable for
me to use. I followed the instructions from [this](https://Kindlemodding.org) site and repeated a few steps as necessary
(it’s an old device, I had to treat it gently if I wanted results). And bada bing bada boom I had a jail broken Kindle.
It still couldn’t do things I wanted it to yet. So I got started on adding extensions.
[KindleForge](https://github.com/KindleTweaks/KindleForge) is a GUI package manager that comes pre-configured with my
two main extensions: [KOReader](https://github.com/koreader/koreader) and Toggle ADs. KOReader does most of the heavy
lifting in terms of features: allowing multiple file formats, Calibre integration, and RSS feeds. Toggle ADs gets rid of
the bane of my existence: persistent, pervasive advertizing. For that, it deserves to be shouted out separately.

I was able to connect my Kindle to my Calibre instance in order to wirelessly download books. KOReader’s built-in plugin
that utilizes Calibre’s content server didn’t work for me unfortunately. I’m 90% sure it’s a networking issue with
docker that I would have spent more time debugging if I didn’t uncover a different avenue via ODPS (Step 5 from
[this](https://blog.classstruggle.tech/making-calibre-web-work-with-koreader/) tutorial). From what I’ve seen online,
both of these methods basically do the same thing, so I’m satisfied.

Once I had my books covered, I wanted to personalize the Kindle a little. Honestly, this was one of the major reasons I
wanted to jailbreak this thing. I wanted to have cute screensavers for my Kindle. I followed this
[guide](https://Kindlemodshelf.me/customscreensavers.html) to get my screensavers up and working. One thing I noticed is
if you put your Kindle to sleep while outside of the KOReader app, you’ll still have the default screensavers or special
offers.

{{< gallery >}}

    {{< figure src="./images/cover1.jpg" alt="Cat screensaver" width="300px">}}

    {{< figure src="./images/cover2.jpg" alt="Read banned books screensaver" width="300px" >}}

{{< /gallery >}}

## Post Mortem

I’m pretty satisfied with my jailbroken Kindle. If I ever come across another cheap Kindle with larger capacity, I would
definitely do this again. I do want to try to get Tailscale installed on it so I would be able to download books from
Calibre from anywhere instead of just my house. I did find a
[KUAL extension](https://github.com/mitanshu7/tailscale_kual) that allows for that, but that will be tinkering for
another day. Or maybe I’ll finally get a reverse proxy server running properly ¯\ _(ツ)_/¯. Only time will tell.

I will warn, KindleForge technically is not supported for my firmware version (the devs recommend 5.13.7 or greater).
The build is unstable on lower firmware versions but it's working fine for me so far.

## Resources

- Kindle Modding Guide (https://kindlemodding.org/)
- Kindle Modding Resources (Lots of good screensavers can be found here) (https://kindlemodshelf.me/index.html)
- KOReader (https://github.com/koreader/koreader)
- Filler files for your kindle (https://github.com/bastianmarin/Kindle-Filler-Disk/)
- Resize images for screensavers (https://www.ebookscreensaver.com/)
