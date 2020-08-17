---
layout: post
title: Kali VMWare Image - Could Not Get Screen Information
permalink: /kali-vmware-image-could-not-get-screen-information/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>I recently downloaded the Kali 2016.2 VMWare image to my desktop computer. I use a number of the tools on Kali for testing various applications.</p>
<p>After downloading the VMWare image, I started the VM and went to change the screen resolution. When I opened the Settings--&gt;Display screen, I was presented with:</p>
<pre><code>Could not get screen information
</code></pre>
<p>I did some Googling and found that running:</p>
<pre><code>apt-get update
apt-get dist-upgrade
</code></pre>
<p>The updates took about 15 minutes. A quick reboot and I was presented with the regular Display setting screen.</p>
<!--kg-card-end: markdown-->