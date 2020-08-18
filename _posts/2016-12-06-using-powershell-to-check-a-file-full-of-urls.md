---
layout: post
title: Using PowerShell to Check a File Full of URLs
permalink: /using-powershell-to-check-a-file-full-of-urls/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>I had to write a quick and dirty script to read URLs out of a file and test to make sure they were working correctly. Seemed like a pretty straightforward and simple problem. Here is the script version that I started with:</p>
<pre><code>function TestSite($url) {

    $HTTP_Status = (invoke-webrequest  -method head -uri $url).statuscode

    If ($HTTP_Status -eq 200) { 
        Write-Host &quot;Site is OK!&quot; 
    }
    Else {
        Write-Host &quot;The Site may be down, please check!&quot;
    }

}

$lines = Get-Content f:\temp\url_test.txt

foreach ($line in $lines){
    Write-Host $line
    TestSite $line
}

</code></pre>
<p>Each time I tested a URL, I received the following error:<br>
<code>invoke-webrequest : The server committed a protocol violation. Section=ResponseHeader Detail=CR must be followed by LF</code></p>
<p>After much more Googling than I would have thought necessary, I came across this StackOverflow post:<br>
<a href="http://stackoverflow.com/questions/35260354/powershell-wget-protocol-violation">http://stackoverflow.com/questions/35260354/powershell-wget-protocol-violation</a></p>
<p>Which had a great function already written:</p>
<pre><code>function Set-UseUnsafeHeaderParsing
{
    param(
        [Parameter(Mandatory,ParameterSetName='Enable')]
        [switch]$Enable,

        [Parameter(Mandatory,ParameterSetName='Disable')]
        [switch]$Disable
    )

    $ShouldEnable = $PSCmdlet.ParameterSetName -eq 'Enable'

    $netAssembly = [Reflection.Assembly]::GetAssembly([System.Net.Configuration.SettingsSection])

    if($netAssembly)
    {
        $bindingFlags = [Reflection.BindingFlags] 'Static,GetProperty,NonPublic'
        $settingsType = $netAssembly.GetType('System.Net.Configuration.SettingsSectionInternal')

        $instance = $settingsType.InvokeMember('Section', $bindingFlags, $null, $null, @())

        if($instance)
        {
            $bindingFlags = 'NonPublic','Instance'
            $useUnsafeHeaderParsingField = $settingsType.GetField('useUnsafeHeaderParsing', $bindingFlags)

            if($useUnsafeHeaderParsingField)
            {
              $useUnsafeHeaderParsingField.SetValue($instance, $ShouldEnable)
            }
        }
    }
}
</code></pre>
<p>Enabling the UseUnsafeHeaderParsing at the start of the script worked. Here is the final script I used:</p>
<pre><code>function Set-UseUnsafeHeaderParsing
{
    param(
        [Parameter(Mandatory,ParameterSetName='Enable')]
        [switch]$Enable,

        [Parameter(Mandatory,ParameterSetName='Disable')]
        [switch]$Disable
    )

    $ShouldEnable = $PSCmdlet.ParameterSetName -eq 'Enable'

    $netAssembly = [Reflection.Assembly]::GetAssembly([System.Net.Configuration.SettingsSection])

    if($netAssembly)
    {
        $bindingFlags = [Reflection.BindingFlags] 'Static,GetProperty,NonPublic'
        $settingsType = $netAssembly.GetType('System.Net.Configuration.SettingsSectionInternal')

        $instance = $settingsType.InvokeMember('Section', $bindingFlags, $null, $null, @())

        if($instance)
        {
            $bindingFlags = 'NonPublic','Instance'
            $useUnsafeHeaderParsingField = $settingsType.GetField('useUnsafeHeaderParsing', $bindingFlags)

            if($useUnsafeHeaderParsingField)
            {
              $useUnsafeHeaderParsingField.SetValue($instance, $ShouldEnable)
            }
        }
    }
}

function TestSite($url) {

    $HTTP_Status = (invoke-webrequest  -method head -uri $url).statuscode

    If ($HTTP_Status -eq 200) { 
        Write-Host &quot;Site is OK!&quot; 
    }
    Else {
        Write-Host &quot;The Site may be down, please check!&quot;
    }

}

Set-UseUnsafeHeaderParsing -Enable
$lines = Get-Content f:\temp\url_test.txt

foreach ($line in $lines){
    Write-Host $line
    TestSite $line
}

</code></pre>
<!--kg-card-end: markdown-->