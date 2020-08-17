---
layout: post
title: Retrieving DNS Info With PowerShell
permalink: /retrieving-dns-info-with-powershell/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>I had reason to iterate over all the web sites that we host to determine which domains we host the DNS for. I did some Googling and found a PowerShell script that I heavily modified to come up with the following:</p>
<pre><code>$name = &quot;heat-assault.com&quot;

try{
    $dns = Resolve-DnsName -Name $name -Type NS -DnsOnly -ErrorAction Stop

    $IPhash = @{}

    $dnsHostName = ($dns | Where-Object Section -ne Additional | Select-Object -first 1).NameHost

    if ($dnsHostName -like '*canadawebhosting*')
        {
            Write-Host &quot;CWH&quot;
        } else {
            Write &quot;Nope - &quot; $dnsHostName 
        }

} Catch{
    [pscustomobject]@{
        Name = $name
        NameHost = ''
        IP = ''
        Status = $Error[0].Exception.Message
    }
}
</code></pre>
<!--kg-card-end: markdown-->