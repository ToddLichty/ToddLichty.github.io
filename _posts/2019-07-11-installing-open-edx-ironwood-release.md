---
layout: post
title: Installing Open edX Ironwood Release
permalink: /installing-open-edx-ironwood-release/
author: Todd Lichty
---
<p>I've spent the last couple of days struggling to install the Ironwood release of Open edX in an Ubuntu 16.04 Virtualbox. After struggling with various issues, I came across this post in the General Open edX Google Group:</p><p><a href="https://groups.google.com/forum/?utm_medium=email&amp;utm_source=footer#!msg/edx-code/cgMseEEKGAg/wgvld6EkAwAJ">https://groups.google.com/forum/?utm_medium=email&amp;utm_source=footer#!msg/edx-code/cgMseEEKGAg/wgvld6EkAwAJ</a></p><p>The following instructions worked for me to finally install a stable copy of the platform:</p><!--kg-card-begin: markdown--><pre><code>sudo apt-get update -y
sudo apt-get upgrade -y
sudo reboot
sudo su 
export OPENEDX_RELEASE=open-release/ironwood.master
</code></pre>
<!--kg-card-end: markdown--><p>I then created the config.yml file in the current directory:</p><!--kg-card-begin: markdown--><pre><code># The host names of LMS and Studio. Don't include the &quot;https://&quot; part:

EDXAPP_LMS_BASE: &quot;example.com&quot;
EDXAPP_CMS_BASE: &quot;studio.example.com&quot;
</code></pre>
<!--kg-card-end: markdown--><!--kg-card-begin: markdown--><pre><code>wget https://raw.githubusercontent.com/edx/configuration/$OPENEDX_RELEASE/util/install/ansible-bootstrap.sh -O - | sudo bash
wget https://raw.githubusercontent.com/edx/configuration/$OPENEDX_RELEASE/util/install/generate-passwords.sh -O - | bash
wget https://raw.githubusercontent.com/edx/configuration/$OPENEDX_RELEASE/util/install/native.sh -O - | bash
</code></pre>
<!--kg-card-end: markdown--><p>The install took almost an hour on a small Virtualbox but it did complete. The step that I believe made all the difference was running as a superuser:</p><pre><code class="language-bash">sudo su</code></pre>