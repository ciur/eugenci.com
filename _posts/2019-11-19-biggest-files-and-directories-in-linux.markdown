---
layout: post
title:  "Biggest Files and Directories in Linux"
date:   2019-11-19 08:00:00 +0200
categories: devops
---

When troubleshooting a Linux server, one of the first things to check is
system space. A simple command:

    df -h

will display in human readable format used storage space.
Example of output:

    Filesystem      Size  Used Avail Use% Mounted on
    udev            962M     0  962M   0% /dev
    tmpfs           200M  7.0M  193M   4% /run
    /dev/sda         49G   39G  7.6G  84% /
    tmpfs           996M     0  996M   0% /dev/shm
    tmpfs           5.0M     0  5.0M   0% /run/lock
    tmpfs           996M     0  996M   0% /sys/fs/cgroup


In case that some device has little space left - it makes sense to ask
yourself which file or directory  uses most of disk space? In example above,
device /dev/sda mounted on root (/) uses 84%.

Following (du = disk usage) command comes handy:

    du -h  /  | sort -h -r | head -n 10

It will display top 10 biggest files or directories in Linux system.
Example from my system:

    7.7G    /
    5.0G    /var
    4.0G    /var/lib
    3.6G    /var/lib/jenkins
    3.0G    /var/lib/jenkins/jobs
    2.1G    /usr
    1.4G    /var/lib/jenkins/jobs/04-ax/jobs
    1.4G    /var/lib/jenkins/jobs/04-ax
    1.4G    /usr/lib
    1.1G    /var/lib/jenkins/jobs/04-ax/jobs/build-whl/builds

Aha! jenkins folder /var/lib/jenkins/jobs/04-ax/jobs needs some clean up!