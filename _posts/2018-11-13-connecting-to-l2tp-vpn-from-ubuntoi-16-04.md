---
layout: post
title: Connecting to L2TP VPN from Ubuntu 16.04
permalink: /connecting-to-l2tp-vpn-from-ubuntoi-16-04/
author: Todd Lichty
---
<p>I had to setup an L2TP connection from my new Ubuntu laptop. I was surprised that this was not naively built into Ubuntu. The steps that I followed to make this work were:</p><!--kg-card-begin: markdown--><pre><code>sudo add-apt-repository ppa:nm-l2tp/network-manager-l2tp  
sudo apt-get update  
sudo apt-get install network-manager-l2tp  
sudo apt install network-manager-l2tp-gnome
</code></pre>
<!--kg-card-end: markdown--><p>A quick reboot later and I was in business.</p>