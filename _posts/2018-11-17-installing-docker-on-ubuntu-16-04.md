---
layout: post
title: Installing Docker on Ubuntu 16.04
permalink: /installing-docker-on-ubuntu-16-04/
author: Todd Lichty
---
<p>I've had reason to start playing with containers on Ubuntu. The first step was to get docker installed and working on my laptop.</p><ol><li>I needed to add the GPG key for Docker to my system.</li></ol><pre><code>curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -</code></pre><p>2. Next I needed to add the Docker repository to APT and refresh the package database.</p><pre><code>sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

sudo apt-get update</code></pre><p>3. Finally, install Docker:</p><pre><code>sudo apt-get install -y docker-ce</code></pre><p>After about 30 seconds the install was completed. I verified that everything installed correctly and was active by running the command:</p><pre><code>sudo systemctl status docker</code></pre><p>Docker needs to run with elevated privileges. Rather than typing <em>sudo</em> before each command, I added my user account to the <em>docker</em> user group:</p><pre><code>sudo usermod -aG docker ${USER}
su - ${USER}</code></pre><p>Running the following command will verify that it worked correctly:</p><pre><code>id -nG

todd adm sudo lpadmin sambashare docker</code></pre><p>Pretty straightforward to install a piece of software as powerful as Docker. So far, I'm loving the change to Linux.</p>