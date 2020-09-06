---
layout: post
title:  "My Homelab Part 2"
date:   2020-09-06 13:25:00 +0100
description: Starting my homelab
categories: Homelab starting 
---

# My Homelab - Part 2

## Where did I go next?
Quite a few new things where added and a few things changed, and quite a few are not in any photos.

The first main change was that the rack moved, it was in the shared office downstairs but having created some more space in my own office upstairs we moved it up there. This came with a few benefits, for the family the fact that they didn't have to listen to the rack anymore when working. For me it meant that it was a lot closer to me so working on things became a lot easier. Very quickly I found myself tinkering on things more, including the days where I was working from home I'd often be installing something new or running updates etc.

With my ever growing interest, came yet more equipment and new things to do. One of the first things that we did was install new access points and CCTV around the house. With this came a new network switch. At this point we opted to get a Unifi Switch 24-250w. This was a perfect switch for what we needed, for starters it integrated straight in with all of our current equipment, and importantly it provided 24v POE which is required for our two original AP-AC-LR as they where bought before the change to POE+. It also gave me more gigabit ports which meant more changes to the virtual environment.

One of the first things that I started to learn about was NIC teaming, whilst not a massively important feature for my setup, it was interesting to learn about and test it in wasys such as just pulling out random network cables and watching things keep running.

![]({{site.url}}/assets/OfficeRack.jpg)

This photo shows the new CCTV cameras being prepared for installation, mainly just setting a static IP, naming them and also getting them added to my NVR of choice Blue Iris.

The other new addition in this photo is an Apple XRaid, I got this for free but things where not quite as I had hoped. My plan for this was to use it as a SAN for the R710, however I would not be so lucky. The main issue that I ran into was the support for the software needed to configure it, I couldn't find it! When I did finally get a copy of the software running I could never get it to connect to the XRaid. With this in mind, my friend and I decided it would be a cool thing to rip the internals out and turn it into a backup server with some different hardware, so that is what I did. 

![]({{site.url}}/assets/BackupRig.jpg)

Here you can see how it turned out... it was a little jank but it did work. I am running a cheap gigabyte motherboard, an i5, 8GB of ram and a HP raid card from my friend. Surprisingly it worked. It was setup to run Windows Server 2016 and using Veeam Backup and Replication as my backup software of choice. I was able to use an NFR license for this giving me all of the features for a year. It worked well, a quiet setup that would do daily backups of all of my important virtual machines, such as domain controllers and also the file shares on the host itself.

## More additions
### Cisco
Next thing I did was decided that I needed to use other switches, not just Unifi that can be configured from a nice web GUI. So to eBay I went, and found myself a Cisco 3750, a 48 port gigabit switch with 4 gigabit SFP ports as well.

I think that I wildly underestimated the learning curve here, suddenly I was configuring everything on a switch using a console cable and Putty. It went pretty well. The first day of owning it I had core virtual machines connected to it and fully accessible, so a win. I went on to further learn and setup link aggregation using my NIC Teams on the R710. 

The major roadblock that I hit with the Cisco was the ability to use another router for inter-VLAN routing. Turns out all I needed to do was setup the SFP ports as trunk ports and away I went, if only I had found the right google page first. 

### Another server
The next thing to be added was another server, this time a Dell R610. I bought this on a bit of whim but it turned out to be perfect for what I needed. 

I had recently started self hosting some things, rocket-chat and a wiki for example. I had decided to setup a DMZ and the addition of this server let me have a fully segregated hosting environment for these additions. 

### Yet another server
A deal came up and I couldn't help myself, I had caught the homelab bug. This time I found a Dell R310 on Facebook Marketplace for £80. Not a very powerful server but it did have 4 drive bays and with the use of a disk drive to 2.5" adaptor it also had an SSD. It also came with rails included in the price so very quickly I had this installed and needed to come up with a purpose for it.

Turns out that the backup rig that had been working well, it wasn't working that well after all. The motherboard and the raid card where not really compatible and it caused a lot of issues whenever I wanted to reboot it etc. So this new R310 became the new backup server and the XRaid case was once more dormant. 

Turns out that this was a very capable machine for what I needed and ran veeam with no issues what so ever. It even had iDrac enterprise so I could easily see what was going on without being in the office, the DIY job did not have an ipmi at all. 

## What next?
With the next post comes a new site and a simple network setup, but not without it's problems. A lot of blood, sweat and tears, well maybe not the blood, but a lot of learning.