---
layout: post
title: Installing an SSL Certificate on Tableau Server
permalink: /installing-an-ssl-certificate-on-tableau-server/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>Every time that the SSL certificate on our Tableau server is up for renewal, I need to remember how to install the certificate. These are my notes for 2020 when the current certificate expires. :)</p>
<p>After obtaining the SSL certificate, export it from IIS into a PFX file (this is the default format).</p>
<p>Next, open a command prompt and type:</p>
<pre><code>openssl pkcs12 -in [yourfile.pfx] -nocerts -out [keyfile-encrypted.key]
</code></pre>
<p>This will export the .key file. Next type:</p>
<pre><code>openssl pkcs12 -in [yourfile.pfx] -clcerts -nokeys -out [certificate.crt]
</code></pre>
<p>Which will export the crt file.</p>
<p>Upload these files to the Tableau server into the c:\program files\tableau\tableau server\ssl directory.</p>
<p>Stop Tableau and then open the Configure Tableau app.</p>
<p>Select the SSL tab.</p>
<p>Select the new crt and key files.</p>
<p>Start Tableau service.</p>
<!--kg-card-end: markdown-->