---
layout: post
title: Learning Docker
permalink: /learning-docker/
author: Todd Lichty
---
<p>I'm spending a lot of time learning new and exciting development technologies at my new job. Spending time in open source development has given me a chance to really understand and experiment with technology that I did not have time to previously.</p><p>This past week I spent some time learning <a href="https://www.docker.com/">docker</a> and containers in general. I had ample experience configuring and using virtual machines previously. Containers were something new and foreign.</p><p>I started with some general reading on the docker.com website. I then used the free <a href="http://www.lynda.com">lynda.com</a> account that my employer provides to dig into some docker 101 courses:</p><p><a href="https://www.lynda.com/Docker-tutorials/Learning-Docker-REVISION-Q3-2018/721901-2.html">https://www.lynda.com/Docker-tutorials/Learning-Docker-REVISION-Q3-2018/721901-2.html</a></p><p>The notes I took from this course are below. I hope to continue to update them as my experience in docker increases.</p><!--kg-card-begin: markdown--><p><code>docker ps</code> - show running images</p>
<p><code>docker run -ti ubuntu:latest bash</code> - run container with terminal interface enabled</p>
<p><code>docker ps -a</code> show ALL containers</p>
<p><code>docker ps -l</code> - show last container that was run</p>
<p><code>docker commit IMAGE_NAME CONTAINER_NAME</code> - save changes made to the container and image</p>
<p>i.e. <code>docker commit saucy_nancy my-image-2</code></p>
<p><code>docker -rm CONTAINER_NAME</code> - remove a container</p>
<p><code>Docker network create NETWORK_NAME</code> - creates a new network for docker containers</p>
<p><code>docker run -rm -ti --net=NETWORK_NAME --name=server ubuntu:14.04 bash</code></p>
<p><code>docker rmi IMAGE_NAME</code> - removes a docker image</p>
<!--kg-card-end: markdown-->