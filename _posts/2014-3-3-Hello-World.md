---
layout: post
title: Raspberry pi 2 model b
categories: 
  - test
  - raspberry
tags: raspberry
published: true
---

> some quotations

Next you can update your site name, avatar and other options using the _config.yml file in the root of your repository (shown below).

![_config.yml]({{ site.baseurl }}/images/config.png)

# Raspberry pi 2 model b

## First steps
### Mounting external hdd

- Step 1.
Log on pi using ssh terminal and execute:
ls -l /dev/disk/by-uuid/

You will see something like the following:

lrwxrwxrwx 1 root root 10 Jan  1  1970 0AC4D607C4D5F543 -> ../../sda1
Note down the value of the UUID --> 0AC4D607C4D5F543

- Step 2.
Create a location for mount point:
<kbd>sudo mkdir /media/NASDRIVE</kbd>

Give proper permission:
sudo chmod 775 /media/NASDRIVE

- Step 3.
Get the uid, gid for pi user and group with id command (usually 1000)

- Step 4.
Mount the USB Drive and then check if it is accessible at /media/NASDRIVE
sudo mount -t ntfs-3g -o uid=1000,gid=1000,umask=007 /dev/sda1 /media/NASDRIVE

Note:
ntfs-3g for NTFS Drives
vfat for FAT32 Drives
ext4 for ext4 Drives

- Step 5.
Now, we will configure RasPi to do this after every reboot:
Take a backup of current fstab and then edit
sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab

Add the mount information in the fstab file (replace UUID with your own):
UUID=0AC4D607C4D5F543 /media/NASDRIVE ntfs-3g uid=1000,gid=1000,umask=007 0 0

- Step 6.
Reboot
sudo reboot

[how to setup automount](http://www.techjawab.com/2013/06/how-to-setup-mount-auto-mount-usb-hard.html)

### Samba
[configure samba](http://raspberrywebserver.com/serveradmin/share-your-raspberry-pis-files-and-folders-across-a-network.html)

{% highlight php linenos %}
 <?php
 	echo 'test';
 ?>
{% endhighlight %}
