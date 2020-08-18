---
layout: post
title: Checking the Status of an Azure WebJob
permalink: /checking-the-status-of-an-azure-webjob/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>As we migrate more and more of our infrastructure to Azure, we've begun to make use of WebJobs. Now that we have started to reply more and more on WebJobs rather than Windows Services, I wanted to add a status check to our dashboard to make sure that the WebJob was run successfully.</p>
<p>After some digging, it was actually quite easy:</p>
<pre><code>Dim Url As [String] = &quot;https://APPSERVICENAME.scm.azurewebsites.net/api/triggeredwebjobs/JOBNAME&quot;
Dim request As WebRequest = WebRequest.Create(Url)

request.ContentType = &quot;application/json&quot;
request.Method = &quot;GET&quot;

Dim userName As [String] = &quot;$username&quot;
Dim passWord As [String] = &quot;password&quot;
Dim credentials As String = Convert.ToBase64String(Encoding.ASCII.GetBytes(userName + &quot;:&quot; + passWord))
request.Headers(HttpRequestHeader.Authorization) = String.Format(&quot;Basic {0}&quot;, credentials)
request.ContentType = &quot;application/json; charset=utf-8&quot;

Dim response As HttpWebResponse = request.GetResponse()

Using sr = New StreamReader(response.GetResponseStream())

    Dim data = sr.ReadToEnd()
    'This will be a JSON string
End Using
</code></pre>
<p>The hardest part of this was figuring out what credentials to use. In the Azure Portal, if you go to the properties of your WebJob, the username and password can be seen:</p>
<p><img src="/images/webjob.jpg" alt=""></p>
<!--kg-card-end: markdown-->