---
layout: post
title: HMAVPN and Windows 10 TAP Driver Error
permalink: /hmavpn-and-windows-10-tap-driver-error/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>I recently repaved my Surface Pro 3. As with all Windows systems, it started to display symptoms of &quot;Windows Rot&quot;. I purchased the system new and applied all the OS updates (Windows 8.1, Windows 10, Windows 10 Anniversary Update) to it without reformatting it. The system held up remarkably well considering it went through three major OS updates.</p>
<p>During the past three weeks, I started noticing that the battery was draining very rapidly, apps would just randomly crash and the system was just plain sluggish. It was time to repave. I used the Windows 10 System Restore and opted to keep nothing. All my documents, images etc. are in OneDrive so there really was nothing that I needed to backup.</p>
<p>It took about 30 minutes from starting the restore to booting to a fully patched system. Then came the inevitable install of all the programs. I started with Office, then VS Code and the required VPN settings for Sherpa Marketing.</p>
<p>After installing Visual Studio 2015 and GitHub, it was time to leave for the <a href="http://conferences.oreilly.com/security/network-data-security-ny">O'Reilly Security Conference</a>.</p>
<p>On the first day of the conference, I arrived at my training course early, fired up my Surface Pro and connected to the conference WiFi. I then went to connect to my VPN provider HMA and realized I forgot to install it.</p>
<p>I quickly downloaded the Windows install for HMA, went through the setup and was presented with a security alert stating that Windows could not install the TAP driver since it was unsigned.</p>
<p>I knew this was not a good sign.</p>
<p>I tried connecting to HMA anyway, but was not able to. After some Googling, it was apparent that this was a known issue and HMA did post instructions on how to work around this problem, but they looked a  bit sketchy to me.</p>
<p>Since I have been dabbling more and more in the Linux / OS world, I decided to give <a href="https://openvpn.net">OpenVPN</a> a whirl on Windows. I download the installer, then downloaded the config files from <a href="http://hidemyass.com/vpn-config/vpn-configs.zip">HMA</a>, found the file I needed and was able to quickly connect.</p>
<p>I'm now able to use the conference WiFi with some semblance of confidence that the connection is private and secured. :)</p>
<!--kg-card-end: markdown-->