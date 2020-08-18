---
layout: post
title: Managing Logfiles with Logrotate
permalink: /managing-logfiles-with-logrotate/
author: Todd Lichty
---
<p>Log files provide an important glimpse into what actions users are performing in your application. While the web application I am currently developing generates very detailed log files, there is no easy way to manage them. They continue to grow infinitely. </p><p>Ubuntu 18.04 has a marvelous tool built in called <a href="https://linuxconfig.org/logrotate-8-manual-page">logrotate</a>. This utility will run daily and perform log rotation based on configuration files that you create. These configuration files are located in /etc/logrotate.d. Each file is used to add additional settings or override the default settings for specific folders that you specify. The folder also contains the logrotate configuration of any packages you install that need log rotation.</p><p>Below is an example of a logrotate file that I used for a web application.</p><!--kg-card-begin: markdown--><pre><code>/app1/logs/*.log
/app2/logs/*.log 
{
       # Rotate once every day
        daily
        # Keep a history of 15 rotations
        rotate 15
        # Rotate even if the log file is empty
        ifempty
        # Skip this block without error if no files match the pattern
        missingok
        # Copy and truncate the original log file
        copytruncate
        # Change the file extension to use the date
        dateext
}
</code></pre>
<!--kg-card-end: markdown--><p>The file above is pretty straightforward. The comments indicate what each line does.</p>