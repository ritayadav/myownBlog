---
title: "Move Home Folder to Another Partition"
modified: 2018-1-13T03:55:10-04:00
permalink: /posts/2018/1/Move Home Folder to Another Partition/
categories: 
  - Linux
tags:
  - Home Partition
---

If you have accepted the default option while installing Ubuntu, or that your computer comes with Ubuntu pre-installed, chances are that your Home folder and the system folders all lie in the same partition. This is perfectly fine, but that will surely grow in size has to be the /home directory. This is because system accounts (users) directories will reside in /home except root account – here users will continuously store documents and other files.

When these directories fill up, this can cause critical problems on the root file system resulting into system boot failure or some other related issues. However, sometimes you can only notice this after installing your system and configuring all directories on the root file system/partition

One of the good practice is to give the Home folder its own partition, so whatever changes you made to the System folder won’t affect your Home directory, and you can easily upgrade or reinstall Ubuntu with ease.

### Creating a new partition

fdisk is started by typing (as root or sudoer) fdisk device at the command prompt. device might be something like /dev/hda or /dev/sda

sudo fdisk /dev/sda 
{: .notice}
These are Generic commands:

   d    delete a partition  
   F    list free unpartitioned space
   l    list known partition types
   n    add a new partition
   p    print the partition table
   t    change a partition type
   v    verify the partition table
   i    print information about a partition

These are steps to create Partition.

1. Press n to create new Partition;
2. Enter value of Partition type;
3. Enter the value of first cylinder or just press enter;
4. Enter the value Partition size;
5. Enter w to write Partition table

Partition is read now we should format it to use.

To format we use

sudo mkfs.ext4 /dev/sda9
{: .notice}
assuming /sdb9 is the new partition for HOME
Select right Partition to format otherwise data will be lost.

Temporarily mount the new partition:

sudo mkdir /mnt/tmp
{: .notice}
sudo mount /dev/sdb9 /mnt/tmp
{: .notice}

Copy HOME to the new location:

sudo rsync -avx /home/ /mnt/tmp
{: .notice}
sudo cp -aR /home/* /mnt/tmp
{: .notice}
After that, we will find the difference between the two directories using the diff tool, if all is well, continue to the next step.

sudo diff -r /home /mnt/tmp/home
{: .notice}
Afterwards, delete all the old content in the /home as follows.

sudo rm -rf /home/*
{: .notice}
Next unmount mnt/tmp.

sudo umount mnt/tmp
{: .notice}
Finally, we have to mount the filesystem /dev/sdb9 to /home for the mean time.

sudo mount /dev/sdb9 /home
{: .notice}
sudo ls -l /home
{: .notice}
The above changes will last only for the current boot, make some changes in the /etc/fstab to make the changes permanent.

Use following command to get the partition UUID.

sudo blkid /dev/sdb9
{: .notice}
Once you know the partition UUID, open /etc/fstab file add following line.

sudo nano /etc/fstab   #or any other editor
{: .notice}
and add the following line at the end:

UUID=<noted number from above>    	/home    	ext4    	defaults   0  2

Take care to choose the appropriate filesystem here, e.g. ext3 if ext3 formatted

Explaining the field in the line above:

UUID – specifies the block device, you can alternatively use the device file /dev/sdb1.
/home – this is the mount point.

etx4 – describes the filesystem type on the device/partition.

defaults – mount options, (here this value means rw, suid, dev, exec, auto, nouser, and async).

0 – used by dump tool, 0 meaning don’t dump if filesystem is not present.

2 – used by fsck tool for discovering filesystem check order, this value means check this device after root filesystem.

Save the file and reboot the system.
After a reboot, your /home resides on the new drive having plenty of space.
You can run following command to see that /home directory has been successfully moved into a dedicated partition.

sudo df -hl
{: .notice}