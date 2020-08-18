---
layout: post
title: VPN Routing Issues
permalink: /vpn-routing-issues/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>Every week, I work from an arena while my son has an hour hockey practice. I see this as time to clean up my inbox, finish small jobs and get myself ready for the next week.</p>
<p>Last week, there was a new WiFi network setup in the arena. After connecting to the WiFi, I fired up OpenVPN and was able to successfully connect to the VPN.</p>
<p>I started RDP and tried to connect to my desktop. The connection failed. I disconnected the VPN, connected again and tried to RDP again. The connection failed yet again. I decided this was the internet Gods telling me to take Saturday off and do something else. :)</p>
<p>This morning, I tried to connect again. The VPN connected again without issue but the RDP connection was refused. I figured it was time to try and get this solved. I tried pinging a couple of the servers and my workstation but that was unsuccessful.</p>
<p>I looked at the reply (from 10.172.255.251) and realized that this was a routing issue. I checked my routing table and found the offending entry:<br>
<img src="/images/initial_routes.PNG" alt=""></p>
<p>I opened an admin command prompt and ran:</p>
<pre><code>route delete 10.0.0.0
</code></pre>
<p>After the command completed, I was able to ping the servers and my desktop.</p>
<!--kg-card-end: markdown-->