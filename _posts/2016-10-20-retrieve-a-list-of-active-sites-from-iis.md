---
layout: post
title: Retrieve a List Of Active Sites From IIS
permalink: /retrieve-a-list-of-active-sites-from-iis/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>I had reason to need a list of all the sites that were running on an IIS server and were &quot;on&quot;. After much Googling, I was able to piece together the simple script below:</p>
<pre><code>Import-Module webadministration
Get-ChildItem IIS:\Sites | where {$_.State -eq 'Started'} | select Name
</code></pre>
<p>This worked so well that I have setup the script to run weekly on our staging servers and email me the results. This allows me to audit the sites and turn off sites that I know we no longer need to have active. It is always best to keep the attack surface as small as possible. :)</p>
<!--kg-card-end: markdown-->