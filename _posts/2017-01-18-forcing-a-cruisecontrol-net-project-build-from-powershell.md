---
layout: post
title: Forcing a CruiseControl.net project build from PowerShell
permalink: /forcing-a-cruisecontrol-net-project-build-from-powershell/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>While we are in the process of migrating to TeamCity for our CI server, we're (sadly) still using <a href="http://www.cruisecontrolnet.org/">CruiseControl.NET</a> for some of our older automated continuous integrations. I have a project that I <strong>don't</strong> want to have build every time CCNET detects a check in. It's not ideal but this is a special case.</p>
<p>I quickly became bored/frustrated etc. having to open a browser and force a build every time I wanted a new build to kick off. I thought this would be a perfect job to automate using PowerShell.</p>
<p>Below is the script I use to kick off a build of my project. I've made it a bit more generic than the one I use at the office. :)</p>
<pre><code>cls
$projectName = &quot;Test Project&quot;

# Return the project node from the XML 
function GetProject() {
	$doc = New-Object System.Xml.XmlDocument
	$doc.Load(&quot;http://ccnetURL/XmlStatusReport.aspx&quot;)
	$doc.Projects.Project | Where-Object {$_.name -eq $projectName}
}

#Return the value of the activity element of the project
function GetActivity() {
	$project = GetProject
	$project.activity	
}

#Return the lastBuildStatus element of the project
function GetLastBuildStatus() {
	$project = GetProject
	$project.lastBuildStatus
}

#Update this to be the URL to the ViewProjectReport page of the project you are viewing
$result = Invoke-WebRequest &quot;http://SERVER_NAME/server/local/project/$projectName/ViewProjectReport.aspx?ForceBuild=Force&quot; -Method Get

if ($result.StatusCode -eq 200) {
	
	Write-Host &quot;Build started&quot; -foregroundcolor green
	Start-Sleep -s 10
	$i = 0

	while($i -ne 20) {
		$i++
		$activity = GetActivity
		Write-Host &quot;Activity: $activity&quot; 
		
		if ($activity -eq 'Sleeping') {
			Write-Host &quot;Build done&quot; -foregroundcolor green
			break
		}

		Start-Sleep -s 10
	}

	$status = GetLastBuildStatus

	if ($status -eq &quot;Success&quot;) {
		Write-Host &quot;Build status: $status&quot; -foregroundcolor green
	} else {
		Write-Host &quot;Build status: $status&quot; -foregroundcolor red
	}

} else {
	Write-Host &quot;NOPE!&quot; -foregroundcolor red
}

</code></pre>
<p>It's been working great and has saved my sanity. Always automate something that you have to do more than twice.</p>
<!--kg-card-end: markdown-->