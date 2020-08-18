---
layout: post
title: An attempt was made to load an assembly from a network location
permalink: /an-attempt-was-made-to-load-an-assembly-from-a-network-location/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>We ran into our first real issue with our new TeamCity build server on Friday afternoon. We ported an old project from Vault into GitHub and then migrated the build script from CruiseControl.Net over to TemaCity. This was the 8th project that I had migrated so I did not expect to have any issues. Once the migration was complete, I hit the Run button in TeamCity to verify that the build would work. A few minutes later, I received the following email:</p>
<pre><code>Compilation errors

SGEN Could not load file or assembly 'file://\\NETWORKPATH\AjaxMin.dll' or one of its dependencies. Operation is not supported. (Exception from HRESULT: 0x80131515)

</code></pre>
<p>Some Googling provided a number of different solutions, the most popular of which was to &quot;unblock&quot; the DLL. None of them seemed to work. I updated the server and rebooted but still no luck. I found this post on <a href="http://stackoverflow.com/questions/3007190/vsts-2010-sgen-error-could-not-load-file-or-assembly-exception-from-hresult">SO</a> and followed the solution provided by Martin Hyldahl:</p>
<blockquote>
<p>To fix your issue just find the location of sgen.exe and create a sgen.exe.config in the same folder with following contents:</p>
</blockquote>
<p><code>&lt;configuration&gt;   &lt;runtime&gt;     &lt;loadFromRemoteSources enabled=&quot;true&quot; /&gt;   &lt;/runtime&gt; &lt;/configuration&gt;</code></p>
<p>Creating this file and adding it to the C:\Program Files (x86)\Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6 Tools directory worked!</p>
<p>Thank God for StackOverflow!</p>
<!--kg-card-end: markdown-->