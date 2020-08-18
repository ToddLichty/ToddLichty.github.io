---
layout: post
title: IIS log files and LogParser 2.2
permalink: /iis-log-files-and-logparser-2-2/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>I had to deal with a serious client issue the past 24 hours that required me to be able to parse through IIS logs. I had played with Microsoft's LogParser in the past but it had been a while.</p>
<p>To quickly import the files into a SQL database, it was quite easy to do:</p>
<pre><code>logparser &quot;SELECT * INTO iisLogs FROM f:\temp\logs\*.log &quot; -i:iisw3c -o:SQL -server:10.0.0.X -database:SiteMonitor -username:USERNAME -password:PASSWORD -createTable: ON
</code></pre>
<p>This quickly had the logs imported to a database that I could easily query as needed.</p>
<!--kg-card-end: markdown-->