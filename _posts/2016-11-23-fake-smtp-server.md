---
layout: post
title: Fake SMTP Server
permalink: /fake-smtp-server/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>Almost every web application we develop has functionality to email our client when someone submits a form. It is usually the form on the Contact Us page, but it could also be a notification when a new order is submitted, or someone submits a new FAQ. Either way, part of the development of the component is actually testing the email and reviewing the emails contents. The developer then checks the code into the project with their own email as the recipient.</p>
<p>All is great until I start the security audit of the site and suddenly BAM the original developer of component is <a href="https://en.wikipedia.org/wiki/Email_bomb">email bombed</a> with 400 email submissions when the web application testing tool starts hammering on the contact us form. :)</p>
<p>I did some digging and reading and eventually came across <a href="https://mailtrap.io/">MailTrap</a>. It is super easy to use. They basically give you an SMTP server to use and ANY email sent to that server is trapped and stored in a demo inbox. For Sherpa, this means simply changing the SMTP settings in the app config file to point to MailTrap instead of SMTP.com.:</p>
<pre><code>    &lt;add key=&quot;SMTPCOMServer&quot; value=&quot;mailtrap.io&quot;/&gt;
    &lt;add key=&quot;SMTPCOMPort&quot; value=&quot;2525&quot;/&gt;
    &lt;add key=&quot;SMTPCOMUsername&quot; value=&quot;OBFUSCATED&quot;/&gt;
    &lt;add key=&quot;SMTPCOMPassword&quot; value=&quot;OBFUSCATED&quot;/&gt;
</code></pre>
<p>Mailtrap provides the SMTP server username and password to use. The free plan will show the last 50 emails sent to the SMTP server. For us, this is more than sufficient.</p>
<!--kg-card-end: markdown-->