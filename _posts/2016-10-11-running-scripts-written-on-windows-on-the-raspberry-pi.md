---
layout: post
title: Running scripts written on Windows on the Raspberry Pi
permalink: /running-scripts-written-on-windows-on-the-raspberry-pi/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>I spent some time this weekend writing a Python script to check the SSL expiration dates for all our sites. We've been caught flat footed too many times having to run around and renew certificates that have expired. I figured this was something that should be automated. I'll post the script in a future post.</p>
<p>I wrote the script on my Kali VM, tested it and wanted to deploy it to one of the Raspberry Pis. I was unable to get SSH working from the VM to the Pi, so I copied the script from the VM, pasted it into sublime on my Windows machine and then FTP'd the file to the Pi. When I ran the script, I was presented with the following error:</p>
<p><code>-bash: ./my_script: /bin/bash^M: bad interpreter: No such file or directory </code></p>
<p>I recall running into this error before. Some quick Googling found this fix on stackoverflow:</p>
<p><a href="http://stackoverflow.com/questions/14219092/bash-my-script-bin-bashm-bad-interpreter-no-such-file-or-directory">http://stackoverflow.com/questions/14219092/bash-my-script-bin-bashm-bad-interpreter-no-such-file-or-directory</a></p>
<p>I wound up switching the line endings in sublime using the View--&gt;Line Endings menu item.</p>
<!--kg-card-end: markdown-->