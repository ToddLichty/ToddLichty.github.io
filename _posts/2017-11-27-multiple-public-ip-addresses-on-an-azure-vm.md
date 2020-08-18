---
layout: post
title: Multiple Public IP Addresses on an Azure VM
permalink: /multiple-public-ip-addresses-on-an-azure-vm/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>I recently was forced to setup a virtual server on Azure to host a few of our old .NET 2.0 sites. The Azure App Service does not support applications written on .NET 2.0 (and understandably so). The sites need to function for 6 months or so until they can be rewritten. Rather than go through the hassle of recompiling the sites in .NET 3.5 (and having to retest everything), I felt it was quicker to just stand up a VM in Azure and run the sites there.</p>
<p>One glitch I found was that I needed two public IP addresses for SSL certificates. I was quickly able to add an additional public IP through the Azure portal but I was hard pressed to find how to assign the new IP to the VM. Some quick Googling and I came across this post:</p>
<p><a href="https://blogs.technet.microsoft.com/canitpro/2017/03/15/step-by-step-setup-multiple-public-ips-on-a-vm-in-azure/">https://blogs.technet.microsoft.com/canitpro/2017/03/15/step-by-step-setup-multiple-public-ips-on-a-vm-in-azure/</a></p>
<p>I followed the steps as outlined, crossed my fingers and it just plain worked.</p>
<!--kg-card-end: markdown-->