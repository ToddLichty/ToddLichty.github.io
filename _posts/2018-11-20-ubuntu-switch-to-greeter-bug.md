---
layout: post
title: Ubuntu - Switch to greeter bug
permalink: /ubuntu-switch-to-greeter-bug/
author: Todd Lichty
---
<p>After installing VirtualBox on my laptop, I locked my computer and went to lunch. When I returned and woke my laptop, I was greeted by an "Authentication failed" error and a button that read "Switch to greeter". Clicking the button allowed me to login as normal. I thought this odd, but did not think anything of it.</p><p>However, the same thing happened when returned from a meeting and found the laptop locked. It happened a third time after a trip to the coffee machine. I knew it was time to dig into it and figure out what went wrong.</p><p>Some quick Googling did not find a lot of fixes. I did, however, come across <a href="https://medium.com/@5XvYrLT7/fix-ubuntus-switch-to-greeter-bug-715d05520f46">this post on Medium</a> which did fix the issue.</p><p>From the terminal, I ran the following commands:</p><pre><code>$ sudo apt install --reinstall lightdm
$ sudo service lightdm restart
</code></pre><p><strong>NOTE</strong>: Your application will close after running the second command. Make sure they are closed before running it!</p>