---
layout: post
title: Pushover and MotionPie
permalink: /pushover-and-motionpie/
author: Todd Lichty
---
<!--kg-card-begin: markdown--><p>I have been playing around with my Raspberry Pi 3 at home lately. I enjoy moving from a purely software based existence when I am working to watching my code change something in the real world when I am using my Pi.</p>
<p>I purchased the official <a href="https://www.raspberrypi.org/help/camera-module-setup/">Raspberry Pi Camera Module</a> and quickly had the module installed and working. After writing some quick examples with python and attaching an PIR sensor to trigger the camera, I did some googling to check out what other makers had created with their camera modules.</p>
<p><img src="https://toddlichty.github.io/images/pi_camera.jpg" /></p>
<p>I stumbled upon <a href="https://github.com/ccrisan/motionpie">MotionPie</a> and had it setup and configured in about 30 minutes. <em>NOTE</em>: There is a new version of this project that I need to upgrade to called <a href="https://github.com/ccrisan/motioneyeos">MotionEye</a>.</p>
<p>After having MotionPie running at home for the past couple of Months, I read the following <a href="https://www.raspberrypi.org/magpi/add-push-notifications-to-motioneyeos/">article</a> in the <a href="https://www.raspberrypi.org/weekly/">Raspberry Pi Weekly</a> newsletter. I immediately signed up for a <a href="https://pushover.net/">Pushover</a> account and created a <a href="https://github.com/ToddLichty/Pushover.py">Python script</a> to send push notifications when the alarm is triggered.</p>
<p>I want to play with Pushover more to see what other purposes I can utilize it for!</p>
<!--kg-card-end: markdown-->