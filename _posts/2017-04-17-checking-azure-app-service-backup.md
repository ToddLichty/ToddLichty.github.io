---
layout: post
title: Checking Azure App Service Backup
permalink: /checking-azure-app-service-backup/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>While we are in the process of automating our Azure deployments, one item that keeps me awake at nights is backups. What if someone deploys an app to Azure but completely forgets to setup and automated backup?</p>
<p>I had some time last night to (finally) address this problem and came up with the following code:</p>
<pre><code>Login-AzureRmAccount

$sites = Get-AzureRmResource | Where-Object {$_.ResourceType -eq &quot;Microsoft.Web/sites&quot;}

foreach ($site in $sites)
{
    $backup = Get-AzureRmWebAppBackupConfiguration -Name $site.Name -ResourceGroupName $site.ResourceGroupName

    if (-Not $backup.Enabled) {
        Write-Host &quot;NOT ENABLED FOR &quot; $site.Name
    }
}
</code></pre>
<p>At the moment, there is still a login prompt where I have to manually authenticate with my Azure subscription info. I'll be working on automating this in the future.</p>
<!--kg-card-end: markdown-->