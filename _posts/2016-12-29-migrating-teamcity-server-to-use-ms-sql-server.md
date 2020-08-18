---
layout: post
title: Migrating TeamCity Server to Use MS SQL Server
permalink: /migrating-teamcity-server-to-use-ms-sql-server/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>After testing TeamCity for the past several months, it was obvious that this was a GREAT upgrade from our current CruiseControl.NET build solution. It's been rock solid and, other than some missing DLLS, I have not had to RDP into the server to correct any issues.</p>
<p>I was performing some maintenance on the servers when I noticed that an update to TeamCity was available. I had full intentions of installing the update. I was looking up the TeamCity data directory location on the setting page, when I noticed a warning that reminded me I was using the build in database for TeamCity. I should have remembered to upgrade this to something a little more substantial.</p>
<p>I took the opportunity to backup the TeamCity VM (just in case) and followed the instructions here:</p>
<p><a href="https://confluence.jetbrains.com/display/TCD10//Migrating+to+an+External+Database">https://confluence.jetbrains.com/display/TCD10//Migrating+to+an+External+Database</a></p>
<p>I performed the full migration and used the MS SQL Server steps for creating the empty database, installing the proper JDBC drivers and ultimately migrating from the build in database over to SQL Server.</p>
<p>There were no hiccups, everything just worked. The entire process took me less than 15 minutes. Great work!</p>
<!--kg-card-end: markdown-->