---
layout: post
title: The Wait Operation Timed Out
permalink: /the-wait-operation-timed-out/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>We've been experiencing this SQL error with one of our sites lately. When I ran the offending stored procedure in SSMS, it ran in under a second. Running the page with this stored procedure would hang for 30 seconds and then time out.</p>
<p>The quick fix is to run the following:</p>
<pre><code> DBCC DROPCLEANBUFFERS
 DBCC FREEPROCCACHE
</code></pre>
<p>This is just a temporary fix. I need to dig into the real issues behind these errors.</p>
<!--kg-card-end: markdown-->