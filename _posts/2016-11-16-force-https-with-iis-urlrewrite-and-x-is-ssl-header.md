---
layout: post
title: Force HTTPS with IIS URLRewrite and X-Is-SSL Header
permalink: /force-https-with-iis-urlrewrite-and-x-is-ssl-header/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>Recently we had reason to force all page connections to use SSL for one of our clients. We have done this in the past with code, but I wanted to see if this was possible to do with the URL Rewrite module. We utilize an SSL load balancer so all the examples online did not work for us. I was able to tinker with the rule until I found one that worked. Below is the code from the web.config file that causes all non-HTTPS traffic on a site to be routed to HTTPS.</p>
<pre><code>    &lt;rewrite&gt;
        &lt;rules&gt;
          &lt;rule name=&quot;Force Https&quot; stopProcessing=&quot;true&quot;&gt;
            &lt;conditions&gt;
                &lt;add input=&quot;{HTTP_X_IS_SSL}&quot; pattern=&quot;Yes&quot; negate=&quot;true&quot; /&gt;
            &lt;/conditions&gt;
            &lt;action type=&quot;Redirect&quot; url=&quot;https://{HTTP_HOST}{REQUEST_URI}&quot; redirectType=&quot;Permanent&quot; /&gt;
          &lt;/rule&gt;
        &lt;/rules&gt;
    &lt;/rewrite&gt;
</code></pre>
<p>We check the X-Is-SSL header that is added by the F5 load balancer and redirect as needed. So far, so good.</p>
<!--kg-card-end: markdown-->