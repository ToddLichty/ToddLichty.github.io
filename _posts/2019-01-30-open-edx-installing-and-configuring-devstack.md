---
layout: post
title: Open edX - Installing and Configuring Devstack
permalink: /open-edx-installing-and-configuring-devstack/
author: Todd Lichty
---
<p>After a few starts and stops, it appears that I will be starting to work with the <a href="https://open.edx.org/">Open edX</a> platform for my next project. Part of learning a new platform is documenting EVERYTHING. I want to make sure that I always have a copy of my notes, so I've decided to make a number of blog posts relating to the installation of the <a href="https://open.edx.org/">Open edX</a> devstack as well as the process of customizing the default theme.</p><p>Starting with a new installation of Ubuntu 16.04 (I really need to take some time to upgrade my laptop to 18.04), these are the steps I followed to install the devstack version of <a href="https://open.edx.org/">Open edX</a>.</p><!--kg-card-begin: html--><ol>
    <li>Install prerequisites
        <ol>
            <li>make - from the command line, run: sudo apt install make</li>
            <li>docker - I followed the instructions <a href="https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04" target="_blank">here</a>.</li>
            <li>docker-compose - Again, I followed the instructions from <a href="https://www.digitalocean.com/community/tutorials/how-to-install-docker-compose-on-ubuntu-18-04" target="_blank">here</a>.</li>
        </ol>
    </li>
    <li>From a command prompt, run the following code to clone the master branch of the latest repository:
        <code>
            git clone https://github.com/edx/devstack
        </code>
    </li>
    <li>This will create a devstack subdirectory in the current directory. Navigate to the devstack directory and checkout the master branch:
        <code>
            git checkout open-release/hawthorn.master</code></li>
    <li>Next, run the following code:
        <code>make dev.checkout</code></li>
    <li>Run the following command to clone the work service repositories needed for Open edX:<code>make dev.clone</code></li>
    <li>Run the provision command to configure each of the services and configure the databases. This step takes a bit of time to complete.<code>make dev.provision</code></li>
</ol>
<!--kg-card-end: html--><p>These steps required approximately 25 minutes to complete on my system. Once they were finished, running the following command from the devstack directory will launch the various Docker containers and bring up Open edX on your local computer.</p><!--kg-card-begin: html--><code>make dev.up</code><!--kg-card-end: html--><figure class="kg-card kg-image-card"><img src="/images/openedx_make_dev_up.png" class="kg-image"></figure><!--kg-card-begin: html-->Once the containers have started and are running, you can access the LMS at: <a href="http://localhost:18000/">http://localhost:18000/</a>. The studio can be accessed at: <a href="http://localhost:18000/">http://localhost:18010/</a>.

More detailed instructions can be found at the Open edX documentation site <a href="https://edx.readthedocs.io/projects/edx-installing-configuring-and-running/en/latest/installation/index.html">here</a>.<!--kg-card-end: html-->