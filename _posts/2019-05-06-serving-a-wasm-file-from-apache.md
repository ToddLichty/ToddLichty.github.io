---
layout: post
title: Serving a WASM file from Apache
permalink: /serving-a-wasm-file-from-apache/
author: Todd Lichty
---
<p>I've been spending a considerable amount of time playing with WebAssembly the last few weeks. It is fascinating what is possible in the browser. One issue that I ran into with my Ubuntu Apache setup was an the following error message:</p><!--kg-card-begin: markdown--><p><code>Failed to execute 'compile' on 'WebAssembly': Incorrect response MIME type. Expected 'application/wasm'.</code></p>
<!--kg-card-end: markdown--><p>This would be displayed in the Chrome console every time I tried to load a WASM file. The issue is that Apache has no clue what a WASM file is. To fix this issue, I had to:</p><!--kg-card-begin: html--><ol>
    <li>Edit the /etc/mime.types file using sudo</li>
    <li>Add the following line to the bottom of the file:<br>
        application/wasm     wasm</li>
    <li>Save the changes and restart Apache</li>
</ol><!--kg-card-end: html--><p>Once Apache had restarted, the error went away.</p>