---
layout: post
title: Blocking an IP in an Azure App Service
permalink: /blocking-an-ip-in-an-azure-app-service/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>Last weekend I received a notification from one of our web properties that it had experienced over 5000 errors in the past hour. I looked at the error log and noticed that the site was being hammered by a single IP address. I wanted to block the IP address until I could understand what was happening.</p>
<p>There is s security setting that can be set in the web.config as shown below:</p>
<pre><code>    &lt;security&gt;
      &lt;ipSecurity allowUnlisted=&quot;true&quot;&gt;
        &lt;clear /&gt;
        &lt;add ipAddress=&quot;38.64.196.3&quot; allowed=&quot;false&quot; /&gt;
      &lt;/ipSecurity&gt;
    &lt;/security&gt;
</code></pre>
<!--kg-card-end: markdown-->