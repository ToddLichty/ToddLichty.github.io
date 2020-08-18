---
layout: post
title: The Times They Are A Changin'
permalink: /the-times-they-are-a-changin/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>After listening to episode 1379 of <a href="http://www.dotnetrocks.com/?show=1379">DOTNETROCKS</a> titled &quot;SQL Choices with Tony Petrossian&quot;, I was gobsmacked to hear that Microsoft has delivered a public preview of MS SQL Server 2016 that runs on Linux. I had heard the hype but assumed that it was going to be a few years before it was a viable option.</p>
<p>When Tony said that MSSQL on Linux has feature parity with MSSQL on Windows, I was in shock. I assumed it would take years of development to get the Linux version even close to where the Windows version is.</p>
<p>I had to play around with this. I followed the instructions on the Microsoft site: <a href="https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-setup-ubuntu">Install SQL Server on Ubuntu</a> and within 10 minutes I had a SQL Server running on my System 76 Ubuntu machine.</p>
<p>I was able to connect to the Linux SQL instance from my Windows desktop using Management Studio without any issues:</p>
<p><img src="/images/SQL-Linux.PNG" alt=""></p>
<p>I'm still in shock. I never assumed that I would see SQL Server running on Linux. Ever.</p>
<p>I still need to play with backups, restores and run some real performance tests on this, but so far so good!</p>
<!--kg-card-end: markdown-->