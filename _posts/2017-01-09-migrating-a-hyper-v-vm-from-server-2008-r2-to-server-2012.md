---
layout: post
title: Migrating a Hyper-V VM from Server 2008 R2 to Server 2012
permalink: /migrating-a-hyper-v-vm-from-server-2008-r2-to-server-2012/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>With our new development methodology running smoothly for the past few months, it was time to start cleaning up the server rack. There were a few old 2008 servers that were hosting some of our low priority servers as VMs in Hyper-V. With our new powerhouse server running flawlessly, I wanted to start consolidating the servers onto one.</p>
<p>I was surprised to find that you could not easily migrate a VM from 2008 to 2012. Since these were non-mission critical servers, it was quicker (and easier) for me to just shut them down, copy the VHDX files from the old host to the new one and then setup a new VM using these old hard drives.</p>
<p>The NICs had to be reinstalled but Windows did this automatically for me. I did have to go and reassign the static IP addresses, but that was all the hand holding I had to do.</p>
<p>All in all, this was a very painless process. And I was able to turn off one of our older physical servers. Time for the recycling facility. :)</p>
<!--kg-card-end: markdown-->