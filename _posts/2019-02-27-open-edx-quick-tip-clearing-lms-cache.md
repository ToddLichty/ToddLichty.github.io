---
layout: post
title: Open edX - Quick Tip - Clearing LMS Cache
permalink: /open-edx-quick-tip-clearing-lms-cache/
author: Todd Lichty
---
<p>A quick tip that I discovered when working with the LMS on devstack. I would make changes in the Studio but they would take forever to show on the LMS. Restarting the memcached container did the trick:</p><pre><code>docker restart edx.devstack.memcached</code></pre><p>You will need to sign back into the LMS, but the content will be refreshed.</p>