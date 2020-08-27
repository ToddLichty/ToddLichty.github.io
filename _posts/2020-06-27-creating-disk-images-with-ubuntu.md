---
layout: post
title: Creating Disk Images With Ubuntu
permalink: /creating-disk-images-with-ubuntu/
author: Todd Lichty
---
I've been delaying upgrading my work laptop from Ubuntu 18.04 to the latest 20.04 (Focal Fossa). With the spring term finished at the beginning of this month and the fall term still a few weeks away, I figured now would be a "safe" time to finally perform the upgrade.

I've been in this industry long enough to know that backups are a must. Too many disasters could have been avoided by simply having a proper backup. When I was running Windows as my primary OS, I was a die hard [Acronis True Image](https://www.acronis.com/en-eu/personal/computer-backup/) fan. It was easy to boot the workstation with the Acronis Rescue CD and quickly image the drive. 

Having migrated over to Ubuntu in the last couple of years, I was curious what options were available for imaging drives. As you might expect there [were](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwivyMOdoqzrAhWzlHIEHRZoBmc4ChC3AjAAegQIBRAB&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DcCNzl2x5Gdk&usg=AOvVaw3vikRQLSBojZXzXRjrBjan) [quite](https://itstillworks.com/clone-hard-drive-ubuntu-6884403.html) a [few](https://clonezilla.org/) options.

I opted to use the Disks utility that ships with Ubuntu paired with an Ubuntu Live CD. I've never trusted applications that claim to clone a "live" hard drive. I feel it is safer to boot into a different OS and then clone/image a hard drive.

The steps below outline how I captured an image of my laptop onto an external USB hard drive.

1. Plugged in the 3TB external USB hard drive where I wanted the hard drive image to be saved.
2. Plugged in the Ubuntu Live USB key.
3. Turned on the laptop and booted into Ubuntu on the USB.
4. When prompted, I clicked on the Try Ubuntu button.
5. After the laptop was finished booting, I started the Disks utility from Applications.
<img src="/images/2020_08_disks.png" />
6. I selected the main hard drive from the list shown in the Disks applications and then clicked the three vertical dots located in the header.
7. From the drop down menu, I clicked on the "Create Disk Image..." item.
<img src="/images/2020_08_disks_create_image.png" />
8. In the pop-up window, I changed the "Save in folder" to the 3TB external hard drive and clicked the "Start Creating...".
<img src="/images/2020_08_disks_create_popup.png" />
It took about 90 minutes to complete the full image. Knowing that I have a backup image of my laptop makes the prospect of upgrading my OS much less stressful.
<img src="/images/2020_08_disks_progress.png" />