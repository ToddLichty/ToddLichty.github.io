---
layout: post
title: Slow Hyper-V Guest OS Networking Speeds
permalink: /slow-hyper-v-guest-os-networking-speeds/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>This is more a post so that I can recall what the final solution was should I ever run into this again.</p>
<p>After configuring our new server and installing two hyper-v virtual servers on the host OS, I noticed that the network transfers within the guest OSs were BRUTALLY slow. As in &lt; 1MB/s. I assumed that I had configured the Virtual Switch incorrectly or that all three servers were using the same NIC (even though I configured them to all have their own dedicated one).</p>
<p>I beat my head against the wall for 20 minutes and then turned to every IT workers favorite tool Google. I found this <a href="https://www.reddit.com/r/sysadmin/comments/2k7jn5/after_2_years_i_have_finally_solved_my_slow/">article</a> which walked me step-by-step through the solution.</p>
<p>A quick reboot later and the network speeds were back to normal.</p>
<!--kg-card-end: markdown-->