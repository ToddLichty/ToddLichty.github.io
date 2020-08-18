---
layout: post
title: Ubuntu - Monitor Traffic Over VPN Tunnel
permalink: /ubuntu-monitor-traffic-over-vpn-tunnel/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>The script below uses the <code>watch</code> command to execute the <code>ifconfig</code> program every second and highlight the differences. I recently needed to verify that all my traffic was going through a specific VPN tunnel.</p>
<pre><code class="language-shell">watch -n 1 -d ifconfig tun0</code></pre>
<!--kg-card-end: markdown--><figure class="kg-card kg-image-card"><img src="/images/vpn_tunnel.JPG" class="kg-image"></figure>