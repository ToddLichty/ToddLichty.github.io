---
layout: post
title: Deploying to Azure WebApp From An Organizations GitHub Account
permalink: /deploying-to-azure-webapp-from-an-organizations-github-account/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>I've spent a good part of the last two days working on our deployment methodology. We have started the slow migration of our sites from our current hosting provider to Azure. To date I have been using the FTPS deployment. I wanted to experiment deploying from GitHub.</p>
<p>I setup the deployment option in the Azure portal, but when I went to select the project to deploy, I was greeted with the error message &quot;No Results&quot;.</p>
<p>After some Googling, I found this blog post which walked me through granting Azure access to the organization's account:</p>
<p><a href="https://azure.microsoft.com/en-us/blog/using-app-service-web-apps-continuous-deployment-with-github-organizations/">https://azure.microsoft.com/en-us/blog/using-app-service-web-apps-continuous-deployment-with-github-organizations/</a></p>
<!--kg-card-end: markdown-->