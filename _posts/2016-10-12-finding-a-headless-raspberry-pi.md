---
layout: post
title: Finding a Headless Raspberry Pi
permalink: /finding-a-headless-raspberry-pi/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>As I continue to play more and more with my Raspberry Pi 3, I was having issues setting a static IP AND being able to surf from the Raspberry Pi after. I decided to leave the Raspberry Pi with DHCP enabled and continue my tinkering.</p>
<p>This worked well when I used the Pi at home. My smaller network meant that the Pi was pretty much assigned the exact same IP for weeks. However, once I brought the Pi to the office, this was not the case. Rather than logging into the server to check the DHCP logs and find the IP addres that way, I did some Googling and found the following nmap command:</p>
<pre><code>nmap -T5 -n -p 22 --open --min-parallelism 200 192.168.1.0/24
</code></pre>
<p>Right now, there are only three Pis on the network, so figuring out which one is mine is very straightforward.</p>
<!--kg-card-end: markdown-->