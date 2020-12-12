---
layout: post
title:  "A Second Site"
date:   2020-12-10 13:25:00 +0100
description: Growing to a second site
categories: Homelab starting 
---

# The Second Site
I was lucky enough to purchase a flat in London, and that meant only one thing... a new network. 

A two bed flat, surely doesn't need much a network? Well probably not but didn't want to leave it with just an ISP router. 

## The First Iteration
The first step of the network was to choose an ISP, and the best option for this was BT. So then I got a Draytek Vigor modem to replace the BT router with. 
Then it was onto the Unifi equipment for the property. 

I kept it quite simple here to begin with, just a USG and AP-AC-Pro. This worked quite well, Lan1 on the USG and the AP used for the main lan, and then Lan2 on both for an IoT network. These devices where being managed by a cloud key at the main site. 

This set up was ... terrible. I had constant drop out of connections with the Draytek which made it unusable, especially when it didn't come back online after the drop out. 

## The Second Iteration
I got incredibly fed up with the drop outs, and the phone calls telling me it had dropped out. So I made some calls to BT and ended up moving to their business plan. This gave me two things, an ISP provided router with a modem mode and a static IP.

Two advantages here, firstly a modem that actually works, and no drop outs! Next the static IP made it a lot easier to set up a site-to-site VPN connection with my first site. 

I also added a Unifi US-60W 8 port switch. There where two reasons for this addition. To start with I was adding a Phillips Hue Bridge which of course needed an ethernet port, and I wanted to be able to put it on the IoT network. The other reason to add the switch was to remove the requirement for a POE injector. In all fairness this isn't really a pro or a con, it didn't save on a power socket which is generally a key benefit of replacing the injectors. 

The last thing that I did as part of this iteration was to set up a site-to-site VPN. The primary reason for this was to allow access to the servers at the main site. It did come with the added benefit that people at the second site could view CCTV at the first. 

And that's it really with the second site. There will be more to do here I am sure but for now it is a simple setup that just works. 