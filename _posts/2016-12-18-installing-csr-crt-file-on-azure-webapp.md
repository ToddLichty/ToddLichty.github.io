---
layout: post
title: Installing CSR/CRT File on Azure WebApp
permalink: /installing-csr-crt-file-on-azure-webapp/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>Part of migrating our hosting from our current environment over to Azure involved migrating the SSL certificates. To save money, the clients generally do not want to pay for new certificates, they would rather use the existing ones. Our current host exports the SSL certificates as CSR files and provides a separate private key file. Unfortunately, Azure requires you to upload a PFX password protected file.</p>
<p>To convert the supplied CSR file to a PFX, I followed the steps in this blog post: <a href="http://stackoverflow.com/questions/6307886/how-to-create-pfx-file-from-certificate-and-private-key">http://stackoverflow.com/questions/6307886/how-to-create-pfx-file-from-certificate-and-private-key</a></p>
<p>Basically, I ran the command:</p>
<pre><code>openssl pkcs12 -export -out domainname.pfx -inkey privatekey.txt -in supplied.csr
</code></pre>
<p>NOTE: Make sure to run the command as an Administrator!</p>
<!--kg-card-end: markdown-->