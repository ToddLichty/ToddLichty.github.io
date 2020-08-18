---
layout: post
title: Open edX - Devstack - Viewing logs
permalink: /open-edx-devstack-viewing-logs/
author: Todd Lichty
---
<p>This is a hint for debugging the devstack installation of Open edX. I ran into a problem where I was recieving a "Connection Reset" error whenever I was trying to browse the LMS at <a href="http://localhost:18000/">http://localhost:18000/</a>. By running the following command you can see the logs entries being generated for the container:</p><!--kg-card-begin: markdown--><p><code>make lms-logs</code></p>
<!--kg-card-end: markdown--><p>This can be run for the studio as well:</p><pre><code>make studio-logs</code></pre><figure class="kg-card kg-image-card"><img src="/images/make_lms_logs.png" class="kg-image"></figure>