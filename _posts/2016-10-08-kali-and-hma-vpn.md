---
layout: post
title: Kali and HMA VPN
permalink: /kali-and-hma-vpn/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p><img src="/images/kali_desktop.PNG" alt=""><br><br>
I recently downloaded an updated version of the <a href="https://www.offensive-security.com/kali-linux-vmware-virtualbox-image-download/">Kali 2016.2 VMWare</a>. One of the first items I installed on the VM (after running the OS updates), is the <a href="https://www.offensive-security.com/kali-linux-vmware-virtualbox-image-download/">HMA VPN script</a></p>
<p>After downloading the ZIP file, I extracted the hma-openvpn.sh file, marked it as executable, and I was ready to go.</p>
<p>For the record, I HATE having to use the new Dialog script. I would much sooner use the old script rather than jump through a bunch of dialogs.</p>
<p><strong>UPDATE</strong>: After looking through the hma-openvpn.sh script, I was able to figure out what it was running. I downloaded the appropriate ovpn file from <a href="https://www.hidemyass.com/vpn-config/TCP/">https://www.hidemyass.com/vpn-config/TCP/</a> and then run the following script:</p>
<p><code>openvpn --script-security 3 --config SCRIPT_TCP.ovpn </code></p>
<p>Sweet!</p>
<!--kg-card-end: markdown-->