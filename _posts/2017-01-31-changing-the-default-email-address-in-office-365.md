---
layout: post
title: Changing the default email address in Office 365
permalink: /changing-the-default-email-address-in-office-365/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>We ran into a problem last week where account managers noticed that the reply-to address on the emails that they were sending was defaulting to onmicrosoft.com. I assumed that this would be an easy fix, so I logged into the Office 365 admin and tried to change the default email address to the @sherpamarketing.ca email. I was presented with the following error message:</p>
<p><img src="/images/outlook-error.PNG" alt=""></p>
<p>After trying many different changes, I stumbled upon a post that walked me throught the following steps:</p>
<ol>
<li>
<p>Run as ADSIEDIT.msc as an Administrator</p>
</li>
<li>
<p>Add entries to the mail and proxyAddress values:</p>
</li>
</ol>
<p><img src="/images/proxyAddress.jpg" alt=""></p>
<p><img src="/images/mail.jpg" alt=""></p>
<ol start="3">
<li>Force a sync.</li>
</ol>
<p>This seems to have corrected the problem for us.</p>
<!--kg-card-end: markdown-->