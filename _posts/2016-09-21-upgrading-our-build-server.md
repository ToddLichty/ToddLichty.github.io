---
layout: post
title: Upgrading Our Build Server
permalink: /upgrading-our-build-server/
---
It's been a long time coming, but we are finally upgrading our build/stage server. Our current server was getting a little long in the tooth. It's served us well but it is over four years old and was in need of replacement. There was a lot of humming and hawing around moving to the cloud rather than procuring a physical server. I suspect that this will be the last physical server we invest in. It is hard to let go of old habits.

Once the server arrived, it was time to do the OS install and windows update dance. Installing the OS was quick and painless. All the drivers were detected and installed. There were no "Unknown devices" listed in Device Manager. That's always a plus. :)

Next step was to run Windows Update. I started WU and waited...and waited...and waited. I left it running overnight and came back the next day to WU still "Checking for updates". I rebooted the server and tried again. I let WU continue to check for updates while I ran for a meeting. When I returned an hour later, WU was installing 2 of 237 updates.

After multiple rounds of updates and reboots, the server was stable. I then added the Hyper-V and the Windows Server Backup roles. After yet another round of Windows Updates, the server was setup and ready for "deployment". Deployment consisted of moving the server out of my office and into the server rack. :)

The server was configured with 4 NICs which let me dedicate a physical NIC to each of the virtual servers that will be running on this server as well as two for management of the host server itself. I thought this was a great idea and it seemed pretty straightforward. I was wrong.

I went into Hyper-V Manager and configured two virtual switches. There was some confusion around which NIC to choose from the list. The NIC that was labeled as MANUFACTURER #1 did NOT match up to the NIC labeled #1 on the back of the server. After spending some time messing around with unplugging network cables and determining which NIC was which, I was able to have NIC 2 and 4 configured to work with only the virtual server and NICs 1 and 3 be assigned to the host OS.

The server has been running the two virtual machines for three days now and it seems to be very stable.

Next up, replacing our CI server.
