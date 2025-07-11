# Assignment-on-Testing-Linux-Servers
Taskk 1

Task 1: System Monitoring Setup
Objective: Configure a monitoring system to ensure the development environment’s health, performance, and capacity planning.
Scenario:
The development server is reporting intermittent performance issues.
New developers need visibility into system resource usage for their tasks.
System metrics must be consistently tracked for effective capacity planning.
Requirements:
Install and configure monitoring tools (htop or nmon) to monitor CPU, memory, and process usage.
Set up disk usage monitoring to track storage availability using df and du.
Implement process monitoring to identify resource-intensive applications.
Ceate a basic reporting structure (e.g., save outputs to a log file for review).
===============================================================================================
ANS

root@SomuMH:~# sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu noble InRelease
Hit:2 http://security.ubuntu.com/ubuntu noble-security InRelease
Hit:3 http://archive.ubuntu.com/ubuntu noble-updates InRelease
Hit:4 http://archive.ubuntu.com/ubuntu noble-backports InRelease
Reading package lists... Error!
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_noble-security_restricted_binary-amd64_Packages (1)
W: You may want to run apt-get update to correct these problems
E: The package cache file is corrupted
root@SomuMH:~# sudo apt install -y htop nmon
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  libncurses6 libnl-3-200 libnl-genl-3-200
Suggested packages:
  lm-sensors strace
The following NEW packages will be installed:
  htop libncurses6 libnl-3-200 libnl-genl-3-200 nmon
0 upgraded, 5 newly installed, 0 to remove and 37 not upgraded.
Need to get 422 kB of archives.
After this operation, 1193 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu noble/main amd64 libncurses6 amd64 6.4+20240113-1ubuntu2 [112 kB]
Get:2 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libnl-3-200 amd64 3.7.0-0.3build1.1 [55.7 kB]
Get:3 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libnl-genl-3-200 amd64 3.7.0-0.3build1.1 [12.2 kB]
Get:4 http://archive.ubuntu.com/ubuntu noble/main amd64 htop amd64 3.3.0-4build1 [171 kB]
Get:5 http://archive.ubuntu.com/ubuntu noble/universe amd64 nmon amd64 16p+debian-1 [71.4 kB]
Fetched 422 kB in 2s (227 kB/s)
Selecting previously unselected package libncurses6:amd64.
(Reading database ... 41590 files and directories currently installed.)
Preparing to unpack .../libncurses6_6.4+20240113-1ubuntu2_amd64.deb ...
Unpacking libncurses6:amd64 (6.4+20240113-1ubuntu2) ...
Selecting previously unselected package libnl-3-200:amd64.
Preparing to unpack .../libnl-3-200_3.7.0-0.3build1.1_amd64.deb ...
Unpacking libnl-3-200:amd64 (3.7.0-0.3build1.1) ...
Selecting previously unselected package libnl-genl-3-200:amd64.
Preparing to unpack .../libnl-genl-3-200_3.7.0-0.3build1.1_amd64.deb ...
Unpacking libnl-genl-3-200:amd64 (3.7.0-0.3build1.1) ...
Selecting previously unselected package htop.
Preparing to unpack .../htop_3.3.0-4build1_amd64.deb ...
Unpacking htop (3.3.0-4build1) ...
Selecting previously unselected package nmon.
Preparing to unpack .../nmon_16p+debian-1_amd64.deb ...
Unpacking nmon (16p+debian-1) ...
Setting up libncurses6:amd64 (6.4+20240113-1ubuntu2) ...
Setting up libnl-3-200:amd64 (3.7.0-0.3build1.1) ...
Setting up nmon (16p+debian-1) ...
Setting up libnl-genl-3-200:amd64 (3.7.0-0.3build1.1) ...
Setting up htop (3.3.0-4build1) ...
Processing triggers for man-db (2.12.0-4build2) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for libc-bin (2.39-0ubuntu8.4) ...
root@SomuMH:~# sudo apt install -y htop nmon
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
htop is already the newest version (3.3.0-4build1).
nmon is already the newest version (16p+debian-1).
0 upgraded, 0 newly installed, 0 to remove and 37 not upgraded.
root@SomuMH:~# df -g
df: invalid option -- 'g'
Try 'df --help' for more information.
root@SomuMH:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
none            1.9G     0  1.9G   0% /usr/lib/modules/5.15.167.4-microsoft-standard-WSL2
none            1.9G  4.0K  1.9G   1% /mnt/wsl
drivers         238G  206G   32G  87% /usr/lib/wsl/drivers
/dev/sdc       1007G  1.6G  955G   1% /
none            1.9G   76K  1.9G   1% /mnt/wslg
none            1.9G     0  1.9G   0% /usr/lib/wsl/lib
rootfs          1.9G  2.4M  1.9G   1% /init
none            1.9G  520K  1.9G   1% /run
none            1.9G     0  1.9G   0% /run/lock
none            1.9G     0  1.9G   0% /run/shm
tmpfs           4.0M     0  4.0M   0% /sys/fs/cgroup
none            1.9G   76K  1.9G   1% /mnt/wslg/versions.txt
none            1.9G   76K  1.9G   1% /mnt/wslg/doc
C:\             238G  206G   32G  87% /mnt/c
D:\             450G  132G  319G  30% /mnt/d
E:\             483G   87G  396G  19% /mnt/e
tmpfs           382M   16K  382M   1% /run/user/1000
tmpfs           382M   16K  382M   1% /run/user/0
root@SomuMH:~# du -h
4.0K    ./.ssh
28K     .
root@SomuMH:~# du -f
du: invalid option -- 'f'
Try 'du --help' for more information.
root@SomuMH:~# df -h > /var/log/sys_monitoring/disk_usage.log
-bash: /var/log/sys_monitoring/disk_usage.log: No such file or directory
root@SomuMH:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
none            1.9G     0  1.9G   0% /usr/lib/modules/5.15.167.4-microsoft-standard-WSL2
none            1.9G  4.0K  1.9G   1% /mnt/wsl
drivers         238G  206G   32G  87% /usr/lib/wsl/drivers
/dev/sdc       1007G  1.6G  955G   1% /
none            1.9G   76K  1.9G   1% /mnt/wslg
none            1.9G     0  1.9G   0% /usr/lib/wsl/lib
rootfs          1.9G  2.4M  1.9G   1% /init
none            1.9G  520K  1.9G   1% /run
none            1.9G     0  1.9G   0% /run/lock
none            1.9G     0  1.9G   0% /run/shm
tmpfs           4.0M     0  4.0M   0% /sys/fs/cgroup
none            1.9G   76K  1.9G   1% /mnt/wslg/versions.txt
none            1.9G   76K  1.9G   1% /mnt/wslg/doc
C:\             238G  206G   32G  87% /mnt/c
D:\             450G  132G  319G  30% /mnt/d
E:\             483G   87G  396G  19% /mnt/e
tmpfs           382M   16K  382M   1% /run/user/1000
tmpfs           382M   16K  382M   1% /run/user/0
root@SomuMH:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
none            1.9G     0  1.9G   0% /usr/lib/modules/5.15.167.4-microsoft-standard-WSL2
none            1.9G  4.0K  1.9G   1% /mnt/wsl
drivers         238G  206G   32G  87% /usr/lib/wsl/drivers
/dev/sdc       1007G  1.6G  955G   1% /
none            1.9G   76K  1.9G   1% /mnt/wslg
none            1.9G     0  1.9G   0% /usr/lib/wsl/lib
rootfs          1.9G  2.4M  1.9G   1% /init
none            1.9G  520K  1.9G   1% /run
none            1.9G     0  1.9G   0% /run/lock
none            1.9G     0  1.9G   0% /run/shm
tmpfs           4.0M     0  4.0M   0% /sys/fs/cgroup
none            1.9G   76K  1.9G   1% /mnt/wslg/versions.txt
none            1.9G   76K  1.9G   1% /mnt/wslg/doc
C:\             238G  206G   32G  87% /mnt/c
D:\             450G  132G  319G  30% /mnt/d
E:\             483G   87G  396G  19% /mnt/e
tmpfs           382M   16K  382M   1% /run/user/1000
tmpfs           382M   16K  382M   1% /run/user/0
root@SomuMH:~# df -h > /var/log/sys_monitoring/disk_usage.log
-bash: /var/log/sys_monitoring/disk_usage.log: No such file or directory
root@SomuMH:~# cd /var/log
root@SomuMH:/var/log# ls -ltr
total 2600
drwxr-xr-x  2 root      root              4096 Jan 31 17:11 dist-upgrade
-rw-rw----  1 root      utmp                 0 Feb 15 08:09 btmp
-rw-rw-r--  1 root      utmp                 0 Feb 15 08:09 lastlog
-rw-r--r--  1 root      root                 0 Feb 15 08:09 faillog
lrwxrwxrwx  1 root      root                39 Feb 15 08:09 README -> ../../usr/share/doc/systemd/README.logs
drwx------  2 root      root              4096 Feb 15 08:09 private
-rw-r--r--  1 root      root            118497 Feb 15 08:09 bootstrap.log
-rw-r--r--  1 root      root               790 Feb 15 08:11 fontconfig.log
drwxr-xr-x  2 landscape landscape         4096 Feb 15 08:11 landscape
drwxr-sr-x+ 3 root      systemd-journal   4096 Jun 14 05:04 journal
-rw-r-----  1 root      adm              10471 Jun 14 05:04 dmesg.3.gz
drwxr-x---  2 root      adm               4096 Jun 14 06:29 unattended-upgrades
-rw-r--r--  1 root      root             28793 Jun 15 06:19 alternatives.log
-rw-r-----  1 root      adm              10690 Jun 21 04:41 dmesg.2.gz
-rw-r-----  1 syslog    adm              17495 Jun 21 08:17 auth.log.1
-rw-r-----  1 syslog    adm              89259 Jun 22 04:05 kern.log.1
-rw-r-----  1 syslog    adm             895116 Jun 22 04:05 syslog.1
-rw-r-----  1 root      adm              10461 Jun 23 03:02 dmesg.1.gz
-rw-r-----  1 root      adm              33875 Jun 28 04:41 dmesg.0
drwxr-x---  2 root      adm               4096 Jun 28 04:56 apache2
drwxr-xr-x  2 root      adm               4096 Jun 28 06:57 nginx
-rw-rw-r--  1 root      utmp             11520 Jun 28 10:20 wtmp
-rw-r-----  1 root      adm              73082 Jun 28 10:20 dmesg
-rw-r-----  1 syslog    adm              92857 Jun 28 10:20 kern.log
drwxr-xr-x  2 root      root              4096 Jun 28 10:23 apt
-rw-r--r--  1 root      root            449947 Jun 28 10:23 dpkg.log
-rw-r-----  1 syslog    adm              14739 Jun 28 10:37 auth.log
-rw-r-----  1 syslog    adm             732415 Jun 28 10:39 syslog
root@SomuMH:/var/log# cd sys_monitoring
-bash: cd: sys_monitoring: No such file or directory
root@SomuMH:/var/log# mkdir sys_monitoring
root@SomuMH:/var/log# ls -ltr
total 2604
drwxr-xr-x  2 root      root              4096 Jan 31 17:11 dist-upgrade
-rw-rw----  1 root      utmp                 0 Feb 15 08:09 btmp
-rw-rw-r--  1 root      utmp                 0 Feb 15 08:09 lastlog
-rw-r--r--  1 root      root                 0 Feb 15 08:09 faillog
lrwxrwxrwx  1 root      root                39 Feb 15 08:09 README -> ../../usr/share/doc/systemd/README.logs
drwx------  2 root      root              4096 Feb 15 08:09 private
-rw-r--r--  1 root      root            118497 Feb 15 08:09 bootstrap.log
-rw-r--r--  1 root      root               790 Feb 15 08:11 fontconfig.log
drwxr-xr-x  2 landscape landscape         4096 Feb 15 08:11 landscape
drwxr-sr-x+ 3 root      systemd-journal   4096 Jun 14 05:04 journal
-rw-r-----  1 root      adm              10471 Jun 14 05:04 dmesg.3.gz
drwxr-x---  2 root      adm               4096 Jun 14 06:29 unattended-upgrades
-rw-r--r--  1 root      root             28793 Jun 15 06:19 alternatives.log
-rw-r-----  1 root      adm              10690 Jun 21 04:41 dmesg.2.gz
-rw-r-----  1 syslog    adm              17495 Jun 21 08:17 auth.log.1
-rw-r-----  1 syslog    adm              89259 Jun 22 04:05 kern.log.1
-rw-r-----  1 syslog    adm             895116 Jun 22 04:05 syslog.1
-rw-r-----  1 root      adm              10461 Jun 23 03:02 dmesg.1.gz
-rw-r-----  1 root      adm              33875 Jun 28 04:41 dmesg.0
drwxr-x---  2 root      adm               4096 Jun 28 04:56 apache2
drwxr-xr-x  2 root      adm               4096 Jun 28 06:57 nginx
-rw-rw-r--  1 root      utmp             11520 Jun 28 10:20 wtmp
-rw-r-----  1 root      adm              73082 Jun 28 10:20 dmesg
-rw-r-----  1 syslog    adm              92857 Jun 28 10:20 kern.log
drwxr-xr-x  2 root      root              4096 Jun 28 10:23 apt
-rw-r--r--  1 root      root            449947 Jun 28 10:23 dpkg.log
-rw-r-----  1 syslog    adm              14739 Jun 28 10:37 auth.log
-rw-r-----  1 syslog    adm             732415 Jun 28 10:39 syslog
drwxr-xr-x  2 root      root              4096 Jun 28 10:39 sys_monitoring
root@SomuMH:/var/log# cd ..
root@SomuMH:/var# cd ..
root@SomuMH:/# pwd
/
root@SomuMH:/# df -h > /var/log/sys_monitoring/disk_usage.log
root@SomuMH:/# du -sh /home/* >> /var/log/sys_monitoring/disk_usage.log
root@SomuMH:/# cd /var/log
root@SomuMH:/var/log# ls -ltr
total 2608
drwxr-xr-x  2 root      root              4096 Jan 31 17:11 dist-upgrade
-rw-rw----  1 root      utmp                 0 Feb 15 08:09 btmp
-rw-rw-r--  1 root      utmp                 0 Feb 15 08:09 lastlog
-rw-r--r--  1 root      root                 0 Feb 15 08:09 faillog
lrwxrwxrwx  1 root      root                39 Feb 15 08:09 README -> ../../usr/share/doc/systemd/README.logs
drwx------  2 root      root              4096 Feb 15 08:09 private
-rw-r--r--  1 root      root            118497 Feb 15 08:09 bootstrap.log
-rw-r--r--  1 root      root               790 Feb 15 08:11 fontconfig.log
drwxr-xr-x  2 landscape landscape         4096 Feb 15 08:11 landscape
drwxr-sr-x+ 3 root      systemd-journal   4096 Jun 14 05:04 journal
-rw-r-----  1 root      adm              10471 Jun 14 05:04 dmesg.3.gz
drwxr-x---  2 root      adm               4096 Jun 14 06:29 unattended-upgrades
-rw-r--r--  1 root      root             28793 Jun 15 06:19 alternatives.log
-rw-r-----  1 root      adm              10690 Jun 21 04:41 dmesg.2.gz
-rw-r-----  1 syslog    adm              17495 Jun 21 08:17 auth.log.1
-rw-r-----  1 syslog    adm              89259 Jun 22 04:05 kern.log.1
-rw-r-----  1 syslog    adm             895116 Jun 22 04:05 syslog.1
-rw-r-----  1 root      adm              10461 Jun 23 03:02 dmesg.1.gz
-rw-r-----  1 root      adm              33875 Jun 28 04:41 dmesg.0
drwxr-x---  2 root      adm               4096 Jun 28 04:56 apache2
drwxr-xr-x  2 root      adm               4096 Jun 28 06:57 nginx
-rw-rw-r--  1 root      utmp             11520 Jun 28 10:20 wtmp
-rw-r-----  1 root      adm              73082 Jun 28 10:20 dmesg
-rw-r-----  1 syslog    adm              92857 Jun 28 10:20 kern.log
drwxr-xr-x  2 root      root              4096 Jun 28 10:23 apt
-rw-r--r--  1 root      root            449947 Jun 28 10:23 dpkg.log
-rw-r-----  1 syslog    adm              14739 Jun 28 10:37 auth.log
-rw-r-----  1 syslog    adm             733219 Jun 28 10:40 syslog
drwxr-xr-x  2 root      root              4096 Jun 28 10:40 sys_monitoring
root@SomuMH:/var/log# cd sys_monitoring
root@SomuMH:/var/log/sys_monitoring# ls -ltr
total 4
-rw-r--r-- 1 root root 994 Jun 28 10:40 disk_usage.log
root@SomuMH:/var/log/sys_monitoring# cd ..
root@SomuMH:/var/log# cd ..
root@SomuMH:/var# cd ..
root@SomuMH:/# pwd
/
root@SomuMH:/# ls -ltr
total 2448
drwxr-xr-x   2 root root    4096 Feb 26  2024 bin.usr-is-merged
drwxr-xr-x   2 root root    4096 Mar 31  2024 sbin.usr-is-merged
drwxr-xr-x   2 root root    4096 Apr  8  2024 lib.usr-is-merged
lrwxrwxrwx   1 root root       8 Apr 22  2024 sbin -> usr/sbin
lrwxrwxrwx   1 root root       9 Apr 22  2024 lib64 -> usr/lib64
lrwxrwxrwx   1 root root       7 Apr 22  2024 lib -> usr/lib
drwxr-xr-x   2 root root    4096 Apr 22  2024 boot
lrwxrwxrwx   1 root root       7 Apr 22  2024 bin -> usr/bin
drwxr-xr-x   2 root root    4096 Feb 15 08:09 srv
drwxr-xr-x   2 root root    4096 Feb 15 08:09 opt
drwxr-xr-x   2 root root    4096 Feb 15 08:09 media
drwxr-xr-x  12 root root    4096 Feb 15 08:09 usr
-rwxrwxrwx   1 root root 2424984 Mar 19 21:11 init
drwx------   2 root root   16384 Apr 26 05:36 lost+found
drwxr-xr-x   7 root root    4096 Jun  6 04:18 mnt
drwxr-xr-x   2 root root    4096 Jun 14 05:04 snap
drwxr-xr-x   3 root root    4096 Jun 14 05:05 home
dr-xr-xr-x  11 root root       0 Jun 28 04:41 sys
drwxr-xr-x  14 root root    4096 Jun 28 04:56 var
drwx------   3 root root    4096 Jun 28 06:57 root
dr-xr-xr-x 216 root root       0 Jun 28 10:20 proc
drwxr-xr-x  16 root root    3580 Jun 28 10:20 dev
drwxr-xr-x  20 root root     600 Jun 28 10:21 run
drwxr-xr-x  92 root root    4096 Jun 28 10:23 etc
drwxrwxrwt  12 root root    4096 Jun 28 10:24 tmp
root@SomuMH:/# cd home
root@SomuMH:/home# lss -ltr
Command 'lss' not found, but there are 16 similar ones.
root@SomuMH:/home# ls -ltr
total 4
drwxr-x--- 7 shiremath shiremath 4096 Jun 28 06:32 shiremath
root@SomuMH:/home# du -sh /home/* >> /var/log/sys_monitoring/disk_usage.log
root@SomuMH:/home# ls -ltr
total 4
drwxr-x--- 7 shiremath shiremath 4096 Jun 28 06:32 shiremath
root@SomuMH:/home# cd shiremath/
root@SomuMH:/home/shiremath# ls -ltr
total 16
drwxr-xr-x 3 shiremath shiremath 4096 Jun 15 05:32 b12
-rw-rw-r-- 1 shiremath shiremath  112 Jun 21 05:13 data.csv
-rw-rw-r-- 1 shiremath shiremath  159 Jun 21 05:52 access.log
-rw-r--r-- 1 shiremath shiremath   55 Jun 23 03:03 cpu_usage.txt
root@SomuMH:/home/shiremath# cd ..
root@SomuMH:/home# pwd
/home
root@SomuMH:/home# du -sh /home/* >> /var/log/sys_monitoring/disk_usage.log
root@SomuMH:/home# cd ..
root@SomuMH:/# pwd
/
root@SomuMH:/# cd /var/log
root@SomuMH:/var/log# ls -ltr
total 2608
drwxr-xr-x  2 root      root              4096 Jan 31 17:11 dist-upgrade
-rw-rw----  1 root      utmp                 0 Feb 15 08:09 btmp
-rw-rw-r--  1 root      utmp                 0 Feb 15 08:09 lastlog
-rw-r--r--  1 root      root                 0 Feb 15 08:09 faillog
lrwxrwxrwx  1 root      root                39 Feb 15 08:09 README -> ../../usr/share/doc/systemd/README.logs
drwx------  2 root      root              4096 Feb 15 08:09 private
-rw-r--r--  1 root      root            118497 Feb 15 08:09 bootstrap.log
-rw-r--r--  1 root      root               790 Feb 15 08:11 fontconfig.log
drwxr-xr-x  2 landscape landscape         4096 Feb 15 08:11 landscape
drwxr-sr-x+ 3 root      systemd-journal   4096 Jun 14 05:04 journal
-rw-r-----  1 root      adm              10471 Jun 14 05:04 dmesg.3.gz
drwxr-x---  2 root      adm               4096 Jun 14 06:29 unattended-upgrades
-rw-r--r--  1 root      root             28793 Jun 15 06:19 alternatives.log
-rw-r-----  1 root      adm              10690 Jun 21 04:41 dmesg.2.gz
-rw-r-----  1 syslog    adm              17495 Jun 21 08:17 auth.log.1
-rw-r-----  1 syslog    adm              89259 Jun 22 04:05 kern.log.1
-rw-r-----  1 syslog    adm             895116 Jun 22 04:05 syslog.1
-rw-r-----  1 root      adm              10461 Jun 23 03:02 dmesg.1.gz
-rw-r-----  1 root      adm              33875 Jun 28 04:41 dmesg.0
drwxr-x---  2 root      adm               4096 Jun 28 04:56 apache2
drwxr-xr-x  2 root      adm               4096 Jun 28 06:57 nginx
-rw-rw-r--  1 root      utmp             11520 Jun 28 10:20 wtmp
-rw-r-----  1 root      adm              73082 Jun 28 10:20 dmesg
-rw-r-----  1 syslog    adm              92857 Jun 28 10:20 kern.log
drwxr-xr-x  2 root      root              4096 Jun 28 10:23 apt
-rw-r--r--  1 root      root            449947 Jun 28 10:23 dpkg.log
-rw-r-----  1 syslog    adm              14739 Jun 28 10:37 auth.log
drwxr-xr-x  2 root      root              4096 Jun 28 10:40 sys_monitoring
-rw-r-----  1 syslog    adm             734827 Jun 28 10:42 syslog
root@SomuMH:/var/log# cd sys_monitoring/
root@SomuMH:/var/log/sys_monitoring# ls -ltr
total 4
-rw-r--r-- 1 root root 1034 Jun 28 10:42 disk_usage.log
root@SomuMH:/var/log/sys_monitoring# du -sh /home/* >> /var/log/sys_monitoring/disk_usage.log
root@SomuMH:/var/log/sys_monitoring# df -h > /var/log/sys_monitoring/disk_usage.log
root@SomuMH:/var/log/sys_monitoring# ls -ltr
total 4
-rw-r--r-- 1 root root 974 Jun 28 10:42 disk_usage.log
root@SomuMH:/var/log/sys_monitoring# ls -ltr
total 4
-rw-r--r-- 1 root root 974 Jun 28 10:42 disk_usage.log
root@SomuMH:/var/log/sys_monitoring# du -sh /home/* >> /var/log/sys_monitoring/disk_usage1.log
root@SomuMH:/var/log/sys_monitoring# ls -ltr
total 8
-rw-r--r-- 1 root root 974 Jun 28 10:42 disk_usage.log
-rw-r--r-- 1 root root  20 Jun 28 10:43 disk_usage1.log
root@SomuMH:/var/log/sys_monitoring# cat disk_usage.log
Filesystem      Size  Used Avail Use% Mounted on
none            1.9G     0  1.9G   0% /usr/lib/modules/5.15.167.4-microsoft-standard-WSL2
none            1.9G  4.0K  1.9G   1% /mnt/wsl
drivers         238G  206G   32G  87% /usr/lib/wsl/drivers
/dev/sdc       1007G  1.6G  955G   1% /
none            1.9G   76K  1.9G   1% /mnt/wslg
none            1.9G     0  1.9G   0% /usr/lib/wsl/lib
rootfs          1.9G  2.4M  1.9G   1% /init
none            1.9G  520K  1.9G   1% /run
none            1.9G     0  1.9G   0% /run/lock
none            1.9G     0  1.9G   0% /run/shm
tmpfs           4.0M     0  4.0M   0% /sys/fs/cgroup
none            1.9G   76K  1.9G   1% /mnt/wslg/versions.txt
none            1.9G   76K  1.9G   1% /mnt/wslg/doc
C:\             238G  206G   32G  87% /mnt/c
D:\             450G  132G  319G  30% /mnt/d
E:\             483G   87G  396G  19% /mnt/e
tmpfs           382M   16K  382M   1% /run/user/1000
tmpfs           382M   16K  382M   1% /run/user/0
root@SomuMH:/var/log/sys_monitoring# cat disk_usage1.log
96K     /home/shiremath
root@SomuMH:/var/log/sys_monitoring# top
top - 10:45:02 up  4:50,  2 users,  load average: 0.00, 0.00, 0.00
Tasks:  39 total,   1 running,  38 sleeping,   0 stopped,   0 zombie
%Cpu(s):   0.0/0.0     0[                                                                                                    ]
MiB Mem :   3816.0 total,   3236.5 free,    583.7 used,    211.1 buff/cache
MiB Swap:   1024.0 total,   1024.0 free,      0.0 used.   3232.3 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
      1 root      20   0   21832  12968   9468 S   0.0   0.3   0:00.84 systemd
      2 root      20   0    2776   1924   1796 S   0.0   0.0   0:00.01 init-systemd(Ub
      8 root      20   0    2776    132    132 S   0.0   0.0   0:00.01 init
     59 root      19  -1   50424  16460  15332 S   0.0   0.4   0:00.26 systemd-journal
    106 root      20   0   23968   6220   5068 S   0.0   0.2   0:00.26 systemd-udevd
    127 systemd+  20   0   21452  12040   9844 S   0.0   0.3   0:00.22 systemd-resolve
    132 systemd+  20   0   91020   6576   5720 S   0.0   0.2   0:00.11 systemd-timesyn
    162 root      20   0    4236   2696   2464 S   0.0   0.1   0:00.01 cron
    163 message+  20   0    9592   5192   4640 S   0.0   0.1   0:00.11 dbus-daemon
    180 root      20   0   17976   8784   7736 S   0.0   0.2   0:00.12 systemd-logind
    186 root      20   0 1755840  16256   9664 S   0.0   0.4   0:00.21 wsl-pro-service
    194 root      20   0    3160   1196   1108 S   0.0   0.0   0:00.00 agetty
    198 syslog    20   0  222508   5080   4488 S   0.0   0.1   0:00.13 rsyslogd
    202 root      20   0    3116   1108   1020 S   0.0   0.0   0:00.01 agetty
    203 root      20   0   11156    968      0 S   0.0   0.0   0:00.01 nginx
    204 www-data  20   0   12880   4360   3104 S   0.0   0.1   0:00.01 nginx
    206 www-data  20   0   12880   4360   3104 S   0.0   0.1   0:00.01 nginx
    207 www-data  20   0   12880   4360   3104 S   0.0   0.1   0:00.00 nginx
    208 www-data  20   0   12880   4356   3100 S   0.0   0.1   0:00.00 nginx
    209 www-data  20   0   12880   4360   3104 S   0.0   0.1   0:00.00 nginx
    210 www-data  20   0   12880   4360   3104 S   0.0   0.1   0:00.00 nginx
    211 root      20   0  107028  22560  13224 S   0.0   0.6   0:00.25 unattended-upgr
    212 www-data  20   0   12880   4360   3104 S   0.0   0.1   0:00.01 nginx
    213 www-data  20   0   12880   4360   3104 S   0.0   0.1   0:00.00 nginx
    325 root      20   0    6684   4712   3936 S   0.0   0.1   0:00.01 login
    376 shirema+  20   0   20268  11320   9236 S   0.0   0.3   0:00.07 systemd
    377 shirema+  20   0   21148   1728      0 S   0.0   0.0   0:00.00 (sd-pam)
    388 shirema+  20   0    6072   4860   3356 S   0.0   0.1   0:00.01 bash
    401 root      20   0    2776    212     80 S   0.0   0.0   0:00.00 SessionLeader
    402 root      20   0    2776    212     80 S   0.0   0.0   0:00.12 Relay(409)
    409 shirema+  20   0    6072   5236   3516 S   0.0   0.1   0:00.05 bash
    643 polkitd   20   0  308164   7852   6988 S   0.0   0.2   0:00.10 polkitd
    703 root      20   0   14144   6804   5648 S   0.0   0.2   0:00.14 sudo
    704 root      20   0   14144   1192      0 S   0.0   0.0   0:00.00 sudo
root@SomuMH:/var/log/sys_monitoring# top -b -n 1 | head -20 >> /var/log/sys_monitoring/top_processes.log
root@SomuMH:/var/log/sys_monitoring# ls -ltr
total 12
-rw-r--r-- 1 root root  974 Jun 28 10:42 disk_usage.log
-rw-r--r-- 1 root root   20 Jun 28 10:43 disk_usage1.log
-rw-r--r-- 1 root root 1478 Jun 28 10:45 top_processes.log
root@SomuMH:/var/log/sys_monitoring# cat top_processes.log
top - 10:45:05 up  4:50,  2 users,  load average: 0.00, 0.00, 0.00
Tasks:  40 total,   1 running,  39 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.0 sy,  0.0 ni, 98.8 id,  1.2 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :   3816.0 total,   3233.0 free,    587.2 used,    211.1 buff/cache
MiB Swap:   1024.0 total,   1024.0 free,      0.0 used.   3228.8 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
   1962 root      20   0    9284   4932   3040 R  10.0   0.1   0:00.01 top
      1 root      20   0   21832  12968   9468 S   0.0   0.3   0:00.84 systemd
      2 root      20   0    2776   1924   1796 S   0.0   0.0   0:00.01 init-sy+
      8 root      20   0    2776    132    132 S   0.0   0.0   0:00.01 init
     59 root      19  -1   50424  16460  15332 S   0.0   0.4   0:00.26 systemd+
    106 root      20   0   23968   6220   5068 S   0.0   0.2   0:00.26 systemd+
    127 systemd+  20   0   21452  12040   9844 S   0.0   0.3   0:00.22 systemd+
    132 systemd+  20   0   91020   6576   5720 S   0.0   0.2   0:00.11 systemd+
    162 root      20   0    4236   2696   2464 S   0.0   0.1   0:00.01 cron
    163 message+  20   0    9592   5192   4640 S   0.0   0.1   0:00.11 dbus-da+
    180 root      20   0   17976   8784   7736 S   0.0   0.2   0:00.12 systemd+
    186 root      20   0 1755840  16256   9664 S   0.0   0.4   0:00.21 wsl-pro+
    194 root      20   0    3160   1196   1108 S   0.0   0.0   0:00.00 agetty
root@SomuMH:/var/log/sys_monitoring# ^C
root@SomuMH:/var/log/sys_monitoring# htop
root@SomuMH:/var/log/sys_monitoring# htop -b -n 1 >> /var/log/sys_monitoring/htop_snapshot.log
htop: invalid option -- 'b'
root@SomuMH:/var/log/sys_monitoring# htop -n 1 >> /var/log/sys_monitoring/htop_snapshot.log
root@SomuMH:/var/log/sys_monitoring# ls -ltr
total 20
-rw-r--r-- 1 root root  974 Jun 28 10:42 disk_usage.log
-rw-r--r-- 1 root root   20 Jun 28 10:43 disk_usage1.log
-rw-r--r-- 1 root root 1478 Jun 28 10:45 top_processes.log
-rw-r--r-- 1 root root 7627 Jun 28 10:45 htop_snapshot.log
root@SomuMH:/var/log/sys_monitoring# cat htop_snapshot.log

    0[                                                                  0.0%]   4[                                                                   0.0%]
    1[                                                                  0.0%]   5[                                                                   0.0%]
    2[                                                                  0.0%]   6[|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||100.0%]
    3[                                                                  0.0%]   7[                                                                   0.0%]
  Mem[|||||||||||||                                               375M/3.73G] Tasks: 39, 17 thr, 0 kthr; 1 running
  Swp[                                                              0K/1.00G] Load average: 0.00 0.00 0.00
                                                                              Uptime: 04:51:12

  [Main] [I/O]
    PID USER       PRI  NI  VIRT   RES   SHR S  CPU%▽MEM%   TIME+  Command
      1 root        20   0 21832 12968  9468 S   0.0  0.3  0:00.84 /sbin/init
      2 root        20   0  2776  1924  1796 S   0.0  0.0  0:00.01 /init
      8 root        20   0  2776   132   132 S   0.0  0.0  0:00.00 plan9 --control-socket 7 --log-level 4 --server-fd 8 --pipe-fd 10 --log-truncate
      9 root        20   0  2776   132   132 S   0.0  0.0  0:00.00 plan9 --control-socket 7 --log-level 4 --server-fd 8 --pipe-fd 10 --log-truncate
     10 root        20   0  2776  1924  1796 S   0.0  0.0  0:00.00 /init
     59 root        19  -1 50424 16460 15332 S   0.0  0.4  0:00.25 /usr/lib/systemd/systemd-journald
    106 root        20   0 23968  6220  5068 S   0.0  0.2  0:00.26 /usr/lib/systemd/systemd-udevd
    127 systemd-re  20   0 21452 12040  9844 S   0.0  0.3  0:00.22 /usr/lib/systemd/systemd-resolved
    132 systemd-ti  20   0 91020  6576  5720 S   0.0  0.2  0:00.10 /usr/lib/systemd/systemd-timesyncd
    156 systemd-ti  20   0 91020  6576  5720 S   0.0  0.2  0:00.00 /usr/lib/systemd/systemd-timesyncd
    162 root        20   0  4236  2696  2464 S   0.0  0.1  0:00.01 /usr/sbin/cron -f -P
    163 messagebus  20   0  9592  5192  4640 S   0.0  0.1  0:00.11 @dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation --sysl    180 root        20   0 17976  8784  7736 S   0.0  0.2  0:00.12 /usr/lib/systemd/systemd-logind
    186 root        20   0 1714M 16256  9664 S   0.0  0.4  0:00.12 /usr/libexec/wsl-pro-service -vv
    194 root        20   0  3160  1196  1108 S   0.0  0.0  0:00.00 /sbin/agetty -o -p -- \u --noclear --keep-baud - 115200,38400,9600 vt220
    198 syslog      20   0  217M  5080  4488 S   0.0  0.1  0:00.08 /usr/sbin/rsyslogd -n -iNONE
    202 root        20   0  3116  1108  1020 S   0.0  0.0  0:00.01 /sbin/agetty -o -p -- \u --noclear - linux
    203 root        20   0 11156   968     0 S   0.0  0.0  0:00.01 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
    204 www-data    20   0 12880  4360  3104 S   0.0  0.1  0:00.01 nginx: worker process
    206 www-data    20   0 12880  4360  3104 S   0.0  0.1  0:00.01 nginx: worker process
    207 www-data    20   0 12880  4360  3104 S   0.0  0.1  0:00.00 nginx: worker process
    208 www-data    20   0 12880  4356  3100 S   0.0  0.1  0:00.00 nginx: worker process
    209 www-data    20   0 12880  4360  3104 S   0.0  0.1  0:00.00 nginx: worker process
    210 www-data    20   0 12880  4360  3104 S   0.0  0.1  0:00.00 nginx: worker process
    211 root        20   0  104M 22560 13224 S   0.0  0.6  0:00.25 /usr/bin/python3 /usr/share/unattended-upgrades/unattended-upgrade-shutdown --wait-for-si    212 www-data    20   0 12880  4360  3104 S   0.0  0.1  0:00.01 nginx: worker process
    213 www-data    20   0 12880  4360  3104 S   0.0  0.1  0:00.00 nginx: worker process
    231 syslog      20   0  217M  5080  4488 S   0.0  0.1  0:00.01 /usr/sbin/rsyslogd -n -iNONE
    232 syslog      20   0  217M  5080  4488 S   0.0  0.1  0:00.01 /usr/sbin/rsyslogd -n -iNONE
root@SomuMH:/var/log/sys_monitoring# ^C
root@SomuMH:/var/log/sys_monitoring# ^C
root@SomuMH:/var/log/sys_monitoring# ^C
root@SomuMH:/var/log/sys_monitoring# ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem | head -n 15 >> /var/log/sysmon/top_processes.log
-bash: /var/log/sysmon/top_processes.log: No such file or directory
root@SomuMH:/var/log/sys_monitoring# crontab -e
no crontab for root - using an empty one

Select an editor.  To change later, run 'select-editor'.
  1. /bin/nano        <---- easiest
  2. /usr/bin/vim.basic
  3. /usr/bin/vim.tiny
  4. /bin/ed

Choose 1-4 [1]: 2
crontab: installing new crontab
root@SomuMH:/var/log/sys_monitoring# cat crontab
cat: crontab: No such file or directory
root@SomuMH:/var/log/sys_monitoring# ls -ltr
total 20
-rw-r--r-- 1 root root  974 Jun 28 10:42 disk_usage.log
-rw-r--r-- 1 root root   20 Jun 28 10:43 disk_usage1.log
-rw-r--r-- 1 root root 1478 Jun 28 10:45 top_processes.log
-rw-r--r-- 1 root root 7627 Jun 28 10:45 htop_snapshot.log
root@SomuMH:/var/log/sys_monitoring# cd /usr
root@SomuMH:/usr# ls -ltr
total 76
drwxr-xr-x   2 root root  4096 Apr 22  2024 src
drwxr-xr-x   2 root root  4096 Apr 22  2024 games
drwxr-xr-x  10 root root  4096 Feb 15 08:09 local
drwxr-xr-x   2 root root  4096 Feb 15 08:10 lib64
drwxr-xr-x   4 root root  4096 Feb 15 08:10 include
drwxr-xr-x   7 root root  4096 Feb 15 08:10 libexec
drwxr-xr-x  57 root root  4096 Jun 28 04:56 lib
drwxr-xr-x 112 root root  4096 Jun 28 06:57 share
drwxr-xr-x   2 root root 12288 Jun 28 06:57 sbin
drwxr-xr-x   2 root root 32768 Jun 28 10:23 bin
root@SomuMH:/usr# cd local
root@SomuMH:/usr/local# cd bin
root@SomuMH:/usr/local/bin# ls -ltr
total 0
root@SomuMH:/usr/local/bin# vi monitor.sh
root@SomuMH:/usr/local/bin# cat monitor.sh
#!/bin/bash
mkdir -p /var/log/sysmon
date >> /var/log/sysmon/system_report.log
echo "Top Processes:" >> /var/log/sysmon/system_report.log
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem | head -n 10 >> /var/log/sysmon/system_report.log
echo "Disk Usage:" >> /var/log/sysmon/system_report.log
df -h >> /var/log/sysmon/system_report.log
echo "----" >> /var/log/sysmon/system_report.log
root@SomuMH:/usr/local/bin# chmod +x /usr/local/bin/monitor.sh
root@SomuMH:/usr/local/bin# ls -ltr
total 4
-rwxr-xr-x 1 root root 379 Jun 28 10:58 monitor.sh
root@SomuMH:/usr/local/bin# vi #!/bin/bash
LOG_DIR="/var/log/sys_monitor"
mkdir -p $LOG_DIR

echo "==== Disk Usage Summary - $(date) ====" >> $LOG_DIR/disk_usage.log
df -h >> $LOG_DIR/disk_usage.log

echo -e "\n---- Top 5 Space-Consuming Directories (/) ----" >> $LOG_DIR/disk_usage.log
du -ah / | sort -rh | head -n 5 >> $LOG_DIR/disk_usage.log
echo -e "\n" >> $LOG_DIR/disk_usage.log
^C
root@SomuMH:/usr/local/bin# ^C
root@SomuMH:/usr/local/bin# vi diskmonitor.sh
root@SomuMH:/usr/local/bin# chmod +x disk_monitor.sh
chmod: cannot access 'disk_monitor.sh': No such file or directory
root@SomuMH:/usr/local/bin# ls -ltr
total 8
-rwxr-xr-x 1 root root 379 Jun 28 10:58 monitor.sh
-rw-r--r-- 1 root root 356 Jun 28 10:59 diskmonitor.sh
root@SomuMH:/usr/local/bin# chmod 755 diskmonitor.sh
root@SomuMH:/usr/local/bin# ls -ltr
total 8
-rwxr-xr-x 1 root root 379 Jun 28 10:58 monitor.sh
-rwxr-xr-x 1 root root 356 Jun 28 10:59 diskmonitor.sh
root@SomuMH:/usr/local/bin# vi processmonitor.sh
root@SomuMH:/usr/local/bin# cat
^C
root@SomuMH:/usr/local/bin# cat processmonitor.sh
#!/bin/bash
LOG_DIR="/var/log/sys_monitor"
mkdir -p $LOG_DIR

echo "==== High CPU and Memory Usage - $(date) ====" >> $LOG_DIR/process_monitor.log
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu | head -n 10 >> $LOG_DIR/process_monitor.log
echo -e "\n" >> $LOG_DIR/process_monitor.log

root@SomuMH:/usr/local/bin# chmod 755 processmonitor.sh
root@SomuMH:/usr/local/bin# crontab -e
crontab: installing new crontab
root@SomuMH:/usr/local/bin#


==============================================================================================================================================
==============================================================================================================================================
task 2

Task 2: User Management and Access Control
Objective: Set up user accounts and configure secure access controls for the new developers.
Scenario:
Two new developers, Sarah and Mike, require system access.
Each developer needs an isolated working directory to maintain security and confidentiality.
Security policies must ensure proper password management and access restrictions.
Requirements:
Create user accounts for Sarah and Mike with secure passwords.
Set up dedicated directories: 
Sarah: /home/Sarah/workspace
Mike: /home/mike/workspace
Ensure only the respective users can access their directories using appropriate permissions.
Implement a password policy to enforce expiration and complexity (e.g., passwords expire every 30 days).

Ans 

root@SomuMH:~# whoami
root
root@SomuMH:~# pwd
/root
root@SomuMH:~# sudo useradd -m Sarah
root@SomuMH:~# sudo useradd -m mike
root@SomuMH:~# pwd
/root
root@SomuMH:~# ls -ltr
total 0
root@SomuMH:~# sudo passwd Sarah
New password:
Retype new password:
passwd: password updated successfully
root@SomuMH:~# sudo passwd mike
New password:
Retype new password:
passwd: password updated successfully
root@SomuMH:~# pwd
/root
root@SomuMH:~# ls -ltr
total 0
root@SomuMH:~# mkdir -p /home/Sarah/workspace
root@SomuMH:~# mkdir -p /home/mike/workspace
root@SomuMH:~# ls -ltr
total 0
root@SomuMH:~# chown Sarah:Sarah /home/Sarah/workspace
root@SomuMH:~# chown mike:mike /home/mike/workspace
root@SomuMH:~# chmod 700 /home/Sarah/workspace
root@SomuMH:~# chmod 700 /home/mike/workspace
root@SomuMH:~# ls -ltr
total 0
root@SomuMH:~# cd /home
root@SomuMH:/home# ls -ltr
total 12
drwxr-x--- 7 shiremath shiremath 4096 Jun 28 06:32 shiremath
drwxr-x--- 3 Sarah     Sarah     4096 Jun 28 11:08 Sarah
drwxr-x--- 3 mike      mike      4096 Jun 28 11:08 mike
root@SomuMH:/home# sudo apt-get install libpam-pwquality
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  cracklib-runtime libcrack2 libpwquality-common libpwquality1 wamerican
The following NEW packages will be installed:
  cracklib-runtime libcrack2 libpam-pwquality libpwquality-common libpwquality1 wamerican
0 upgraded, 6 newly installed, 0 to remove and 37 not upgraded.
Need to get 446 kB of archives.
After this operation, 1932 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://archive.ubuntu.com/ubuntu noble/main amd64 libcrack2 amd64 2.9.6-5.1build2 [29.0 kB]
Get:2 http://archive.ubuntu.com/ubuntu noble/main amd64 cracklib-runtime amd64 2.9.6-5.1build2 [147 kB]
Get:3 http://archive.ubuntu.com/ubuntu noble/main amd64 libpwquality-common all 1.4.5-3build1 [7748 B]
Get:4 http://archive.ubuntu.com/ubuntu noble/main amd64 libpwquality1 amd64 1.4.5-3build1 [13.5 kB]
Get:5 http://archive.ubuntu.com/ubuntu noble/main amd64 libpam-pwquality amd64 1.4.5-3build1 [11.7 kB]
Get:6 http://archive.ubuntu.com/ubuntu noble/main amd64 wamerican all 2020.12.07-2 [236 kB]
Fetched 446 kB in 3s (163 kB/s)
Preconfiguring packages ...
Selecting previously unselected package libcrack2:amd64.
(Reading database ... 41628 files and directories currently installed.)
Preparing to unpack .../0-libcrack2_2.9.6-5.1build2_amd64.deb ...
Unpacking libcrack2:amd64 (2.9.6-5.1build2) ...
Selecting previously unselected package cracklib-runtime.
Preparing to unpack .../1-cracklib-runtime_2.9.6-5.1build2_amd64.deb ...
Unpacking cracklib-runtime (2.9.6-5.1build2) ...
Selecting previously unselected package libpwquality-common.
Preparing to unpack .../2-libpwquality-common_1.4.5-3build1_all.deb ...
Unpacking libpwquality-common (1.4.5-3build1) ...
Selecting previously unselected package libpwquality1:amd64.
Preparing to unpack .../3-libpwquality1_1.4.5-3build1_amd64.deb ...
Unpacking libpwquality1:amd64 (1.4.5-3build1) ...
Selecting previously unselected package libpam-pwquality:amd64.
Preparing to unpack .../4-libpam-pwquality_1.4.5-3build1_amd64.deb ...
Unpacking libpam-pwquality:amd64 (1.4.5-3build1) ...
Selecting previously unselected package wamerican.
Preparing to unpack .../5-wamerican_2020.12.07-2_all.deb ...
Unpacking wamerican (2020.12.07-2) ...
Setting up libpwquality-common (1.4.5-3build1) ...
Setting up wamerican (2020.12.07-2) ...
Setting up libcrack2:amd64 (2.9.6-5.1build2) ...
Setting up cracklib-runtime (2.9.6-5.1build2) ...
Setting up libpwquality1:amd64 (1.4.5-3build1) ...
Setting up libpam-pwquality:amd64 (1.4.5-3build1) ...
Processing triggers for libc-bin (2.39-0ubuntu8.4) ...
Processing triggers for man-db (2.12.0-4build2) ...
root@SomuMH:/home# cd /etc
root@SomuMH:/etc# ls -ltr
total 824
-rw-r--r-- 1 root root         45 Jan 24  2020 bash_completion
-rw-r--r-- 1 root root      12813 Mar 27  2021 services
-rw-r--r-- 1 root root         34 Aug  2  2022 ld.so.conf
-rw-r--r-- 1 root root        367 Aug  2  2022 bindresvport.blacklist
-rw-r--r-- 1 root root        552 Oct 13  2022 pam.conf
-rw-r--r-- 1 root root       3144 Oct 17  2022 protocols
-rw-r--r-- 1 root root        911 Oct 17  2022 rpc
-rw-r--r-- 1 root root       1853 Oct 17  2022 ethertypes
-rw-r--r-- 1 root root        460 Jan 20  2023 zsh_command_not_found
-rw-r--r-- 1 root root       1260 Jan 27  2023 ucf.conf
-rw-r--r-- 1 root root      11424 May 23  2023 nanorc
-rw-r--r-- 1 root root       1706 Jul  5  2023 deluser.conf
-rw-r--r-- 1 root root       3444 Jul  5  2023 adduser.conf
-rw-r--r-- 1 root root      75113 Jul 12  2023 mime.types
-r--r----- 1 root root       1800 Jan 29  2024 sudoers
-rw-r--r-- 1 root root       2584 Jan 31  2024 gai.conf
-rw-r--r-- 1 root root      12345 Feb 22  2024 login.defs
lrwxrwxrwx 1 root root         23 Feb 26  2024 vtrgb -> /etc/alternatives/vtrgb
-rw-r--r-- 1 root root       1213 Mar 22  2024 rsyslog.conf
-rw-r--r-- 1 root root       2209 Mar 24  2024 sysctl.conf
-rw-r--r-- 1 root root       2996 Mar 30  2024 locale.alias
-rw-r--r-- 1 root root       1136 Mar 31  2024 crontab
-rw-r--r-- 1 root root        191 Mar 31  2024 libaudit.conf
-rw-r--r-- 1 root root        767 Mar 31  2024 netconfig
-rw-r--r-- 1 root root      10593 Mar 31  2024 sensors3.conf
-rw-r--r-- 1 root root        111 Mar 31  2024 magic.mime
-rw-r--r-- 1 root root        111 Mar 31  2024 magic
-rw-r--r-- 1 root root       1875 Mar 31  2024 inputrc
-rw-r--r-- 1 root root       2319 Mar 31  2024 bash.bashrc
-rw-r--r-- 1 root root       1429 Mar 31  2024 dhcpcd.conf
-rw-r--r-- 1 root root        744 Apr  8  2024 mke2fs.conf
-rw-r--r-- 1 root root        685 Apr  8  2024 e2scrub.conf
-rw-r--r-- 1 root root       5230 Apr  8  2024 manpath.config
-rw-r--r-- 1 root root       9804 Apr  8  2024 sudo_logsrvd.conf
-rw-r--r-- 1 root root       4343 Apr  8  2024 sudo.conf
-rw-r--r-- 1 root root        681 Apr  8  2024 xattr.conf
-rw-r--r-- 1 root root        694 Apr  8  2024 fuse.conf
-rw-r--r-- 1 root root        586 Apr  8  2024 logrotate.conf
lrwxrwxrwx 1 root root         13 Apr  8  2024 rmt -> /usr/sbin/rmt
-rw-r--r-- 1 root root       2967 Apr 12  2024 debconf.conf
drwxr-xr-x 2 root root       4096 Apr 18  2024 netplan
drwxr-xr-x 2 root root       4096 Apr 19  2024 tmpfiles.d
drwx------ 2 root root       4096 Apr 19  2024 credstore.encrypted
drwx------ 2 root root       4096 Apr 19  2024 credstore
drwxr-xr-x 2 root root       4096 Apr 19  2024 binfmt.d
-rw-r--r-- 1 root root        582 Apr 22  2024 profile
-rw-r--r-- 1 root root         91 Apr 22  2024 networks
-rw-r--r-- 1 root root        267 Apr 22  2024 legal
-rw-r--r-- 1 root root         92 Apr 22  2024 host.conf
-rw-r--r-- 1 root root         11 Apr 22  2024 debian_version
-rw-r--r-- 1 root root       4942 Jun 19  2024 wgetrc
-rw-r--r-- 1 root root       3986 Aug  7  2024 gprofng.rc
lrwxrwxrwx 1 root root         21 Feb  5 16:08 os-release -> ../usr/lib/os-release
-rw-r--r-- 1 root root        104 Feb  5 16:08 lsb-release
-rw-r--r-- 1 root root         19 Feb  5 16:08 issue.net
-rw-r--r-- 1 root root         26 Feb  5 16:08 issue
-rw-r--r-- 1 root root         37 Feb 15 08:09 fstab
drwxr-xr-x 2 root root       4096 Feb 15 08:09 opt
drwxr-xr-x 2 root root       4096 Feb 15 08:09 selinux
drwxr-xr-x 2 root root       4096 Feb 15 08:09 terminfo
drwxr-xr-x 2 root root       4096 Feb 15 08:09 skel
-rw-r--r-- 1 root root        106 Feb 15 08:09 environment
lrwxrwxrwx 1 root root         16 Feb 15 08:09 vconsole.conf -> default/keyboard
lrwxrwxrwx 1 root root         19 Feb 15 08:09 mtab -> ../proc/self/mounts
drwxr-xr-x 2 root root       4096 Feb 15 08:09 cron.hourly
drwxr-xr-x 2 root root       4096 Feb 15 08:09 cron.monthly
drwxr-xr-x 2 root root       4096 Feb 15 08:09 cron.yearly
drwxr-xr-x 4 root root       4096 Feb 15 08:09 kernel
drwxr-xr-x 3 root root       4096 Feb 15 08:09 ca-certificates
drwxr-xr-x 4 root root       4096 Feb 15 08:09 dbus-1
drwxr-xr-x 3 root root       4096 Feb 15 08:09 gss
drwxr-xr-x 8 root root       4096 Feb 15 08:09 networkd-dispatcher
drwxr-xr-x 3 root root       4096 Feb 15 08:09 dhcp
drwxr-xr-x 2 root root       4096 Feb 15 08:09 supercat
-rw-r--r-- 1 root root        526 Feb 15 08:09 nsswitch.conf
-rw-r--r-- 1 root root        212 Feb 15 08:09 modules
lrwxrwxrwx 1 root root         27 Feb 15 08:09 localtime -> /usr/share/zoneinfo/Etc/UTC
drwxr-xr-x 2 root root       4096 Feb 15 08:09 sudoers.d
drwxr-xr-x 2 root root       4096 Feb 15 08:09 newt
-rw-r--r-- 1 root root       6288 Feb 15 08:09 ca-certificates.conf
drwxr-xr-x 4 root root       4096 Feb 15 08:09 iproute2
drwxr-xr-x 2 root root       4096 Feb 15 08:09 python3
drwxr-xr-x 2 root root       4096 Feb 15 08:09 console-setup
-rw-r--r-- 1 root root         13 Feb 15 08:09 locale.conf
drwxr-xr-x 4 root root       4096 Feb 15 08:10 dpkg
-rw-r--r-- 1 root root       9565 Feb 15 08:10 locale.gen
drwxr-xr-x 2 root root       4096 Feb 15 08:10 cron.d
drwxr-xr-x 2 root root       4096 Feb 15 08:10 depmod.d
drwxr-xr-x 2 root root       4096 Feb 15 08:10 modprobe.d
drwxr-xr-x 2 root root       4096 Feb 15 08:10 ubuntu-advantage
drwxr-xr-x 4 root root       4096 Feb 15 08:10 network
drwxr-xr-x 3 root root       4096 Feb 15 08:10 perl
drwxr-xr-x 3 root root       4096 Feb 15 08:10 dconf
drwxr-xr-x 5 root root       4096 Feb 15 08:10 xdg
drwxr-xr-x 5 root root       4096 Feb 15 08:10 vulkan
drwxr-xr-x 3 root root       4096 Feb 15 08:10 polkit-1
drwxr-xr-x 3 root root       4096 Feb 15 08:10 glvnd
drwxr-xr-x 3 root root       4096 Feb 15 08:10 pm
drwxr-xr-x 7 root root       4096 Feb 15 08:10 X11
drwxr-xr-x 2 root root       4096 Feb 15 08:10 sensors.d
drwxr-xr-x 2 root root       4096 Feb 15 08:10 ldap
drwxr-xr-x 2 root root       4096 Feb 15 08:10 apparmor
drwxr-xr-x 2 root root       4096 Feb 15 08:10 rcS.d
drwxr-xr-x 2 root root       4096 Feb 15 08:11 byobu
drwxr-xr-x 4 root root       4096 Feb 15 08:11 fonts
drwxr-xr-x 2 root root       4096 Feb 15 08:11 groff
drwxr-xr-x 2 root root       4096 Feb 15 08:11 sgml
drwxr-xr-x 5 root root       4096 Feb 15 08:11 cloud
drwxr-xr-x 2 root root       4096 Feb 15 08:11 profile.d
drwxr-xr-x 2 root root       4096 Feb 15 08:11 rsyslog.d
drwxr-xr-x 9 root root       4096 Feb 15 08:11 apparmor.d
drwxr-xr-x 2 root root       4096 Feb 15 08:11 cron.weekly
drwxr-xr-x 2 root root       4096 Feb 15 08:11 bash_completion.d
drwxrwxr-x 2 root landscape  4096 Feb 15 08:11 landscape
drwxr-xr-x 2 root root       4096 Feb 15 08:11 alternatives
drwxr-xr-x 3 root root       4096 Feb 15 08:11 update-manager
drwxr-xr-x 2 root root       4096 Feb 15 08:11 update-motd.d
-rw-r--r-- 1 root root        132 Feb 15 08:11 shells
drwxr-xr-x 2 root root       4096 Feb 15 08:11 gtk-3.0
drwxr-xr-x 2 root root       4096 Feb 15 08:11 environment.d
drwxr-xr-x 2 root root       4096 Feb 15 08:11 xml
drwxr-xr-x 2 root root       4096 Feb 15 08:11 PackageKit
-rw-r--r-- 1 root root        204 Feb 15 08:11 wsl-distribution.conf
drwxr-xr-x 8 root root       4096 Feb 15 08:11 apt
drwxr-xr-x 2 root root       4096 Jun  6 04:18 ld.so.conf.d
-r--r--r-- 1 root root         33 Jun 14 05:04 machine-id
-rw-r--r-- 1 root root         46 Jun 14 05:05 wsl.conf
drwxr-xr-x 2 root root       4096 Jun 15 06:18 sysctl.d
drwxr-xr-x 2 root root       4096 Jun 15 06:18 modules-load.d
drwxr-xr-x 4 root root       4096 Jun 15 06:19 udev
drwxr-xr-x 6 root root       4096 Jun 15 06:19 systemd
drwxr-xr-x 2 root root       4096 Jun 15 06:19 vim
drwxr-xr-x 3 root root       4096 Jun 15 06:19 apport
drwxr-xr-x 2 root root       4096 Jun 15 06:19 gnutls
drwxr-xr-x 4 root root       4096 Jun 15 06:19 ssl
drwxr-xr-x 3 root root       4096 Jun 15 06:19 ssh
-rw-r--r-- 1 root root          8 Jun 15 06:19 timezone
drwxr-xr-x 2 root root       4096 Jun 22 06:49 python3.12
drwxr-xr-x 3 root root       4096 Jun 28 04:56 ufw
drwxr-xr-x 8 root root       4096 Jun 28 04:56 apache2
drwxr-xr-x 2 root root       4096 Jun 28 04:56 cron.daily
drwxr-xr-x 2 root root       4096 Jun 28 06:57 init.d
drwxr-xr-x 2 root root       4096 Jun 28 06:57 default
drwxr-xr-x 2 root root       4096 Jun 28 06:57 logrotate.d
drwxr-xr-x 8 root root       4096 Jun 28 06:57 nginx
drwxr-xr-x 2 root root       4096 Jun 28 06:57 rc6.d
drwxr-xr-x 2 root root       4096 Jun 28 06:57 rc5.d
drwxr-xr-x 2 root root       4096 Jun 28 06:57 rc4.d
drwxr-xr-x 2 root root       4096 Jun 28 06:57 rc3.d
drwxr-xr-x 2 root root       4096 Jun 28 06:57 rc2.d
drwxr-xr-x 2 root root       4096 Jun 28 06:57 rc1.d
drwxr-xr-x 2 root root       4096 Jun 28 06:57 rc0.d
-rw-r--r-- 1 root root        398 Jun 28 10:20 hosts
-rw-r--r-- 1 root root          7 Jun 28 10:20 hostname
lrwxrwxrwx 1 root root         20 Jun 28 10:22 resolv.conf -> /mnt/wsl/resolv.conf
drwxr-xr-x 2 root root       4096 Jun 28 10:23 libnl-3
-rw-r--r-- 1 root root         78 Jun 28 11:07 subuid-
-rw-r--r-- 1 root root         78 Jun 28 11:07 subgid-
-rw-r----- 1 root shadow      884 Jun 28 11:07 shadow-
-rw-r--r-- 1 root root       1545 Jun 28 11:07 passwd-
-rw-r----- 1 root shadow      712 Jun 28 11:07 gshadow-
-rw-r--r-- 1 root root        842 Jun 28 11:07 group-
-rw-r--r-- 1 root root       1582 Jun 28 11:07 passwd
-rw-r--r-- 1 root root        855 Jun 28 11:07 group
-rw-r--r-- 1 root root         96 Jun 28 11:07 subuid
-rw-r--r-- 1 root root         96 Jun 28 11:07 subgid
-rw-r----- 1 root shadow      721 Jun 28 11:07 gshadow
-rw-r----- 1 root shadow     1054 Jun 28 11:07 shadow
drwxr-xr-x 4 root root       4096 Jun 28 11:09 logcheck
drwxr-xr-x 4 root root       4096 Jun 28 11:09 security
drwxr-xr-x 2 root root       4096 Jun 28 11:09 cracklib
drwxr-xr-x 2 root root       4096 Jun 28 11:09 pam.d
-rw-r--r-- 1 root root      18439 Jun 28 11:09 ld.so.cache
root@SomuMH:/etc# vi login.defs
root@SomuMH:/etc# cat login.defs
#
# /etc/login.defs - Configuration control definitions for the login package.
#
# Three items must be defined:  MAIL_DIR, ENV_SUPATH, and ENV_PATH.
# If unspecified, some arbitrary (and possibly incorrect) value will
# be assumed.  All other items are optional - if not specified then
# the described action or option will be inhibited.
#
# Comment lines (lines beginning with "#") and blank lines are ignored.
#
# Modified for Linux.  --marekm

# REQUIRED for useradd/userdel/usermod
#   Directory where mailboxes reside, _or_ name of file, relative to the
#   home directory.  If you _do_ define MAIL_DIR and MAIL_FILE,
#   MAIL_DIR takes precedence.
#
#   Essentially:
#      - MAIL_DIR defines the location of users mail spool files
#        (for mbox use) by appending the username to MAIL_DIR as defined
#        below.
#      - MAIL_FILE defines the location of the users mail spool files as the
#        fully-qualified filename obtained by prepending the user home
#        directory before $MAIL_FILE
#
# NOTE: This is no more used for setting up users MAIL environment variable
#       which is, starting from shadow 4.0.12-1 in Debian, entirely the
#       job of the pam_mail PAM modules
#       See default PAM configuration files provided for
#       login, su, etc.
#
# This is a temporary situation: setting these variables will soon
# move to /etc/default/useradd and the variables will then be
# no more supported
MAIL_DIR        /var/mail
#MAIL_FILE      .mail

#
# Enable logging and display of /var/log/faillog login failure info.
# This option conflicts with the pam_tally PAM module.
#
FAILLOG_ENAB            yes

#
# Enable display of unknown usernames when login failures are recorded.
#
# WARNING: Unknown usernames may become world readable.
# See #290803 and #298773 for details about how this could become a security
# concern
LOG_UNKFAIL_ENAB        no

#
# Enable logging of successful logins
#
LOG_OK_LOGINS           no

#
# Enable "syslog" logging of su activity - in addition to sulog file logging.
# SYSLOG_SG_ENAB does the same for newgrp and sg.
#
SYSLOG_SU_ENAB          yes
SYSLOG_SG_ENAB          yes

#
# If defined, all su activity is logged to this file.
#
#SULOG_FILE     /var/log/sulog

#
# If defined, file which maps tty line to TERM environment parameter.
# Each line of the file is in a format something like "vt100  tty01".
#
#TTYTYPE_FILE   /etc/ttytype

#
# If defined, login failures will be logged here in a utmp format
# last, when invoked as lastb, will read /var/log/btmp, so...
#
FTMP_FILE       /var/log/btmp

#
# If defined, the command name to display when running "su -".  For
# example, if this is defined as "su" then a "ps" will display the
# command is "-su".  If not defined, then "ps" would display the
# name of the shell actually being run, e.g. something like "-sh".
#
SU_NAME         su

#
# If defined, file which inhibits all the usual chatter during the login
# sequence.  If a full pathname, then hushed mode will be enabled if the
# user's name or shell are found in the file.  If not a full pathname, then
# hushed mode will be enabled if the file exists in the user's home directory.
#
HUSHLOGIN_FILE  .hushlogin
#HUSHLOGIN_FILE /etc/hushlogins

#
# *REQUIRED*  The default PATH settings, for superuser and normal users.
#
# (they are minimal, add the rest in the shell startup files)
ENV_SUPATH      PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
ENV_PATH        PATH=/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games

#
# Terminal permissions
#
#       TTYGROUP        Login tty will be assigned this group ownership.
#       TTYPERM         Login tty will be set to this permission.
#
# If you have a "write" program which is "setgid" to a special group
# which owns the terminals, define TTYGROUP to the group number and
# TTYPERM to 0620.  Otherwise leave TTYGROUP commented out and assign
# TTYPERM to either 622 or 600.
#
# In Debian /usr/bin/bsd-write or similar programs are setgid tty
# However, the default and recommended value for TTYPERM is still 0600
# to not allow anyone to write to anyone else console or terminal

# Users can still allow other people to write them by issuing
# the "mesg y" command.

TTYGROUP        tty
TTYPERM         0600

#
# Login configuration initializations:
#
#       ERASECHAR       Terminal ERASE character ('\010' = backspace).
#       KILLCHAR        Terminal KILL character ('\025' = CTRL/U).
#       UMASK           Default "umask" value.
#
# The ERASECHAR and KILLCHAR are used only on System V machines.
#
# UMASK is the default umask value for pam_umask and is used by
# useradd and newusers to set the mode of the new home directories.
# 022 is the "historical" value in Debian for UMASK
# 027, or even 077, could be considered better for privacy
# There is no One True Answer here : each sysadmin must make up his/her
# mind.
#
# If USERGROUPS_ENAB is set to "yes", that will modify this UMASK default value
# for private user groups, i. e. the uid is the same as gid, and username is
# the same as the primary group name: for these, the user permissions will be
# used as group permissions, e. g. 022 will become 002.
#
# Prefix these values with "0" to get octal, "0x" to get hexadecimal.
#
ERASECHAR       0177
KILLCHAR        025
UMASK           022

# HOME_MODE is used by useradd(8) and newusers(8) to set the mode for new
# home directories.
# If HOME_MODE is not set, the value of UMASK is used to create the mode.
HOME_MODE       0750

#
# Password aging controls:
#
#       PASS_MAX_DAYS   Maximum number of days a password may be used.
#       PASS_MIN_DAYS   Minimum number of days allowed between password changes.
#       PASS_WARN_AGE   Number of days warning given before a password expires.
#
PASS_MAX_DAYS   30
PASS_MIN_DAYS   1
PASS_WARN_AGE   7

#
# Min/max values for automatic uid selection in useradd
#
UID_MIN                  1000
UID_MAX                 60000
# System accounts
#SYS_UID_MIN              100
#SYS_UID_MAX              999
# Extra per user uids
SUB_UID_MIN                100000
SUB_UID_MAX             600100000
SUB_UID_COUNT               65536

#
# Min/max values for automatic gid selection in groupadd
#
GID_MIN                  1000
GID_MAX                 60000
# System accounts
#SYS_GID_MIN              100
#SYS_GID_MAX              999
# Extra per user group ids
SUB_GID_MIN                100000
SUB_GID_MAX             600100000
SUB_GID_COUNT               65536

#
# Max number of login retries if password is bad. This will most likely be
# overriden by PAM, since the default pam_unix module has it's own built
# in of 3 retries. However, this is a safe fallback in case you are using
# an authentication module that does not enforce PAM_MAXTRIES.
#
LOGIN_RETRIES           5

#
# Max time in seconds for login
#
LOGIN_TIMEOUT           60

#
# Which fields may be changed by regular users using chfn - use
# any combination of letters "frwh" (full name, room number, work
# phone, home phone).  If not defined, no changes are allowed.
# For backward compatibility, "yes" = "rwh" and "no" = "frwh".
#
CHFN_RESTRICT           rwh

#
# Should login be allowed if we can't cd to the home directory?
# Default is no.
#
DEFAULT_HOME    yes

#
# If defined, this command is run when removing a user.
# It should remove any at/cron/print jobs etc. owned by
# the user to be removed (passed as the first argument).
#
#USERDEL_CMD    /usr/sbin/userdel_local

#
# Enable setting of the umask group bits to be the same as owner bits
# (examples: 022 -> 002, 077 -> 007) for non-root users, if the uid is
# the same as gid, and username is the same as the primary group name.
#
# If set to yes, userdel will remove the user's group if it contains no
# more members, and useradd will create by default a group with the name
# of the user.
#
USERGROUPS_ENAB yes

#
# Instead of the real user shell, the program specified by this parameter
# will be launched, although its visible name (argv[0]) will be the shell's.
# The program may do whatever it wants (logging, additional authentification,
# banner, ...) before running the actual shell.
#
# FAKE_SHELL /bin/fakeshell

#
# If defined, either full pathname of a file containing device names or
# a ":" delimited list of device names.  Root logins will be allowed only
# upon these devices.
#
# This variable is used by login and su.
#
#CONSOLE        /etc/consoles
#CONSOLE        console:tty01:tty02:tty03:tty04

#
# List of groups to add to the user's supplementary group set
# when logging in on the console (as determined by the CONSOLE
# setting).  Default is none.
#
# Use with caution - it is possible for users to gain permanent
# access to these groups, even when not logged in on the console.
# How to do it is left as an exercise for the reader...
#
# This variable is used by login and su.
#
#CONSOLE_GROUPS         floppy:audio:cdrom

#
# If set to "yes", new passwords will be encrypted using the MD5-based
# algorithm compatible with the one used by recent releases of FreeBSD.
# It supports passwords of unlimited length and longer salt strings.
# Set to "no" if you need to copy encrypted passwords to other systems
# which don't understand the new algorithm.  Default is "no".
#
# This variable is deprecated. You should use ENCRYPT_METHOD.
#
#MD5_CRYPT_ENAB no

#
# If set to MD5, MD5-based algorithm will be used for encrypting password
# If set to SHA256, SHA256-based algorithm will be used for encrypting password
# If set to SHA512, SHA512-based algorithm will be used for encrypting password
# If set to BCRYPT, BCRYPT-based algorithm will be used for encrypting password
# If set to YESCRYPT, YESCRYPT-based algorithm will be used for encrypting password
# If set to DES, DES-based algorithm will be used for encrypting password (default)
# MD5 and DES should not be used for new hashes, see crypt(5) for recommendations.
# Overrides the MD5_CRYPT_ENAB option
#
# Note: It is recommended to use a value consistent with
# the PAM modules configuration.
#
ENCRYPT_METHOD SHA512

#
# Only works if ENCRYPT_METHOD is set to SHA256 or SHA512.
#
# Define the number of SHA rounds.
# With a lot of rounds, it is more difficult to brute-force the password.
# However, more CPU resources will be needed to authenticate users if
# this value is increased.
#
# If not specified, the libc will choose the default number of rounds (5000),
# which is orders of magnitude too low for modern hardware.
# The values must be within the 1000-999999999 range.
# If only one of the MIN or MAX values is set, then this value will be used.
# If MIN > MAX, the highest value will be used.
#
#SHA_CRYPT_MIN_ROUNDS 5000
#SHA_CRYPT_MAX_ROUNDS 5000

#
# Only works if ENCRYPT_METHOD is set to YESCRYPT.
#
# Define the YESCRYPT cost factor.
# With a higher cost factor, it is more difficult to brute-force the password.
# However, more CPU time and more memory will be needed to authenticate users
# if this value is increased.
#
# If not specified, a cost factor of 5 will be used.
# The value must be within the 1-11 range.
#
#YESCRYPT_COST_FACTOR 5

#
# The pwck(8) utility emits a warning for any system account with a home
# directory that does not exist.  Some system accounts intentionally do
# not have a home directory.  Such accounts may have this string as
# their home directory in /etc/passwd to avoid a spurious warning.
#
NONEXISTENT     /nonexistent

#
# Allow newuidmap and newgidmap when running under an alternative
# primary group.
#
#GRANT_AUX_GROUP_SUBIDS yes

#
# Select the HMAC cryptography algorithm.
# Used in pam_timestamp module to calculate the keyed-hash message
# authentication code.
#
# Note: It is recommended to check hmac(3) to see the possible algorithms
# that are available in your system.
#
#HMAC_CRYPTO_ALGO SHA512

################# OBSOLETED BY PAM ##############
#                                               #
# These options are now handled by PAM. Please  #
# edit the appropriate file in /etc/pam.d/ to   #
# enable the equivelants of them.
#
###############

#MOTD_FILE
#DIALUPS_CHECK_ENAB
#LASTLOG_ENAB
#MAIL_CHECK_ENAB
#OBSCURE_CHECKS_ENAB
#PORTTIME_CHECKS_ENAB
#SU_WHEEL_ONLY
#CRACKLIB_DICTPATH
#PASS_CHANGE_TRIES
#PASS_ALWAYS_WARN
#ENVIRON_FILE
#NOLOGINS_FILE
#ISSUE_FILE
#PASS_MIN_LEN
#PASS_MAX_LEN
#ULIMIT
#ENV_HZ
#CHFN_AUTH
#CHSH_AUTH
#FAIL_DELAY

################# OBSOLETED #######################
#                                                 #
# These options are no more handled by shadow.    #
#                                                 #
# Shadow utilities will display a warning if they #
# still appear.                                   #
#                                                 #
###################################################

# CLOSE_SESSIONS
# LOGIN_STRING
# NO_PASSWORD_CONSOLE
# QMAIL_DIR



root@SomuMH:/etc# chage -M 30 -m 1 -W 7 Sarah
root@SomuMH:/etc# chage -M 30 -m 1 -W 7 mike
root@SomuMH:/etc# ls -ltr
total 824
-rw-r--r-- 1 root root         45 Jan 24  2020 bash_completion
-rw-r--r-- 1 root root      12813 Mar 27  2021 services
-rw-r--r-- 1 root root         34 Aug  2  2022 ld.so.conf
-rw-r--r-- 1 root root        367 Aug  2  2022 bindresvport.blacklist
-rw-r--r-- 1 root root        552 Oct 13  2022 pam.conf
-rw-r--r-- 1 root root       3144 Oct 17  2022 protocols
-rw-r--r-- 1 root root        911 Oct 17  2022 rpc
-rw-r--r-- 1 root root       1853 Oct 17  2022 ethertypes
-rw-r--r-- 1 root root        460 Jan 20  2023 zsh_command_not_found
-rw-r--r-- 1 root root       1260 Jan 27  2023 ucf.conf
-rw-r--r-- 1 root root      11424 May 23  2023 nanorc
-rw-r--r-- 1 root root       1706 Jul  5  2023 deluser.conf
-rw-r--r-- 1 root root       3444 Jul  5  2023 adduser.conf
-rw-r--r-- 1 root root      75113 Jul 12  2023 mime.types
-r--r----- 1 root root       1800 Jan 29  2024 sudoers
-rw-r--r-- 1 root root       2584 Jan 31  2024 gai.conf
lrwxrwxrwx 1 root root         23 Feb 26  2024 vtrgb -> /etc/alternatives/vtrgb
-rw-r--r-- 1 root root       1213 Mar 22  2024 rsyslog.conf
-rw-r--r-- 1 root root       2209 Mar 24  2024 sysctl.conf
-rw-r--r-- 1 root root       2996 Mar 30  2024 locale.alias
-rw-r--r-- 1 root root       1136 Mar 31  2024 crontab
-rw-r--r-- 1 root root        191 Mar 31  2024 libaudit.conf
-rw-r--r-- 1 root root        767 Mar 31  2024 netconfig
-rw-r--r-- 1 root root      10593 Mar 31  2024 sensors3.conf
-rw-r--r-- 1 root root        111 Mar 31  2024 magic.mime
-rw-r--r-- 1 root root        111 Mar 31  2024 magic
-rw-r--r-- 1 root root       1875 Mar 31  2024 inputrc
-rw-r--r-- 1 root root       2319 Mar 31  2024 bash.bashrc
-rw-r--r-- 1 root root       1429 Mar 31  2024 dhcpcd.conf
-rw-r--r-- 1 root root        744 Apr  8  2024 mke2fs.conf
-rw-r--r-- 1 root root        685 Apr  8  2024 e2scrub.conf
-rw-r--r-- 1 root root       5230 Apr  8  2024 manpath.config
-rw-r--r-- 1 root root       9804 Apr  8  2024 sudo_logsrvd.conf
-rw-r--r-- 1 root root       4343 Apr  8  2024 sudo.conf
-rw-r--r-- 1 root root        681 Apr  8  2024 xattr.conf
-rw-r--r-- 1 root root        694 Apr  8  2024 fuse.conf
-rw-r--r-- 1 root root        586 Apr  8  2024 logrotate.conf
lrwxrwxrwx 1 root root         13 Apr  8  2024 rmt -> /usr/sbin/rmt
-rw-r--r-- 1 root root       2967 Apr 12  2024 debconf.conf
drwxr-xr-x 2 root root       4096 Apr 18  2024 netplan
drwxr-xr-x 2 root root       4096 Apr 19  2024 tmpfiles.d
drwx------ 2 root root       4096 Apr 19  2024 credstore.encrypted
drwx------ 2 root root       4096 Apr 19  2024 credstore
drwxr-xr-x 2 root root       4096 Apr 19  2024 binfmt.d
-rw-r--r-- 1 root root        582 Apr 22  2024 profile
-rw-r--r-- 1 root root         91 Apr 22  2024 networks
-rw-r--r-- 1 root root        267 Apr 22  2024 legal
-rw-r--r-- 1 root root         92 Apr 22  2024 host.conf
-rw-r--r-- 1 root root         11 Apr 22  2024 debian_version
-rw-r--r-- 1 root root       4942 Jun 19  2024 wgetrc
-rw-r--r-- 1 root root       3986 Aug  7  2024 gprofng.rc
lrwxrwxrwx 1 root root         21 Feb  5 16:08 os-release -> ../usr/lib/os-release
-rw-r--r-- 1 root root        104 Feb  5 16:08 lsb-release
-rw-r--r-- 1 root root         19 Feb  5 16:08 issue.net
-rw-r--r-- 1 root root         26 Feb  5 16:08 issue
-rw-r--r-- 1 root root         37 Feb 15 08:09 fstab
drwxr-xr-x 2 root root       4096 Feb 15 08:09 opt
drwxr-xr-x 2 root root       4096 Feb 15 08:09 selinux
drwxr-xr-x 2 root root       4096 Feb 15 08:09 terminfo
drwxr-xr-x 2 root root       4096 Feb 15 08:09 skel
-rw-r--r-- 1 root root        106 Feb 15 08:09 environment
lrwxrwxrwx 1 root root         16 Feb 15 08:09 vconsole.conf -> default/keyboard
lrwxrwxrwx 1 root root         19 Feb 15 08:09 mtab -> ../proc/self/mounts
drwxr-xr-x 2 root root       4096 Feb 15 08:09 cron.hourly
drwxr-xr-x 2 root root       4096 Feb 15 08:09 cron.monthly
drwxr-xr-x 2 root root       4096 Feb 15 08:09 cron.yearly
drwxr-xr-x 4 root root       4096 Feb 15 08:09 kernel
drwxr-xr-x 3 root root       4096 Feb 15 08:09 ca-certificates
drwxr-xr-x 4 root root       4096 Feb 15 08:09 dbus-1
drwxr-xr-x 3 root root       4096 Feb 15 08:09 gss
drwxr-xr-x 8 root root       4096 Feb 15 08:09 networkd-dispatcher
drwxr-xr-x 3 root root       4096 Feb 15 08:09 dhcp
drwxr-xr-x 2 root root       4096 Feb 15 08:09 supercat
-rw-r--r-- 1 root root        526 Feb 15 08:09 nsswitch.conf
-rw-r--r-- 1 root root        212 Feb 15 08:09 modules
lrwxrwxrwx 1 root root         27 Feb 15 08:09 localtime -> /usr/share/zoneinfo/Etc/UTC
drwxr-xr-x 2 root root       4096 Feb 15 08:09 sudoers.d
drwxr-xr-x 2 root root       4096 Feb 15 08:09 newt
-rw-r--r-- 1 root root       6288 Feb 15 08:09 ca-certificates.conf
drwxr-xr-x 4 root root       4096 Feb 15 08:09 iproute2
drwxr-xr-x 2 root root       4096 Feb 15 08:09 python3
drwxr-xr-x 2 root root       4096 Feb 15 08:09 console-setup
-rw-r--r-- 1 root root         13 Feb 15 08:09 locale.conf
drwxr-xr-x 4 root root       4096 Feb 15 08:10 dpkg
-rw-r--r-- 1 root root       9565 Feb 15 08:10 locale.gen
drwxr-xr-x 2 root root       4096 Feb 15 08:10 cron.d
drwxr-xr-x 2 root root       4096 Feb 15 08:10 depmod.d
drwxr-xr-x 2 root root       4096 Feb 15 08:10 modprobe.d
drwxr-xr-x 2 root root       4096 Feb 15 08:10 ubuntu-advantage
drwxr-xr-x 4 root root       4096 Feb 15 08:10 network
drwxr-xr-x 3 root root       4096 Feb 15 08:10 perl
drwxr-xr-x 3 root root       4096 Feb 15 08:10 dconf
drwxr-xr-x 5 root root       4096 Feb 15 08:10 xdg
drwxr-xr-x 5 root root       4096 Feb 15 08:10 vulkan
drwxr-xr-x 3 root root       4096 Feb 15 08:10 polkit-1
drwxr-xr-x 3 root root       4096 Feb 15 08:10 glvnd
drwxr-xr-x 3 root root       4096 Feb 15 08:10 pm
drwxr-xr-x 7 root root       4096 Feb 15 08:10 X11
drwxr-xr-x 2 root root       4096 Feb 15 08:10 sensors.d
drwxr-xr-x 2 root root       4096 Feb 15 08:10 ldap
drwxr-xr-x 2 root root       4096 Feb 15 08:10 apparmor
drwxr-xr-x 2 root root       4096 Feb 15 08:10 rcS.d
drwxr-xr-x 2 root root       4096 Feb 15 08:11 byobu
drwxr-xr-x 4 root root       4096 Feb 15 08:11 fonts
drwxr-xr-x 2 root root       4096 Feb 15 08:11 groff
drwxr-xr-x 2 root root       4096 Feb 15 08:11 sgml
drwxr-xr-x 5 root root       4096 Feb 15 08:11 cloud
drwxr-xr-x 2 root root       4096 Feb 15 08:11 profile.d
drwxr-xr-x 2 root root       4096 Feb 15 08:11 rsyslog.d
drwxr-xr-x 9 root root       4096 Feb 15 08:11 apparmor.d
drwxr-xr-x 2 root root       4096 Feb 15 08:11 cron.weekly
drwxr-xr-x 2 root root       4096 Feb 15 08:11 bash_completion.d
drwxrwxr-x 2 root landscape  4096 Feb 15 08:11 landscape
drwxr-xr-x 2 root root       4096 Feb 15 08:11 alternatives
drwxr-xr-x 3 root root       4096 Feb 15 08:11 update-manager
drwxr-xr-x 2 root root       4096 Feb 15 08:11 update-motd.d
-rw-r--r-- 1 root root        132 Feb 15 08:11 shells
drwxr-xr-x 2 root root       4096 Feb 15 08:11 gtk-3.0
drwxr-xr-x 2 root root       4096 Feb 15 08:11 environment.d
drwxr-xr-x 2 root root       4096 Feb 15 08:11 xml
drwxr-xr-x 2 root root       4096 Feb 15 08:11 PackageKit
-rw-r--r-- 1 root root        204 Feb 15 08:11 wsl-distribution.conf
drwxr-xr-x 8 root root       4096 Feb 15 08:11 apt
drwxr-xr-x 2 root root       4096 Jun  6 04:18 ld.so.conf.d
-r--r--r-- 1 root root         33 Jun 14 05:04 machine-id
-rw-r--r-- 1 root root         46 Jun 14 05:05 wsl.conf
drwxr-xr-x 2 root root       4096 Jun 15 06:18 sysctl.d
drwxr-xr-x 2 root root       4096 Jun 15 06:18 modules-load.d
drwxr-xr-x 4 root root       4096 Jun 15 06:19 udev
drwxr-xr-x 6 root root       4096 Jun 15 06:19 systemd
drwxr-xr-x 2 root root       4096 Jun 15 06:19 vim
drwxr-xr-x 3 root root       4096 Jun 15 06:19 apport
drwxr-xr-x 2 root root       4096 Jun 15 06:19 gnutls
drwxr-xr-x 4 root root       4096 Jun 15 06:19 ssl
drwxr-xr-x 3 root root       4096 Jun 15 06:19 ssh
-rw-r--r-- 1 root root          8 Jun 15 06:19 timezone
drwxr-xr-x 2 root root       4096 Jun 22 06:49 python3.12
drwxr-xr-x 3 root root       4096 Jun 28 04:56 ufw
drwxr-xr-x 8 root root       4096 Jun 28 04:56 apache2
drwxr-xr-x 2 root root       4096 Jun 28 04:56 cron.daily
drwxr-xr-x 2 root root       4096 Jun 28 06:57 init.d
drwxr-xr-x 2 root root       4096 Jun 28 06:57 default
drwxr-xr-x 2 root root       4096 Jun 28 06:57 logrotate.d
drwxr-xr-x 8 root root       4096 Jun 28 06:57 nginx
drwxr-xr-x 2 root root       4096 Jun 28 06:57 rc6.d
drwxr-xr-x 2 root root       4096 Jun 28 06:57 rc5.d
drwxr-xr-x 2 root root       4096 Jun 28 06:57 rc4.d
drwxr-xr-x 2 root root       4096 Jun 28 06:57 rc3.d
drwxr-xr-x 2 root root       4096 Jun 28 06:57 rc2.d
drwxr-xr-x 2 root root       4096 Jun 28 06:57 rc1.d
drwxr-xr-x 2 root root       4096 Jun 28 06:57 rc0.d
-rw-r--r-- 1 root root        398 Jun 28 10:20 hosts
-rw-r--r-- 1 root root          7 Jun 28 10:20 hostname
lrwxrwxrwx 1 root root         20 Jun 28 10:22 resolv.conf -> /mnt/wsl/resolv.conf
drwxr-xr-x 2 root root       4096 Jun 28 10:23 libnl-3
-rw-r--r-- 1 root root         78 Jun 28 11:07 subuid-
-rw-r--r-- 1 root root         78 Jun 28 11:07 subgid-
-rw-r--r-- 1 root root       1545 Jun 28 11:07 passwd-
-rw-r----- 1 root shadow      712 Jun 28 11:07 gshadow-
-rw-r--r-- 1 root root        842 Jun 28 11:07 group-
-rw-r--r-- 1 root root       1582 Jun 28 11:07 passwd
-rw-r--r-- 1 root root        855 Jun 28 11:07 group
-rw-r--r-- 1 root root         96 Jun 28 11:07 subuid
-rw-r--r-- 1 root root         96 Jun 28 11:07 subgid
-rw-r----- 1 root shadow      721 Jun 28 11:07 gshadow
drwxr-xr-x 4 root root       4096 Jun 28 11:09 logcheck
drwxr-xr-x 4 root root       4096 Jun 28 11:09 security
drwxr-xr-x 2 root root       4096 Jun 28 11:09 cracklib
drwxr-xr-x 2 root root       4096 Jun 28 11:09 pam.d
-rw-r--r-- 1 root root      18439 Jun 28 11:09 ld.so.cache
-rw-r--r-- 1 root root      12342 Jun 28 11:11 login.defs
-rw-r----- 1 root shadow     1051 Jun 28 11:11 shadow-
-rw-r----- 1 root shadow     1048 Jun 28 11:11 shadow
root@SomuMH:/etc# cd security
root@SomuMH:/etc/security# ls -ltr
total 60
-rw-r--r-- 1 root root 2425 Sep 18  2021 capability.conf
-rw-r--r-- 1 root root 2674 Apr  8  2024 pwquality.conf
-rw-r--r-- 1 root root 2179 Apr 10  2024 time.conf
-rw-r--r-- 1 root root  418 Apr 10  2024 sepermit.conf
-rw-r--r-- 1 root root  517 Apr 10  2024 pwhistory.conf
-rw-r--r-- 1 root root 2971 Apr 10  2024 pam_env.conf
drwxr-xr-x 2 root root 4096 Apr 10  2024 namespace.d
-rw-r--r-- 1 root root 1637 Apr 10  2024 namespace.conf
drwxr-xr-x 2 root root 4096 Apr 10  2024 limits.d
-rw-r--r-- 1 root root 2752 Apr 10  2024 limits.conf
-rw-r--r-- 1 root root 3635 Apr 10  2024 group.conf
-rw-r--r-- 1 root root 2234 Apr 10  2024 faillock.conf
-rw-r--r-- 1 root root 4564 Apr 10  2024 access.conf
-rw------- 1 root root    0 Feb 15 08:09 opasswd
-rwxr-xr-x 1 root root 1971 Jun 12 14:45 namespace.init
root@SomuMH:/etc/security# vi pwquality.conf
root@SomuMH:/etc/security# cat pwquality.conf
# Configuration for systemwide password quality limits
# Defaults:
#
# Number of characters in the new password that must not be present in the
# old password.
# difok = 1
#
# Minimum acceptable size for the new password (plus one if
# credits are not disabled which is the default). (See pam_cracklib manual.)
# Cannot be set to lower value than 6.
# minlen = 8
#
# The maximum credit for having digits in the new password. If less than 0
# it is the minimum number of digits in the new password.
# dcredit = 0
#
# The maximum credit for having uppercase characters in the new password.
# If less than 0 it is the minimum number of uppercase characters in the new
# password.
# ucredit = 0
#
# The maximum credit for having lowercase characters in the new password.
# If less than 0 it is the minimum number of lowercase characters in the new
# password.
# lcredit = 0
#
# The maximum credit for having other characters in the new password.
# If less than 0 it is the minimum number of other characters in the new
# password.
# ocredit = 0
#
# The minimum number of required classes of characters for the new
# password (digits, uppercase, lowercase, others).
# minclass = 0
#
# The maximum number of allowed consecutive same characters in the new password.
# The check is disabled if the value is 0.
# maxrepeat = 0
#
# The maximum number of allowed consecutive characters of the same class in the
# new password.
# The check is disabled if the value is 0.
# maxclassrepeat = 0
#
# Whether to check for the words from the passwd entry GECOS string of the user.
# The check is enabled if the value is not 0.
# gecoscheck = 0
#
# Whether to check for the words from the cracklib dictionary.
# The check is enabled if the value is not 0.
# dictcheck = 1
#
# Whether to check if it contains the user name in some form.
# The check is enabled if the value is not 0.
# usercheck = 1
#
# Length of substrings from the username to check for in the password
# The check is enabled if the value is greater than 0 and usercheck is enabled.
# usersubstr = 0
#
# Whether the check is enforced by the PAM module and possibly other
# applications.
# The new password is rejected if it fails the check and the value is not 0.
# enforcing = 1
#
# Path to the cracklib dictionaries. Default is to use the cracklib default.
# dictpath =
#
# Prompt user at most N times before returning with error. The default is 1.
# retry = 3
#
# Enforces pwquality checks on the root user password.
# Enabled if the option is present.
# enforce_for_root
#
# Skip testing the password quality for users that are not present in the
# /etc/passwd file.
# Enabled if the option is present.
# local_users_only
#
# minlen = 12
dcredit = -1
ucredit = -1
lcredit = -1
ocredit = -1
root@SomuMH:/etc/security# ls -ltr
total 60
-rw-r--r-- 1 root root 2425 Sep 18  2021 capability.conf
-rw-r--r-- 1 root root 2179 Apr 10  2024 time.conf
-rw-r--r-- 1 root root  418 Apr 10  2024 sepermit.conf
-rw-r--r-- 1 root root  517 Apr 10  2024 pwhistory.conf
-rw-r--r-- 1 root root 2971 Apr 10  2024 pam_env.conf
drwxr-xr-x 2 root root 4096 Apr 10  2024 namespace.d
-rw-r--r-- 1 root root 1637 Apr 10  2024 namespace.conf
drwxr-xr-x 2 root root 4096 Apr 10  2024 limits.d
-rw-r--r-- 1 root root 2752 Apr 10  2024 limits.conf
-rw-r--r-- 1 root root 3635 Apr 10  2024 group.conf
-rw-r--r-- 1 root root 2234 Apr 10  2024 faillock.conf
-rw-r--r-- 1 root root 4564 Apr 10  2024 access.conf
-rw------- 1 root root    0 Feb 15 08:09 opasswd
-rwxr-xr-x 1 root root 1971 Jun 12 14:45 namespace.init
-rw-r--r-- 1 root root 2742 Jun 28 11:13 pwquality.conf
root@SomuMH:/etc/security# cd ..
root@SomuMH:/etc# cd ..
root@SomuMH:/# pwd
/
root@SomuMH:/# users
root shiremath shiremath
root@SomuMH:/# list
Command 'list' not found, but there are 22 similar ones.
root@SomuMH:/#

=================================================================================================================================
===============================================================================================================================

Task 3: Backup Configuration for Web Servers
Objective: Configure automated backups for Sarah’s Apache server and Mike’s Nginx server to ensure data integrity and recovery.
Scenario:
Sarah is responsible for managing an Apache web server.
Mike is responsible for managing a Nginx web server. 
Both servers require regular backups to a secure location for disaster recovery.
Requirements:
Sarah and Mike need to automate backups for their respective web server configurations and document roots: 
Sarah: Backup the Apache configuration (/etc/httpd/) and document root (/var/www/html/).
Mike: Backup the Nginx configuration (/etc/nginx/) and document root (/usr/share/nginx/html/).
Schedule the backups to run every Tuesday at 12:00 AM using cron jobs.
Save the backups as compressed files in /backups/ with filenames including the server name and date (e.g., apache_backup_YYYY-MM-DD.tar.gz).
Verify the backup integrity after each run by listing the contents of the compressed file.
Expected Output:
Cron job configurations for Sarah and Mike.
Backup files are created in the /backups/ directory.
A verification log showing the backup integrity.

Ans:

root@SomuMH:/# pwd
/
root@SomuMH:/# whoami
root
root@SomuMH:/# /home
-bash: /home: Is a directory
root@SomuMH:/# cd /hom
-bash: cd: /hom: No such file or directory
root@SomuMH:/# cd /home
root@SomuMH:/home# ls -ltr
total 12
drwxr-x--- 7 shiremath shiremath 4096 Jun 28 06:32 shiremath
drwxr-x--- 3 Sarah     Sarah     4096 Jun 28 11:08 Sarah
drwxr-x--- 3 mike      mike      4096 Jun 28 11:08 mike
root@SomuMH:/home# cd Sarah
root@SomuMH:/home/Sarah# ls -ltr
total 4
drwx------ 2 Sarah Sarah 4096 Jun 28 11:08 workspace
root@SomuMH:/home/Sarah# vi apache_backup.sh
root@SomuMH:/home/Sarah# ls -ltr
total 8
drwx------ 2 Sarah Sarah 4096 Jun 28 11:08 workspace
-rw-r--r-- 1 root  root   407 Jun 28 11:35 apache_backup.sh
root@SomuMH:/home/Sarah# cat apache_backup.sh
#!/bin/bash
backup_dir="/backups"
filename="apache_backup_$(date +%F).tar.gz"
logfile="$backup_dir/apache_verify.log"

mkdir -p "$backup_dir"

tar -czvf "$backup_dir/$filename" /etc/httpd/ /var/www/html/ > "$logfile" 2>&1
echo "Backup created: $filename" >> "$logfile"

# Verify contents
echo "Verifying backup..." >> "$logfile"
tar -tzf "$backup_dir/$filename" >> "$logfile" 2>&1
echo "----" >> "$logfile"
root@SomuMH:/home/Sarah# chmod 755 apache_backup.sh
root@SomuMH:/home/Sarah# ls -ltr
total 8
drwx------ 2 Sarah Sarah 4096 Jun 28 11:08 workspace
-rwxr-xr-x 1 root  root   407 Jun 28 11:35 apache_backup.sh
root@SomuMH:/home/Sarah# cd ..
root@SomuMH:/home# ls -ltr
total 12
drwxr-x--- 7 shiremath shiremath 4096 Jun 28 06:32 shiremath
drwxr-x--- 3 mike      mike      4096 Jun 28 11:08 mike
drwxr-x--- 3 Sarah     Sarah     4096 Jun 28 11:35 Sarah
root@SomuMH:/home# cd #!/bin/bash
backup_dir="/backups"
filename="apache_backup_$(date +%F).tar.gz"
logfile="$backup_dir/apache_verify.log"

mkdir -p "$backup_dir"

tar -czvf "$backup_dir/$filename" /etc/httpd/ /var/www/html/ > "$logfile" 2>&1
echo "Backup created: $filename" >> "$logfile"

# Verify contents
echo "Verifying backup..." >> "$logfile"
tar -tzf "$backup_dir/$filename" >> "$logfile" 2>&1
echo "----" >> "$logfile"^C
root@SomuMH:/home# ^C
root@SomuMH:/home# ^C
root@SomuMH:/home# ^C
root@SomuMH:/home# ls -ltr
total 12
drwxr-x--- 7 shiremath shiremath 4096 Jun 28 06:32 shiremath
drwxr-x--- 3 mike      mike      4096 Jun 28 11:08 mike
drwxr-x--- 3 Sarah     Sarah     4096 Jun 28 11:35 Sarah
root@SomuMH:/home# cd mike
root@SomuMH:/home/mike# ls -ltr
total 4
drwx------ 2 mike mike 4096 Jun 28 11:08 workspace
root@SomuMH:/home/mike# vi nginx_backup.sh
root@SomuMH:/home/mike# chmod 755 nginx_backup.sh
root@SomuMH:/home/mike# ls -ltr
total 8
drwx------ 2 mike mike 4096 Jun 28 11:08 workspace
-rwxr-xr-x 1 root root  413 Jun 28 11:36 nginx_backup.sh
root@SomuMH:/home/mike# cat nginx_backup.sh
#!/bin/bash
backup_dir="/backups"
filename="nginx_backup_$(date +%F).tar.gz"
logfile="$backup_dir/nginx_verify.log"

mkdir -p "$backup_dir"

tar -czvf "$backup_dir/$filename" /etc/nginx/ /usr/share/nginx/html/ > "$logfile" 2>&1
echo "Backup created: $filename" >> "$logfile"

# Verify contents
echo "Verifying backup..." >> "$logfile"
tar -tzf "$backup_dir/$filename" >> "$logfile" 2>&1
echo "----" >> "$logfile"
root@SomuMH:/home/mike# ls -ltr
total 8
drwx------ 2 mike mike 4096 Jun 28 11:08 workspace
-rwxr-xr-x 1 root root  413 Jun 28 11:36 nginx_backup.sh
root@SomuMH:/home/mike# crontab -e
crontab: installing new crontab
root@SomuMH:/home/mike#
