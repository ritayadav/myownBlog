---
title: "Find and Highlight Duplicate Values in Excel using VBA (Macro)"
modified: 2018-12-03T03:55:10-04:00
permalink: /posts/2018/12/Find and Highlight Duplicate Values in Excel using VBA (Macro)/
categories: 
  - Excel
  - Windows
tags:
  - Visual Basic
  - Macro
---

Android Studio is the official IDE for Android. It’s open-source, distributed under the Apache license. This tutorial is going to show you how to install Android Studio on Ubuntu 16.04.


### Install Java 8 on Ubuntu 16.04

No matter which method you choose, you first need to install Java. It’s recommended to install Oracle Java, because it has a performance edge over OpenJDK. Run the following commands in terminal to install it from PPA.

sudo add-apt-repository ppa:webupd8team/java
{: .notice}
sudo apt-get update
{: .notice}
sudo apt-get install java-common oracle-java8-installer
{: .notice}

During the installation process you will need to accept the Oracle License agreement. Once installed we need to set Java environment variables such as

`JAVA_HOME` on Ubuntu 16.04.

sudo apt-get install oracle-java8-set-default
{: .notice}
source /etc/profile
{: .notice}

The above two commands will set the correct Java environment variables.

### Installing Android Studio in Ubuntu 16.04

At the time of this writting, the latest stable version is Android Studio 2.3.1, release on April 2, 2017. Run the following commands to add Android Studio PPA and install it.

sudo add-apt-repository ppa:maarten-fonville/android-studio
{: .notice}
sudo apt update
{: .notice}
sudo apt install android-studio
{: .notice}

During the installation, the latest Android Studio zip file will be downloaded from Google server. Once the installation is finished, you can open Android Studio from Unity Dash or your preferred app launcher.

If the icon didn’t load, then please log out and log back in or use the following command to start Android Studio.
