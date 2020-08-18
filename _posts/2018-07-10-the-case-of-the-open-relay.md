---
layout: post
title: The Case of the Open Relay
permalink: /the-case-of-the-open-relay/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>I love my job. I love solving problems. In IT, the issue can be just about anything. Bad code, server malfunction, firewall issue, authentication issue etc.</p>
<p>Below is an issue I ran into last year. It is a warning to others that are responsible for older websites. Make sure you disable pages and functionality that are no longer in use!</p>
<p>I received a warning from our monitoring system that explained that the C drive on the webserver was full. This came as a shock since the warning should have been triggered when the drive was at 15%.</p>
<p>Shortly after, I received the following email from the client stating that the web site was not working. The error message that they sent indicated an out of memory error, which I thought was odd:<br>
<img src="/images/open_relay_error_message.jpg" alt=""></p>
<p>Once I did some digging, I found these SMTP log files:<br>
<img src="/images/open_relay_smtp_log_directory.JPG" alt=""></p>
<p>A quick look at one of the log files and I found:</p>
<pre><code>2017-02-09 05:28:28 66.196.118.34 OutboundConnectionCommand SMTPSVC1 VSERVER14541 - 25 MAIL - FROM:&lt;MillionairesBlueprint@earthlink.com&gt;+SIZE=1722 0 0 4 0 0 SMTP - - - -
2017-02-09 05:28:28 66.196.118.34 OutboundConnectionResponse SMTPSVC1 VSERVER14541 - 25 - - 421+4.7.0+[TSS04]+Messages+from+192.223.13.201+temporarily+deferred+due+to+user+complaints+-+4.16.55.1;+see+https://help.yahoo.com/kb/postmaster/SLN3434.html 0 0 157 0 16 SMTP - - - -
</code></pre>
<p>I had no clue how someone from earthlink.com was using the internal SMTP server on the webserver to send their spam emails. I checked the firewall rules to verify that the SMTP server was not accessible from the public internet. I also verified this using a telnet on a server outside our network. I was baffled as to how this third party was using our SMTP server as a relay.</p>
<p>I looked into the badmail folder on the server hoping to find a sample of the emailes that they were sending. I was lucky that there were over 1000 emails in the folder. I opened one of the messages and took a look:</p>
<pre><code>Received: from SERVERNAME ([127.0.0.1]) by SERVERNAME with Microsoft SMTPSVC(8.0.9200.16384);
	 Fri, 3 Feb 2017 01:30:51 -0500
thread-index: AdJ95xC3WthkIFbPRrOnrv7P2lwRYQ==
Thread-Topic: A recommendation from Earn Up to $237 per hour Starting Today
From: &lt;XXXX@ymail.com&gt;
To: &lt;XXXX@ymail.com&gt;
Subject: A recommendation from Earn Up to $237 per hour Starting Today
Date: Fri, 3 Feb 2017 01:30:51 -0500
Message-ID: &lt;100BF803A65E45A2996F95459FD64A6A@internal.canadawebhosting.com&gt;
MIME-Version: 1.0
Content-Type: text/plain;
	charset=&quot;iso-8859-1&quot;
Content-Transfer-Encoding: 7bit
X-Mailer: Microsoft CDO for Windows 2000
Content-Class: urn:content-classes:message
Importance: normal
Priority: normal
X-MimeOLE: Produced By Microsoft MimeOLE V6.2.9200.21989
Return-Path: XXXX@ymail.com
X-OriginalArrivalTime: 03 Feb 2017 06:30:51.0872 (UTC) FILETIME=[10BA2E00:01D27DE7]

Dear http://tiny.cc/LINKHERE,

Earn Up to $237 per hour Starting Today 

Earn Up to $237 per hour Starting Today also sent you this message:

&quot;Instant access here: 
&gt;&gt; http://tiny.cc/LINKHERE

Thank me later, 

 Michael J
                  &quot;
</code></pre>
<p>The details indicated that the email did originate on our server. After reviewing the email again, I figured out how they were sending their emails from our server. The X-Mailer value tipped me off that this was being sent from the website somewhere. A quick GREP of the source control for the value &quot;A recommendation from&quot; quickly lead me to the culprit:<br>
<img src="/images/open_relay_form.JPG" alt=""></p>
<p>The source control history of this form shows that it was created 9!! years ago and has not been used in over 6 years. Obviously, this form would have been secured differently if it was built recently.</p>
<p>This is a case where old functionality should have been disabled or deleted rather than forgotten about.</p>
<!--kg-card-end: markdown-->