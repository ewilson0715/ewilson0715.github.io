Coding Day 1
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

Install the latest PowerShell for new features and improvements! https://aka.ms/PSWindows

PS C:\WINDOWS\system32> ssh
usage: ssh [-46AaCfGgKkMNnqsTtVvXxYy] [-B bind_interface] [-b bind_address]
           [-c cipher_spec] [-D [bind_address:]port] [-E log_file]
           [-e escape_char] [-F configfile] [-I pkcs11] [-i identity_file]
           [-J destination] [-L address] [-l login_name] [-m mac_spec]
           [-O ctl_cmd] [-o option] [-P tag] [-p port] [-Q query_option]
           [-R address] [-S ctl_path] [-W host:port] [-w local_tun[:remote_tun]]
           destination [command [argument ...]]
PS C:\WINDOWS\system32> ssh -i C:\users\lenno\.ssh\[REDACTED] opc@157.151.194.68
The authenticity of host '157.151.194.68 (157.151.194.68)' can't be established.
ED25519 key fingerprint is SHA256:GUIXAW95IWJ4eBTk0qvKhmTgxL33CtVR++GMaRtubEs.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '157.151.194.68' (ED25519) to the list of known hosts.
[opc@LennoxsDomain ~]$ ls
[opc@LennoxsDomain ~]$ pwd
/home/opc

Coding Day 2
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

Install the latest PowerShell for new features and improvements! https://aka.ms/PSWindows

PS C:\WINDOWS\system32> C:\Users\lenno\.ssh\[REDACTED]
PS C:\WINDOWS\system32> ssh -i C:\users\lenno\.ssh\[REDACTED] opc@157.151.194.68
Last login: Wed Oct  8 01:13:20 2025 from 204.126.178.254
[opc@LennoxsDomain ~]$ pwd
/home/opc
[opc@LennoxsDomain ~]$ sudo dd if=/dev/zero
bs=        conv=      --help     if=        obs=       oflag=     skip=      --version
cbs=       count=     ibs=       iflag=     of=        seek=      status=
[opc@LennoxsDomain ~]$ sudo dd if=/dev/zero of=/swapfile bs=1024 count=1000000
1000000+0 records in
1000000+0 records out
1024000000 bytes (1.0 GB, 977 MiB) copied, 17.9565 s, 57.0 MB/s
[opc@LennoxsDomain ~]$ sudo mkswap /swapfile
mkswap: /swapfile: insecure permissions 0644, fix with: chmod 0600 /swapfile
Setting up swapspace version 1, size = 976.6 MiB (1023995904 bytes)
no label, UUID=cfedb714-800b-4cbd-8e4c-c2222f4f278b
[opc@LennoxsDomain ~]$ sudo chmod 0600 /swapfile
[opc@LennoxsDomain ~]$ /swapfile swap swap defaults 0 0
-bash: /swapfile: Permission denied
[opc@LennoxsDomain ~]$ client_loop: send disconnect: Connection reset
PS C:\WINDOWS\system32> more /etc/fstab
Get-Content : Cannot find path 'C:\etc\fstab' because it does not exist.
At line:7 char:9
+         Get-Content $file | more.com
+         ~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (C:\etc\fstab:String) [Get-Content], ItemNotFoundException
    + FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetContentCommand

Part 2:
PS C:\WINDOWS\system32> ssh -i C:\users\lenno\.ssh\[REDACTED] opc@157.151.194.68
Last login: Wed Oct  8 03:02:22 2025 from 204.126.178.254
[opc@LennoxsDomain ~]$ more /etc/fstab
#
# /etc/fstab
# Created by anaconda on Thu Jun 12 01:18:32 2025
#
# Accessible filesystems, by reference, are maintained under '/dev/disk/'.
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info.
#
# After editing this file, run 'systemctl daemon-reload' to update systemd
# units generated from this file.
#
/dev/mapper/ocivolume-root /                       xfs     defaults        0 0
UUID=dd88872e-0527-4193-8282-b8281f1ae6fd /boot                   xfs     defaults        0 0
UUID=AE3C-806E          /boot/efi               vfat    defaults,uid=0,gid=0,umask=077,shortname=winnt 0 2
/dev/mapper/ocivolume-oled /var/oled               xfs     defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults,nodev,nosuid,noexec      0 0
######################################
## ORACLE CLOUD INFRASTRUCTURE CUSTOMERS
##
## If you are adding an iSCSI remote block volume to this file you MUST
## include the '_netdev' mount option or your instance will become
## unavailable after the next reboot.
## SCSI device names are not stable across reboots; please use the device UUID instead of /dev path.
##
## Example:
## UUID="94c5aade-8bb1-4d55-ad0c-388bb8aa716a"   /data1    xfs       defaults,noatime,_netdev      0      2
##
## More information:
## https://docs.us-phoenix-1.oraclecloud.com/Content/Block/Tasks/connectingtoavolume.htm
/.swapfile      none    swap    sw      0       0
[opc@LennoxsDomain ~]$ edit /etc/fstab
-bash: edit: command not found
[opc@LennoxsDomain ~]$ vi /etc/fstab
[opc@LennoxsDomain ~]$ sudo vi /etc/fstab
[opc@LennoxsDomain ~]$ sudo dd if=/dev/zero of=/swapfile bs=1024 count=8000000
8000000+0 records in
8000000+0 records out
8192000000 bytes (8.2 GB, 7.6 GiB) copied, 157.821 s, 51.9 MB/s
[opc@LennoxsDomain ~]$ sudo mkswap /swapfile
Setting up swapspace version 1, size = 7.6 GiB (8191995904 bytes)
no label, UUID=88e5e344-a2fe-410c-8b8c-43f179ff7c66
[opc@LennoxsDomain ~]$ sudo chmod 0600 /swapfile
[opc@LennoxsDomain ~]$ sudo systemct1 daemon-reload
sudo: systemct1: command not found
[opc@LennoxsDomain ~]$ sudo systemctl daemon-reload
[opc@LennoxsDomain ~]$ sudo swapon /swapfile
[opc@LennoxsDomain ~]$ cat /proc/swaps
Filename                                Type            Size            Used            Priority
/.swapfile                              file            515068          143344          -2
/swapfile                               file            7999996         0               -3
[opc@LennoxsDomain ~]$ sudo free -h
               total        used        free      shared  buff/cache   available
Mem:           503Mi       223Mi        13Mi       2.0Mi       298Mi       280Mi
Swap:          8.1Gi       139Mi       8.0Gi
[opc@LennoxsDomain ~]$ sudo dnf update
Oracle Linux 9 BaseOS Latest (x86_64)                                                    30 MB/s |  88 MB     00:02
Oracle Linux 9 Application Stream Packages (x86_64)                                      30 MB/s |  70 MB     00:02
Oracle Linux 9 Addons (x86_64)                                                          1.4 MB/s | 733 kB     00:00
Oracle Linux 9 UEK Release 8 (x86_64)                                                    21 MB/s |  16 MB     00:00
Last metadata expiration check: 0:00:02 ago on Wed 08 Oct 2025 01:29:17 PM GMT.
Dependencies resolved.
========================================================================================================================
 Package                                Arch       Version                                  Repository             Size
========================================================================================================================
Installing:
 kernel                                 x86_64     5.14.0-570.51.1.0.1.el9_6                ol9_baseos_latest     1.8 M
 kernel-core                            x86_64     5.14.0-570.51.1.0.1.el9_6                ol9_baseos_latest      18 M
 kernel-modules                         x86_64     5.14.0-570.51.1.0.1.el9_6                ol9_baseos_latest      40 M
 kernel-modules-core                    x86_64     5.14.0-570.51.1.0.1.el9_6                ol9_baseos_latest      32 M
 kernel-uek                             x86_64     6.12.0-103.40.4.4.el9uek                 ol9_UEKR8             788 k
 kernel-uek-core                        x86_64     6.12.0-103.40.4.4.el9uek                 ol9_UEKR8              19 M
 kernel-uek-modules                     x86_64     6.12.0-103.40.4.4.el9uek                 ol9_UEKR8              31 M
 kernel-uek-modules-core                x86_64     6.12.0-103.40.4.4.el9uek                 ol9_UEKR8              37 M
 kernel-uek-modules-desktop             x86_64     6.12.0-103.40.4.4.el9uek                 ol9_UEKR8              20 M
 kernel-uek-modules-extra-netfilter     x86_64     6.12.0-103.40.4.4.el9uek                 ol9_UEKR8             1.6 M
 kernel-uek-modules-usb                 x86_64     6.12.0-103.40.4.4.el9uek                 ol9_UEKR8             1.7 M
 kernel-uek-modules-wireless            x86_64     6.12.0-103.40.4.4.el9uek                 ol9_UEKR8             8.6 M
Upgrading:
 NetworkManager                         x86_64     1:1.52.0-7.0.1.el9_6                     ol9_baseos_latest     2.4 M
 NetworkManager-config-server           noarch     1:1.52.0-7.0.1.el9_6                     ol9_baseos_latest      17 k
 NetworkManager-libnm                   x86_64     1:1.52.0-7.0.1.el9_6                     ol9_baseos_latest     1.9 M
 NetworkManager-team                    x86_64     1:1.52.0-7.0.1.el9_6                     ol9_baseos_latest      37 k
 NetworkManager-tui                     x86_64     1:1.52.0-7.0.1.el9_6                     ol9_baseos_latest     253 k
 gcc-toolset-14-gcc                     x86_64     14.2.1-8.el9_6                           ol9_appstream          47 M
 gcc-toolset-14-gcc-c++                 x86_64     14.2.1-8.el9_6                           ol9_appstream          15 M
 gcc-toolset-14-libstdc++-devel         x86_64     14.2.1-8.el9_6                           ol9_appstream         4.3 M
 gnutls                                 x86_64     3.8.3-6.el9_6.2                          ol9_baseos_latest     1.1 M
 gsettings-desktop-schemas              x86_64     40.0-7.el9_6                             ol9_baseos_latest     759 k
 irqbalance                             x86_64     2:1.9.4-2.0.1.el9_6.2                    ol9_baseos_latest      68 k
 iwl100-firmware                        noarch     999:39.31.5.1-999.44.el9                 ol9_baseos_latest     125 k
 iwl1000-firmware                       noarch     999:39.31.5.1-999.44.el9                 ol9_baseos_latest     126 k
 iwl105-firmware                        noarch     999:18.168.6.1-999.44.el9                ol9_baseos_latest     204 k
 iwl135-firmware                        noarch     999:18.168.6.1-999.44.el9                ol9_baseos_latest     213 k
 iwl2000-firmware                       noarch     999:18.168.6.1-999.44.el9                ol9_baseos_latest     206 k
 iwl2030-firmware                       noarch     999:18.168.6.1-999.44.el9                ol9_baseos_latest     215 k
 iwl3160-firmware                       noarch     999:25.30.13.0-999.44.el9                ol9_baseos_latest     482 k
 iwl5000-firmware                       noarch     999:8.83.5.1_1-999.44.el9                ol9_baseos_latest     123 k
 iwl5150-firmware                       noarch     999:8.24.2.2-999.44.el9                  ol9_baseos_latest     122 k
 iwl6000g2a-firmware                    noarch     999:18.168.6.1-999.44.el9                ol9_baseos_latest     190 k
 iwl6050-firmware                       noarch     999:41.28.5.1-999.44.el9                 ol9_baseos_latest     148 k
 iwl7260-firmware                       noarch     999:25.30.13.0-999.44.el9                ol9_baseos_latest      15 M
 iwlax2xx-firmware                      noarch     999:20250909-999.44.el9                  ol9_baseos_latest      85 M
 kernel-headers                         x86_64     5.14.0-570.51.1.0.1.el9_6                ol9_appstream         4.3 M
 kernel-tools                           x86_64     5.14.0-570.51.1.0.1.el9_6                ol9_baseos_latest     2.1 M
 kernel-tools-libs                      x86_64     5.14.0-570.51.1.0.1.el9_6                ol9_baseos_latest     1.8 M
 kexec-tools                            x86_64     2.0.31-1.0.1.el9                         ol9_baseos_latest     541 k
 kmod-kvdo                              x86_64     8.2.5.14-164.0.1.el9_6                   ol9_baseos_latest     330 k
 ksplice                                x86_64     2.0.8-1.el9                              ol9_ksplice            92 k
 ksplice-core0                          x86_64     2.0.8-1.el9                              ol9_ksplice           355 k
 ksplice-tools                          x86_64     2.0.8-1.el9                              ol9_ksplice           184 k
 libldb                                 x86_64     4.21.3-14.el9_6                          ol9_baseos_latest     192 k
 libsmbclient                           x86_64     4.21.3-14.el9_6                          ol9_baseos_latest      73 k
 libwbclient                            x86_64     4.21.3-14.el9_6                          ol9_baseos_latest      42 k
 linux-firmware                         noarch     999:20250909-999.44.git260ff424.el9      ol9_baseos_latest     583 M
 linux-firmware-core                    noarch     999:20250909-999.44.git260ff424.el9      ol9_baseos_latest     899 k
 linux-firmware-whence                  noarch     999:20250909-999.44.git260ff424.el9      ol9_baseos_latest      46 k
 microcode_ctl                          noarch     4:20250211-1.20250512.1.0.1.el9_6        ol9_baseos_latest      14 M
 perf                                   x86_64     5.14.0-570.51.1.0.1.el9_6                ol9_appstream         4.3 M
 python3-cryptography                   x86_64     36.0.1-5.el9_6                           ol9_appstream         1.5 M
 python3-perf                           x86_64     5.14.0-570.51.1.0.1.el9_6                ol9_baseos_latest     3.2 M
 python39-oci-sdk                       x86_64     2.160.3-1.el9                            ol9_oci_included       90 M
 samba-client-libs                      x86_64     4.21.3-14.el9_6                          ol9_baseos_latest     5.3 M
 samba-common                           noarch     4.21.3-14.el9_6                          ol9_baseos_latest     188 k
 samba-common-libs                      x86_64     4.21.3-14.el9_6                          ol9_baseos_latest     105 k
 sos                                    noarch     4.10.0-4.0.1.el9_6                       ol9_baseos_latest     2.3 M
 sudo                                   x86_64     1.9.5p2-10.el9_6.2                       ol9_baseos_latest     1.1 M
 systemd                                x86_64     252-51.0.4.el9_6.2                       ol9_baseos_latest     4.6 M
 systemd-libs                           x86_64     252-51.0.4.el9_6.2                       ol9_baseos_latest     682 k
 systemd-pam                            x86_64     252-51.0.4.el9_6.2                       ol9_baseos_latest     278 k
 systemd-rpm-macros                     noarch     252-51.0.4.el9_6.2                       ol9_baseos_latest      70 k
 systemd-udev                           x86_64     252-51.0.4.el9_6.2                       ol9_baseos_latest     2.2 M

Transaction Summary
========================================================================================================================
Install  12 Packages
Upgrade  53 Packages

Total download size: 1.1 G
Is this ok [y/N]: y
Downloading Packages:
(1/65): kernel-5.14.0-570.51.1.0.1.el9_6.x86_64.rpm                                     1.6 MB/s | 1.8 MB     00:01
(2/65): kernel-core-5.14.0-570.51.1.0.1.el9_6.x86_64.rpm                                5.9 MB/s |  18 MB     00:03
(3/65): kernel-uek-6.12.0-103.40.4.4.el9uek.x86_64.rpm                                  2.5 MB/s | 788 kB     00:00
(4/65): kernel-modules-5.14.0-570.51.1.0.1.el9_6.x86_64.rpm                             8.3 MB/s |  40 MB     00:04
(5/65): kernel-modules-core-5.14.0-570.51.1.0.1.el9_6.x86_64.rpm                        7.8 MB/s |  32 MB     00:04
(6/65): kernel-uek-core-6.12.0-103.40.4.4.el9uek.x86_64.rpm                             7.5 MB/s |  19 MB     00:02
(7/65): kernel-uek-modules-6.12.0-103.40.4.4.el9uek.x86_64.rpm                           10 MB/s |  31 MB     00:02
(8/65): kernel-uek-modules-desktop-6.12.0-103.40.4.4.el9uek.x86_64.rpm                  9.2 MB/s |  20 MB     00:02
(9/65): kernel-uek-modules-extra-netfilter-6.12.0-103.40.4.4.el9uek.x86_64.rpm          4.7 MB/s | 1.6 MB     00:00
(10/65): kernel-uek-modules-usb-6.12.0-103.40.4.4.el9uek.x86_64.rpm                     9.6 MB/s | 1.7 MB     00:00
(11/65): ksplice-2.0.8-1.el9.x86_64.rpm                                                 641 kB/s |  92 kB     00:00
(12/65): ksplice-core0-2.0.8-1.el9.x86_64.rpm                                           1.5 MB/s | 355 kB     00:00
(13/65): kernel-uek-modules-core-6.12.0-103.40.4.4.el9uek.x86_64.rpm                    9.7 MB/s |  37 MB     00:03
(14/65): ksplice-tools-2.0.8-1.el9.x86_64.rpm                                           392 kB/s | 184 kB     00:00
(15/65): NetworkManager-1.52.0-7.0.1.el9_6.x86_64.rpm                                   9.6 MB/s | 2.4 MB     00:00
(16/65): kernel-uek-modules-wireless-6.12.0-103.40.4.4.el9uek.x86_64.rpm                6.1 MB/s | 8.6 MB     00:01
(17/65): NetworkManager-config-server-1.52.0-7.0.1.el9_6.noarch.rpm                      82 kB/s |  17 kB     00:00
(18/65): NetworkManager-team-1.52.0-7.0.1.el9_6.x86_64.rpm                              651 kB/s |  37 kB     00:00
(19/65): NetworkManager-tui-1.52.0-7.0.1.el9_6.x86_64.rpm                               1.4 MB/s | 253 kB     00:00
(20/65): NetworkManager-libnm-1.52.0-7.0.1.el9_6.x86_64.rpm                             6.8 MB/s | 1.9 MB     00:00
(21/65): gsettings-desktop-schemas-40.0-7.el9_6.x86_64.rpm                              4.9 MB/s | 759 kB     00:00
(22/65): irqbalance-1.9.4-2.0.1.el9_6.2.x86_64.rpm                                      554 kB/s |  68 kB     00:00
(23/65): gnutls-3.8.3-6.el9_6.2.x86_64.rpm                                              3.0 MB/s | 1.1 MB     00:00
(24/65): iwl1000-firmware-39.31.5.1-999.44.el9.noarch.rpm                               967 kB/s | 126 kB     00:00
(25/65): iwl100-firmware-39.31.5.1-999.44.el9.noarch.rpm                                690 kB/s | 125 kB     00:00
(26/65): iwl135-firmware-18.168.6.1-999.44.el9.noarch.rpm                               1.0 MB/s | 213 kB     00:00
(27/65): iwl105-firmware-18.168.6.1-999.44.el9.noarch.rpm                               787 kB/s | 204 kB     00:00
(28/65): iwl2000-firmware-18.168.6.1-999.44.el9.noarch.rpm                              1.9 MB/s | 206 kB     00:00
(29/65): iwl2030-firmware-18.168.6.1-999.44.el9.noarch.rpm                              1.5 MB/s | 215 kB     00:00
(30/65): iwl5000-firmware-8.83.5.1_1-999.44.el9.noarch.rpm                              978 kB/s | 123 kB     00:00
(31/65): iwl3160-firmware-25.30.13.0-999.44.el9.noarch.rpm                              2.1 MB/s | 482 kB     00:00
(32/65): iwl5150-firmware-8.24.2.2-999.44.el9.noarch.rpm                                1.7 MB/s | 122 kB     00:00
(33/65): iwl6000g2a-firmware-18.168.6.1-999.44.el9.noarch.rpm                           1.1 MB/s | 190 kB     00:00
(34/65): iwl6050-firmware-41.28.5.1-999.44.el9.noarch.rpm                               428 kB/s | 148 kB     00:00
(35/65): iwl7260-firmware-25.30.13.0-999.44.el9.noarch.rpm                              5.9 MB/s |  15 MB     00:02
(36/65): kernel-tools-5.14.0-570.51.1.0.1.el9_6.x86_64.rpm                              8.4 MB/s | 2.1 MB     00:00
(37/65): kernel-tools-libs-5.14.0-570.51.1.0.1.el9_6.x86_64.rpm                         6.8 MB/s | 1.8 MB     00:00
(38/65): kexec-tools-2.0.31-1.0.1.el9.x86_64.rpm                                        1.0 MB/s | 541 kB     00:00
(39/65): kmod-kvdo-8.2.5.14-164.0.1.el9_6.x86_64.rpm                                    3.8 MB/s | 330 kB     00:00
(40/65): libldb-4.21.3-14.el9_6.x86_64.rpm                                              1.8 MB/s | 192 kB     00:00
(41/65): libsmbclient-4.21.3-14.el9_6.x86_64.rpm                                        185 kB/s |  73 kB     00:00
(42/65): libwbclient-4.21.3-14.el9_6.x86_64.rpm                                         607 kB/s |  42 kB     00:00
(43/65): python39-oci-sdk-2.160.3-1.el9.x86_64.rpm                                       10 MB/s |  90 MB     00:08
(44/65): linux-firmware-core-20250909-999.44.git260ff424.el9.noarch.rpm                 1.6 MB/s | 899 kB     00:00
(45/65): linux-firmware-whence-20250909-999.44.git260ff424.el9.noarch.rpm               668 kB/s |  46 kB     00:00
(46/65): iwlax2xx-firmware-20250909-999.44.el9.noarch.rpm                               9.0 MB/s |  85 MB     00:09
(47/65): microcode_ctl-20250211-1.20250512.1.0.1.el9_6.noarch.rpm                       6.5 MB/s |  14 MB     00:02
(48/65): python3-perf-5.14.0-570.51.1.0.1.el9_6.x86_64.rpm                               11 MB/s | 3.2 MB     00:00
(49/65): samba-common-4.21.3-14.el9_6.noarch.rpm                                        1.3 MB/s | 188 kB     00:00
(50/65): samba-client-libs-4.21.3-14.el9_6.x86_64.rpm                                    12 MB/s | 5.3 MB     00:00
(51/65): samba-common-libs-4.21.3-14.el9_6.x86_64.rpm                                   813 kB/s | 105 kB     00:00
(52/65): sudo-1.9.5p2-10.el9_6.2.x86_64.rpm                                             3.5 MB/s | 1.1 MB     00:00
(53/65): sos-4.10.0-4.0.1.el9_6.noarch.rpm                                              6.1 MB/s | 2.3 MB     00:00
(54/65): systemd-libs-252-51.0.4.el9_6.2.x86_64.rpm                                     5.8 MB/s | 682 kB     00:00
(55/65): systemd-pam-252-51.0.4.el9_6.2.x86_64.rpm                                      1.3 MB/s | 278 kB     00:00
(56/65): systemd-252-51.0.4.el9_6.2.x86_64.rpm                                           10 MB/s | 4.6 MB     00:00
(57/65): systemd-rpm-macros-252-51.0.4.el9_6.2.noarch.rpm                               755 kB/s |  70 kB     00:00
(58/65): systemd-udev-252-51.0.4.el9_6.2.x86_64.rpm                                     5.7 MB/s | 2.2 MB     00:00
(59/65): gcc-toolset-14-gcc-c++-14.2.1-8.el9_6.x86_64.rpm                               9.4 MB/s |  15 MB     00:01
(60/65): gcc-toolset-14-libstdc++-devel-14.2.1-8.el9_6.x86_64.rpm                       6.3 MB/s | 4.3 MB     00:00
(61/65): kernel-headers-5.14.0-570.51.1.0.1.el9_6.x86_64.rpm                            6.6 MB/s | 4.3 MB     00:00
(62/65): perf-5.14.0-570.51.1.0.1.el9_6.x86_64.rpm                                      6.3 MB/s | 4.3 MB     00:00
(63/65): gcc-toolset-14-gcc-14.2.1-8.el9_6.x86_64.rpm                                    11 MB/s |  47 MB     00:04
(64/65): python3-cryptography-36.0.1-5.el9_6.x86_64.rpm                                 2.8 MB/s | 1.5 MB     00:00
(65/65): linux-firmware-20250909-999.44.git260ff424.el9.noarch.rpm                       16 MB/s | 583 MB     00:35
------------------------------------------------------------------------------------------------------------------------
Total                                                                                    22 MB/s | 1.1 GB     00:50
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Running scriptlet: linux-firmware-999:20250909-999.44.git260ff424.el9.noarch                                      1/1
  Running scriptlet: kmod-kvdo-8.2.5.14-164.0.1.el9_6.x86_64                                                        1/1
  Preparing        :                                                                                                1/1
  Upgrading        : linux-firmware-whence-999:20250909-999.44.git260ff424.el9.noarch                             1/118
  Upgrading        : systemd-libs-252-51.0.4.el9_6.2.x86_64                                                       2/118
  Running scriptlet: systemd-libs-252-51.0.4.el9_6.2.x86_64                                                       2/118
  Upgrading        : libldb-4.21.3-14.el9_6.x86_64                                                                3/118
  Upgrading        : gnutls-3.8.3-6.el9_6.2.x86_64                                                                4/118
  Upgrading        : NetworkManager-libnm-1:1.52.0-7.0.1.el9_6.x86_64                                             5/118
  Upgrading        : linux-firmware-core-999:20250909-999.44.git260ff424.el9.noarch                               6/118
  Upgrading        : linux-firmware-999:20250909-999.44.git260ff424.el9.noarch                                    7/118
  Upgrading        : ksplice-core0-2.0.8-1.el9.x86_64                                                             8/118
  Running scriptlet: ksplice-core0-2.0.8-1.el9.x86_64                                                             8/118
  Running scriptlet: ksplice-tools-2.0.8-1.el9.x86_64                                                             9/118
  Upgrading        : ksplice-tools-2.0.8-1.el9.x86_64                                                             9/118
  Running scriptlet: ksplice-tools-2.0.8-1.el9.x86_64                                                             9/118
  Upgrading        : iwlax2xx-firmware-999:20250909-999.44.el9.noarch                                            10/118
  Upgrading        : iwl7260-firmware-999:25.30.13.0-999.44.el9.noarch                                           11/118
  Upgrading        : python3-cryptography-36.0.1-5.el9_6.x86_64                                                  12/118
  Upgrading        : gcc-toolset-14-libstdc++-devel-14.2.1-8.el9_6.x86_64                                        13/118
  Upgrading        : gcc-toolset-14-gcc-14.2.1-8.el9_6.x86_64                                                    14/118
  Upgrading        : systemd-rpm-macros-252-51.0.4.el9_6.2.noarch                                                15/118
  Upgrading        : systemd-pam-252-51.0.4.el9_6.2.x86_64                                                       16/118
  Running scriptlet: systemd-252-51.0.4.el9_6.2.x86_64                                                           17/118
  Upgrading        : systemd-252-51.0.4.el9_6.2.x86_64                                                           17/118
  Running scriptlet: systemd-252-51.0.4.el9_6.2.x86_64                                                           17/118
  Upgrading        : systemd-udev-252-51.0.4.el9_6.2.x86_64                                                      18/118
  Running scriptlet: systemd-udev-252-51.0.4.el9_6.2.x86_64                                                      18/118
  Installing       : kernel-modules-core-5.14.0-570.51.1.0.1.el9_6.x86_64                                        19/118
  Installing       : kernel-core-5.14.0-570.51.1.0.1.el9_6.x86_64                                                20/118
  Running scriptlet: kernel-core-5.14.0-570.51.1.0.1.el9_6.x86_64                                                20/118
  Running scriptlet: samba-common-4.21.3-14.el9_6.noarch                                                         21/118
  Upgrading        : samba-common-4.21.3-14.el9_6.noarch                                                         21/118
  Running scriptlet: samba-common-4.21.3-14.el9_6.noarch                                                         21/118
  Running scriptlet: libwbclient-4.21.3-14.el9_6.x86_64                                                          22/118
  Upgrading        : libwbclient-4.21.3-14.el9_6.x86_64                                                          22/118
  Upgrading        : samba-common-libs-4.21.3-14.el9_6.x86_64                                                    23/118
  Upgrading        : samba-client-libs-4.21.3-14.el9_6.x86_64                                                    24/118
  Installing       : kernel-modules-5.14.0-570.51.1.0.1.el9_6.x86_64                                             25/118
  Running scriptlet: kernel-modules-5.14.0-570.51.1.0.1.el9_6.x86_64                                             25/118
  Installing       : kernel-uek-modules-core-6.12.0-103.40.4.4.el9uek.x86_64                                     26/118
  Running scriptlet: kernel-uek-core-6.12.0-103.40.4.4.el9uek.x86_64                                             27/118
  Installing       : kernel-uek-core-6.12.0-103.40.4.4.el9uek.x86_64                                             27/118
  Running scriptlet: kernel-uek-core-6.12.0-103.40.4.4.el9uek.x86_64                                             27/118
  Installing       : kernel-uek-modules-6.12.0-103.40.4.4.el9uek.x86_64                                          28/118
  Running scriptlet: kernel-uek-modules-6.12.0-103.40.4.4.el9uek.x86_64                                          28/118
  Running scriptlet: NetworkManager-1:1.52.0-7.0.1.el9_6.x86_64                                                  29/118
  Upgrading        : NetworkManager-1:1.52.0-7.0.1.el9_6.x86_64                                                  29/118
  Running scriptlet: NetworkManager-1:1.52.0-7.0.1.el9_6.x86_64                                                  29/118
  Installing       : kernel-uek-modules-desktop-6.12.0-103.40.4.4.el9uek.x86_64                                  30/118
  Running scriptlet: kernel-uek-modules-desktop-6.12.0-103.40.4.4.el9uek.x86_64                                  30/118
  Installing       : kernel-uek-modules-extra-netfilter-6.12.0-103.40.4.4.el9uek.x86_64                          31/118
  Running scriptlet: kernel-uek-modules-extra-netfilter-6.12.0-103.40.4.4.el9uek.x86_64                          31/118
  Installing       : kernel-uek-modules-usb-6.12.0-103.40.4.4.el9uek.x86_64                                      32/118
  Running scriptlet: kernel-uek-modules-usb-6.12.0-103.40.4.4.el9uek.x86_64                                      32/118
  Installing       : kernel-uek-modules-wireless-6.12.0-103.40.4.4.el9uek.x86_64                                 33/118
  Running scriptlet: kernel-uek-modules-wireless-6.12.0-103.40.4.4.el9uek.x86_64                                 33/118
  Upgrading        : kernel-tools-libs-5.14.0-570.51.1.0.1.el9_6.x86_64                                          34/118
  Running scriptlet: kernel-tools-libs-5.14.0-570.51.1.0.1.el9_6.x86_64                                          34/118
  Upgrading        : kernel-tools-5.14.0-570.51.1.0.1.el9_6.x86_64                                               35/118
  Running scriptlet: kernel-tools-5.14.0-570.51.1.0.1.el9_6.x86_64                                               35/118
  Installing       : kernel-uek-6.12.0-103.40.4.4.el9uek.x86_64                                                  36/118
  Upgrading        : NetworkManager-team-1:1.52.0-7.0.1.el9_6.x86_64                                             37/118
  Upgrading        : NetworkManager-tui-1:1.52.0-7.0.1.el9_6.x86_64                                              38/118
  Installing       : kernel-5.14.0-570.51.1.0.1.el9_6.x86_64                                                     39/118
  Running scriptlet: kmod-kvdo-8.2.5.14-164.0.1.el9_6.x86_64                                                     40/118
  Upgrading        : kmod-kvdo-8.2.5.14-164.0.1.el9_6.x86_64                                                     40/118
  Running scriptlet: kmod-kvdo-8.2.5.14-164.0.1.el9_6.x86_64                                                     40/118
  Upgrading        : libsmbclient-4.21.3-14.el9_6.x86_64                                                         41/118
  Upgrading        : kexec-tools-2.0.31-1.0.1.el9.x86_64                                                         42/118
warning: /etc/kdump.conf created as /etc/kdump.conf.rpmnew
warning: /etc/sysconfig/kdump created as /etc/sysconfig/kdump.rpmnew

  Running scriptlet: kexec-tools-2.0.31-1.0.1.el9.x86_64                                                         42/118
  Upgrading        : microcode_ctl-4:20250211-1.20250512.1.0.1.el9_6.noarch                                      43/118
  Running scriptlet: microcode_ctl-4:20250211-1.20250512.1.0.1.el9_6.noarch                                      43/118
  Upgrading        : gcc-toolset-14-gcc-c++-14.2.1-8.el9_6.x86_64                                                44/118
  Upgrading        : python39-oci-sdk-2.160.3-1.el9.x86_64                                                       45/118
  Upgrading        : ksplice-2.0.8-1.el9.x86_64                                                                  46/118
  Running scriptlet: ksplice-2.0.8-1.el9.x86_64                                                                  46/118
  Upgrading        : irqbalance-2:1.9.4-2.0.1.el9_6.2.x86_64                                                     47/118
  Running scriptlet: irqbalance-2:1.9.4-2.0.1.el9_6.2.x86_64                                                     47/118
  Upgrading        : iwl100-firmware-999:39.31.5.1-999.44.el9.noarch                                             48/118
  Upgrading        : iwl1000-firmware-999:39.31.5.1-999.44.el9.noarch                                            49/118
  Upgrading        : iwl105-firmware-999:18.168.6.1-999.44.el9.noarch                                            50/118
  Upgrading        : iwl135-firmware-999:18.168.6.1-999.44.el9.noarch                                            51/118
  Upgrading        : iwl2000-firmware-999:18.168.6.1-999.44.el9.noarch                                           52/118
  Upgrading        : iwl2030-firmware-999:18.168.6.1-999.44.el9.noarch                                           53/118
  Upgrading        : iwl3160-firmware-999:25.30.13.0-999.44.el9.noarch                                           54/118
  Upgrading        : iwl5000-firmware-999:8.83.5.1_1-999.44.el9.noarch                                           55/118
  Upgrading        : iwl5150-firmware-999:8.24.2.2-999.44.el9.noarch                                             56/118
  Upgrading        : iwl6000g2a-firmware-999:18.168.6.1-999.44.el9.noarch                                        57/118
  Upgrading        : iwl6050-firmware-999:41.28.5.1-999.44.el9.noarch                                            58/118
  Upgrading        : perf-5.14.0-570.51.1.0.1.el9_6.x86_64                                                       59/118
  Upgrading        : kernel-headers-5.14.0-570.51.1.0.1.el9_6.x86_64                                             60/118
  Upgrading        : sudo-1.9.5p2-10.el9_6.2.x86_64                                                              61/118
  Running scriptlet: sudo-1.9.5p2-10.el9_6.2.x86_64                                                              61/118
  Upgrading        : sos-4.10.0-4.0.1.el9_6.noarch                                                               62/118
  Upgrading        : python3-perf-5.14.0-570.51.1.0.1.el9_6.x86_64                                               63/118
  Upgrading        : gsettings-desktop-schemas-40.0-7.el9_6.x86_64                                               64/118
  Upgrading        : NetworkManager-config-server-1:1.52.0-7.0.1.el9_6.noarch                                    65/118
  Running scriptlet: microcode_ctl-4:20250211-1.0.1.el9_6.noarch                                                 66/118
  Cleanup          : microcode_ctl-4:20250211-1.0.1.el9_6.noarch                                                 66/118
  Running scriptlet: microcode_ctl-4:20250211-1.0.1.el9_6.noarch                                                 66/118
  Cleanup          : python39-oci-sdk-2.160.0-1.el9.x86_64                                                       67/118
  Cleanup          : linux-firmware-999:20250611-999.41.git356f06bf.el9.noarch                                   68/118
  Cleanup          : iwl7260-firmware-999:25.30.13.0-999.41.el9.noarch                                           69/118
  Running scriptlet: ksplice-2.0.7-1.el9.x86_64                                                                  70/118
  Cleanup          : ksplice-2.0.7-1.el9.x86_64                                                                  70/118
  Running scriptlet: ksplice-2.0.7-1.el9.x86_64                                                                  70/118
  Running scriptlet: ksplice-tools-2.0.7-1.el9.x86_64                                                            71/118
  Cleanup          : ksplice-tools-2.0.7-1.el9.x86_64                                                            71/118
  Cleanup          : iwlax2xx-firmware-999:20250611-999.41.el9.noarch                                            72/118
  Cleanup          : linux-firmware-core-999:20250611-999.41.git356f06bf.el9.noarch                              73/118
  Cleanup          : iwl6050-firmware-999:41.28.5.1-999.41.el9.noarch                                            74/118
  Cleanup          : iwl6000g2a-firmware-999:18.168.6.1-999.41.el9.noarch                                        75/118
  Cleanup          : iwl5150-firmware-999:8.24.2.2-999.41.el9.noarch                                             76/118
  Cleanup          : iwl5000-firmware-999:8.83.5.1_1-999.41.el9.noarch                                           77/118
  Cleanup          : iwl3160-firmware-999:25.30.13.0-999.41.el9.noarch                                           78/118
  Cleanup          : iwl2030-firmware-999:18.168.6.1-999.41.el9.noarch                                           79/118
  Cleanup          : iwl2000-firmware-999:18.168.6.1-999.41.el9.noarch                                           80/118
  Cleanup          : iwl135-firmware-999:18.168.6.1-999.41.el9.noarch                                            81/118
  Cleanup          : iwl105-firmware-999:18.168.6.1-999.41.el9.noarch                                            82/118
  Cleanup          : iwl1000-firmware-999:39.31.5.1-999.41.el9.noarch                                            83/118
  Cleanup          : iwl100-firmware-999:39.31.5.1-999.41.el9.noarch                                             84/118
  Cleanup          : linux-firmware-whence-999:20250611-999.41.git356f06bf.el9.noarch                            85/118
  Cleanup          : kernel-headers-5.14.0-570.39.1.0.1.el9_6.x86_64                                             86/118
  Cleanup          : sos-4.9.2-1.0.1.el9_6.noarch                                                                87/118
  Running scriptlet: kmod-kvdo-8.2.5.14-163.0.1.el9_6.x86_64                                                     88/118
  Cleanup          : kmod-kvdo-8.2.5.14-163.0.1.el9_6.x86_64                                                     88/118
  Running scriptlet: kmod-kvdo-8.2.5.14-163.0.1.el9_6.x86_64                                                     88/118
  Cleanup          : gsettings-desktop-schemas-40.0-6.el9.x86_64                                                 89/118
  Cleanup          : NetworkManager-config-server-1:1.52.0-5.0.1.el9_6.noarch                                    90/118
  Cleanup          : libsmbclient-4.21.3-7.el9_6.x86_64                                                          91/118
  Cleanup          : NetworkManager-tui-1:1.52.0-5.0.1.el9_6.x86_64                                              92/118
  Cleanup          : samba-client-libs-4.21.3-7.el9_6.x86_64                                                     93/118
  Cleanup          : samba-common-libs-4.21.3-7.el9_6.x86_64                                                     94/118
  Cleanup          : libwbclient-4.21.3-7.el9_6.x86_64                                                           95/118
  Cleanup          : gcc-toolset-14-gcc-c++-14.2.1-7.1.el9.x86_64                                                96/118
  Running scriptlet: kernel-tools-5.14.0-570.39.1.0.1.el9_6.x86_64                                               97/118
  Cleanup          : kernel-tools-5.14.0-570.39.1.0.1.el9_6.x86_64                                               97/118
  Running scriptlet: kernel-tools-5.14.0-570.39.1.0.1.el9_6.x86_64                                               97/118
  Running scriptlet: irqbalance-2:1.9.4-2.0.1.el9.x86_64                                                         98/118
  Cleanup          : irqbalance-2:1.9.4-2.0.1.el9.x86_64                                                         98/118
  Running scriptlet: irqbalance-2:1.9.4-2.0.1.el9.x86_64                                                         98/118
  Cleanup          : samba-common-4.21.3-7.el9_6.noarch                                                          99/118
  Running scriptlet: kexec-tools-2.0.29-5.0.4.el9_6.2.x86_64                                                    100/118
  Cleanup          : kexec-tools-2.0.29-5.0.4.el9_6.2.x86_64                                                    100/118
  Running scriptlet: kexec-tools-2.0.29-5.0.4.el9_6.2.x86_64                                                    100/118
  Cleanup          : NetworkManager-team-1:1.52.0-5.0.1.el9_6.x86_64                                            101/118
  Cleanup          : gcc-toolset-14-libstdc++-devel-14.2.1-7.1.el9.x86_64                                       102/118
  Running scriptlet: NetworkManager-1:1.52.0-5.0.1.el9_6.x86_64                                                 103/118
  Cleanup          : NetworkManager-1:1.52.0-5.0.1.el9_6.x86_64                                                 103/118
  Running scriptlet: NetworkManager-1:1.52.0-5.0.1.el9_6.x86_64                                                 103/118
  Running scriptlet: systemd-udev-252-51.0.4.el9_6.1.x86_64                                                     104/118
  Cleanup          : systemd-udev-252-51.0.4.el9_6.1.x86_64                                                     104/118
  Running scriptlet: systemd-udev-252-51.0.4.el9_6.1.x86_64                                                     104/118
  Cleanup          : NetworkManager-libnm-1:1.52.0-5.0.1.el9_6.x86_64                                           105/118
  Cleanup          : systemd-252-51.0.4.el9_6.1.x86_64                                                          106/118
  Running scriptlet: systemd-252-51.0.4.el9_6.1.x86_64                                                          106/118
  Cleanup          : systemd-rpm-macros-252-51.0.4.el9_6.1.noarch                                               107/118
  Cleanup          : systemd-libs-252-51.0.4.el9_6.1.x86_64                                                     108/118
  Cleanup          : systemd-pam-252-51.0.4.el9_6.1.x86_64                                                      109/118
  Cleanup          : gnutls-3.8.3-6.el9.x86_64                                                                  110/118
  Cleanup          : kernel-tools-libs-5.14.0-570.39.1.0.1.el9_6.x86_64                                         111/118
  Running scriptlet: kernel-tools-libs-5.14.0-570.39.1.0.1.el9_6.x86_64                                         111/118
  Cleanup          : gcc-toolset-14-gcc-14.2.1-7.1.el9.x86_64                                                   112/118
  Cleanup          : libldb-4.21.3-7.el9_6.x86_64                                                               113/118
  Cleanup          : ksplice-core0-2.0.7-1.el9.x86_64                                                           114/118
  Running scriptlet: ksplice-core0-2.0.7-1.el9.x86_64                                                           114/118
  Cleanup          : python3-cryptography-36.0.1-4.0.1.el9.x86_64                                               115/118
  Cleanup          : perf-5.14.0-570.39.1.0.1.el9_6.x86_64                                                      116/118
  Cleanup          : sudo-1.9.5p2-10.el9_6.1.x86_64                                                             117/118
  Cleanup          : python3-perf-5.14.0-570.39.1.0.1.el9_6.x86_64                                              118/118
  Running scriptlet: linux-firmware-core-999:20250909-999.44.git260ff424.el9.noarch                             118/118
  Running scriptlet: ksplice-tools-2.0.8-1.el9.x86_64                                                           118/118
  Running scriptlet: kernel-modules-core-5.14.0-570.51.1.0.1.el9_6.x86_64                                       118/118
  Running scriptlet: kernel-core-5.14.0-570.51.1.0.1.el9_6.x86_64                                               118/118
2025-10-08 13:59:51,456 - INFO - Processing directory: /var/cache/uptrack/Linux/x86_64
2025-10-08 13:59:51,694 - INFO - Kept: /var/cache/uptrack/Linux/x86_64/6.12.0-103.40.4.2.el9uek.x86_64
2025-10-08 13:59:51,695 - INFO - Directory cleaned up successfully: /var/cache/uptrack

  Running scriptlet: kernel-modules-5.14.0-570.51.1.0.1.el9_6.x86_64                                            118/118
  Running scriptlet: kernel-uek-modules-core-6.12.0-103.40.4.4.el9uek.x86_64                                    118/118
  Running scriptlet: kernel-uek-core-6.12.0-103.40.4.4.el9uek.x86_64                                            118/118
2025-10-08 14:04:02,062 - INFO - Processing directory: /var/cache/uptrack/Linux/x86_64
2025-10-08 14:04:02,352 - INFO - Kept: /var/cache/uptrack/Linux/x86_64/6.12.0-103.40.4.2.el9uek.x86_64
2025-10-08 14:04:02,352 - INFO - Directory cleaned up successfully: /var/cache/uptrack

  Running scriptlet: kernel-uek-modules-6.12.0-103.40.4.4.el9uek.x86_64                                         118/118
  Running scriptlet: kmod-kvdo-8.2.5.14-164.0.1.el9_6.x86_64                                                    118/118
  Running scriptlet: kexec-tools-2.0.31-1.0.1.el9.x86_64                                                        118/118
  Running scriptlet: microcode_ctl-4:20250211-1.20250512.1.0.1.el9_6.noarch                                     118/118
  Running scriptlet: ksplice-2.0.8-1.el9.x86_64                                                                 118/118
There are no existing modules on disk that need basename migration.

  Running scriptlet: python3-perf-5.14.0-570.39.1.0.1.el9_6.x86_64                                              118/118
  Verifying        : kernel-5.14.0-570.51.1.0.1.el9_6.x86_64                                                      1/118
  Verifying        : kernel-core-5.14.0-570.51.1.0.1.el9_6.x86_64                                                 2/118
  Verifying        : kernel-modules-5.14.0-570.51.1.0.1.el9_6.x86_64                                              3/118
  Verifying        : kernel-modules-core-5.14.0-570.51.1.0.1.el9_6.x86_64                                         4/118
  Verifying        : kernel-uek-6.12.0-103.40.4.4.el9uek.x86_64                                                   5/118
  Verifying        : kernel-uek-core-6.12.0-103.40.4.4.el9uek.x86_64                                              6/118
  Verifying        : kernel-uek-modules-6.12.0-103.40.4.4.el9uek.x86_64                                           7/118
  Verifying        : kernel-uek-modules-core-6.12.0-103.40.4.4.el9uek.x86_64                                      8/118
  Verifying        : kernel-uek-modules-desktop-6.12.0-103.40.4.4.el9uek.x86_64                                   9/118
  Verifying        : kernel-uek-modules-extra-netfilter-6.12.0-103.40.4.4.el9uek.x86_64                          10/118
  Verifying        : kernel-uek-modules-usb-6.12.0-103.40.4.4.el9uek.x86_64                                      11/118
  Verifying        : kernel-uek-modules-wireless-6.12.0-103.40.4.4.el9uek.x86_64                                 12/118
  Verifying        : ksplice-2.0.8-1.el9.x86_64                                                                  13/118
  Verifying        : ksplice-2.0.7-1.el9.x86_64                                                                  14/118
  Verifying        : ksplice-core0-2.0.8-1.el9.x86_64                                                            15/118
  Verifying        : ksplice-core0-2.0.7-1.el9.x86_64                                                            16/118
  Verifying        : ksplice-tools-2.0.8-1.el9.x86_64                                                            17/118
  Verifying        : ksplice-tools-2.0.7-1.el9.x86_64                                                            18/118
  Verifying        : python39-oci-sdk-2.160.3-1.el9.x86_64                                                       19/118
  Verifying        : python39-oci-sdk-2.160.0-1.el9.x86_64                                                       20/118
  Verifying        : NetworkManager-1:1.52.0-7.0.1.el9_6.x86_64                                                  21/118
  Verifying        : NetworkManager-1:1.52.0-5.0.1.el9_6.x86_64                                                  22/118
  Verifying        : NetworkManager-config-server-1:1.52.0-7.0.1.el9_6.noarch                                    23/118
  Verifying        : NetworkManager-config-server-1:1.52.0-5.0.1.el9_6.noarch                                    24/118
  Verifying        : NetworkManager-libnm-1:1.52.0-7.0.1.el9_6.x86_64                                            25/118
  Verifying        : NetworkManager-libnm-1:1.52.0-5.0.1.el9_6.x86_64                                            26/118
  Verifying        : NetworkManager-team-1:1.52.0-7.0.1.el9_6.x86_64                                             27/118
  Verifying        : NetworkManager-team-1:1.52.0-5.0.1.el9_6.x86_64                                             28/118
  Verifying        : NetworkManager-tui-1:1.52.0-7.0.1.el9_6.x86_64                                              29/118
  Verifying        : NetworkManager-tui-1:1.52.0-5.0.1.el9_6.x86_64                                              30/118
  Verifying        : gnutls-3.8.3-6.el9_6.2.x86_64                                                               31/118
  Verifying        : gnutls-3.8.3-6.el9.x86_64                                                                   32/118
  Verifying        : gsettings-desktop-schemas-40.0-7.el9_6.x86_64                                               33/118
  Verifying        : gsettings-desktop-schemas-40.0-6.el9.x86_64                                                 34/118
  Verifying        : irqbalance-2:1.9.4-2.0.1.el9_6.2.x86_64                                                     35/118
  Verifying        : irqbalance-2:1.9.4-2.0.1.el9.x86_64                                                         36/118
  Verifying        : iwl100-firmware-999:39.31.5.1-999.44.el9.noarch                                             37/118
  Verifying        : iwl100-firmware-999:39.31.5.1-999.41.el9.noarch                                             38/118
  Verifying        : iwl1000-firmware-999:39.31.5.1-999.44.el9.noarch                                            39/118
  Verifying        : iwl1000-firmware-999:39.31.5.1-999.41.el9.noarch                                            40/118
  Verifying        : iwl105-firmware-999:18.168.6.1-999.44.el9.noarch                                            41/118
  Verifying        : iwl105-firmware-999:18.168.6.1-999.41.el9.noarch                                            42/118
  Verifying        : iwl135-firmware-999:18.168.6.1-999.44.el9.noarch                                            43/118
  Verifying        : iwl135-firmware-999:18.168.6.1-999.41.el9.noarch                                            44/118
  Verifying        : iwl2000-firmware-999:18.168.6.1-999.44.el9.noarch                                           45/118
  Verifying        : iwl2000-firmware-999:18.168.6.1-999.41.el9.noarch                                           46/118
  Verifying        : iwl2030-firmware-999:18.168.6.1-999.44.el9.noarch                                           47/118
  Verifying        : iwl2030-firmware-999:18.168.6.1-999.41.el9.noarch                                           48/118
  Verifying        : iwl3160-firmware-999:25.30.13.0-999.44.el9.noarch                                           49/118
  Verifying        : iwl3160-firmware-999:25.30.13.0-999.41.el9.noarch                                           50/118
  Verifying        : iwl5000-firmware-999:8.83.5.1_1-999.44.el9.noarch                                           51/118
  Verifying        : iwl5000-firmware-999:8.83.5.1_1-999.41.el9.noarch                                           52/118
  Verifying        : iwl5150-firmware-999:8.24.2.2-999.44.el9.noarch                                             53/118
  Verifying        : iwl5150-firmware-999:8.24.2.2-999.41.el9.noarch                                             54/118
  Verifying        : iwl6000g2a-firmware-999:18.168.6.1-999.44.el9.noarch                                        55/118
  Verifying        : iwl6000g2a-firmware-999:18.168.6.1-999.41.el9.noarch                                        56/118
  Verifying        : iwl6050-firmware-999:41.28.5.1-999.44.el9.noarch                                            57/118
  Verifying        : iwl6050-firmware-999:41.28.5.1-999.41.el9.noarch                                            58/118
  Verifying        : iwl7260-firmware-999:25.30.13.0-999.44.el9.noarch                                           59/118
  Verifying        : iwl7260-firmware-999:25.30.13.0-999.41.el9.noarch                                           60/118
  Verifying        : iwlax2xx-firmware-999:20250909-999.44.el9.noarch                                            61/118
  Verifying        : iwlax2xx-firmware-999:20250611-999.41.el9.noarch                                            62/118
  Verifying        : kernel-tools-5.14.0-570.51.1.0.1.el9_6.x86_64                                               63/118
  Verifying        : kernel-tools-5.14.0-570.39.1.0.1.el9_6.x86_64                                               64/118
  Verifying        : kernel-tools-libs-5.14.0-570.51.1.0.1.el9_6.x86_64                                          65/118
  Verifying        : kernel-tools-libs-5.14.0-570.39.1.0.1.el9_6.x86_64                                          66/118
  Verifying        : kexec-tools-2.0.31-1.0.1.el9.x86_64                                                         67/118
  Verifying        : kexec-tools-2.0.29-5.0.4.el9_6.2.x86_64                                                     68/118
  Verifying        : kmod-kvdo-8.2.5.14-164.0.1.el9_6.x86_64                                                     69/118
  Verifying        : kmod-kvdo-8.2.5.14-163.0.1.el9_6.x86_64                                                     70/118
  Verifying        : libldb-4.21.3-14.el9_6.x86_64                                                               71/118
  Verifying        : libldb-4.21.3-7.el9_6.x86_64                                                                72/118
  Verifying        : libsmbclient-4.21.3-14.el9_6.x86_64                                                         73/118
  Verifying        : libsmbclient-4.21.3-7.el9_6.x86_64                                                          74/118
  Verifying        : libwbclient-4.21.3-14.el9_6.x86_64                                                          75/118
  Verifying        : libwbclient-4.21.3-7.el9_6.x86_64                                                           76/118
  Verifying        : linux-firmware-999:20250909-999.44.git260ff424.el9.noarch                                   77/118
  Verifying        : linux-firmware-999:20250611-999.41.git356f06bf.el9.noarch                                   78/118
  Verifying        : linux-firmware-core-999:20250909-999.44.git260ff424.el9.noarch                              79/118
  Verifying        : linux-firmware-core-999:20250611-999.41.git356f06bf.el9.noarch                              80/118
  Verifying        : linux-firmware-whence-999:20250909-999.44.git260ff424.el9.noarch                            81/118
  Verifying        : linux-firmware-whence-999:20250611-999.41.git356f06bf.el9.noarch                            82/118
  Verifying        : microcode_ctl-4:20250211-1.20250512.1.0.1.el9_6.noarch                                      83/118
  Verifying        : microcode_ctl-4:20250211-1.0.1.el9_6.noarch                                                 84/118
  Verifying        : python3-perf-5.14.0-570.51.1.0.1.el9_6.x86_64                                               85/118
  Verifying        : python3-perf-5.14.0-570.39.1.0.1.el9_6.x86_64                                               86/118
  Verifying        : samba-client-libs-4.21.3-14.el9_6.x86_64                                                    87/118
  Verifying        : samba-client-libs-4.21.3-7.el9_6.x86_64                                                     88/118
  Verifying        : samba-common-4.21.3-14.el9_6.noarch                                                         89/118
  Verifying        : samba-common-4.21.3-7.el9_6.noarch                                                          90/118
  Verifying        : samba-common-libs-4.21.3-14.el9_6.x86_64                                                    91/118
  Verifying        : samba-common-libs-4.21.3-7.el9_6.x86_64                                                     92/118
  Verifying        : sos-4.10.0-4.0.1.el9_6.noarch                                                               93/118
  Verifying        : sos-4.9.2-1.0.1.el9_6.noarch                                                                94/118
  Verifying        : sudo-1.9.5p2-10.el9_6.2.x86_64                                                              95/118
  Verifying        : sudo-1.9.5p2-10.el9_6.1.x86_64                                                              96/118
  Verifying        : systemd-252-51.0.4.el9_6.2.x86_64                                                           97/118
  Verifying        : systemd-252-51.0.4.el9_6.1.x86_64                                                           98/118
  Verifying        : systemd-libs-252-51.0.4.el9_6.2.x86_64                                                      99/118
  Verifying        : systemd-libs-252-51.0.4.el9_6.1.x86_64                                                     100/118
  Verifying        : systemd-pam-252-51.0.4.el9_6.2.x86_64                                                      101/118
  Verifying        : systemd-pam-252-51.0.4.el9_6.1.x86_64                                                      102/118
  Verifying        : systemd-rpm-macros-252-51.0.4.el9_6.2.noarch                                               103/118
  Verifying        : systemd-rpm-macros-252-51.0.4.el9_6.1.noarch                                               104/118
  Verifying        : systemd-udev-252-51.0.4.el9_6.2.x86_64                                                     105/118
  Verifying        : systemd-udev-252-51.0.4.el9_6.1.x86_64                                                     106/118
  Verifying        : gcc-toolset-14-gcc-14.2.1-8.el9_6.x86_64                                                   107/118
  Verifying        : gcc-toolset-14-gcc-14.2.1-7.1.el9.x86_64                                                   108/118
  Verifying        : gcc-toolset-14-gcc-c++-14.2.1-8.el9_6.x86_64                                               109/118
  Verifying        : gcc-toolset-14-gcc-c++-14.2.1-7.1.el9.x86_64                                               110/118
  Verifying        : gcc-toolset-14-libstdc++-devel-14.2.1-8.el9_6.x86_64                                       111/118
  Verifying        : gcc-toolset-14-libstdc++-devel-14.2.1-7.1.el9.x86_64                                       112/118
  Verifying        : kernel-headers-5.14.0-570.51.1.0.1.el9_6.x86_64                                            113/118
  Verifying        : kernel-headers-5.14.0-570.39.1.0.1.el9_6.x86_64                                            114/118
  Verifying        : perf-5.14.0-570.51.1.0.1.el9_6.x86_64                                                      115/118
  Verifying        : perf-5.14.0-570.39.1.0.1.el9_6.x86_64                                                      116/118
  Verifying        : python3-cryptography-36.0.1-5.el9_6.x86_64                                                 117/118
  Verifying        : python3-cryptography-36.0.1-4.0.1.el9.x86_64                                               118/118

Upgraded:
  NetworkManager-1:1.52.0-7.0.1.el9_6.x86_64
  NetworkManager-config-server-1:1.52.0-7.0.1.el9_6.noarch
  NetworkManager-libnm-1:1.52.0-7.0.1.el9_6.x86_64
  NetworkManager-team-1:1.52.0-7.0.1.el9_6.x86_64
  NetworkManager-tui-1:1.52.0-7.0.1.el9_6.x86_64
  gcc-toolset-14-gcc-14.2.1-8.el9_6.x86_64
  gcc-toolset-14-gcc-c++-14.2.1-8.el9_6.x86_64
  gcc-toolset-14-libstdc++-devel-14.2.1-8.el9_6.x86_64
  gnutls-3.8.3-6.el9_6.2.x86_64
  gsettings-desktop-schemas-40.0-7.el9_6.x86_64
  irqbalance-2:1.9.4-2.0.1.el9_6.2.x86_64
  iwl100-firmware-999:39.31.5.1-999.44.el9.noarch
  iwl1000-firmware-999:39.31.5.1-999.44.el9.noarch
  iwl105-firmware-999:18.168.6.1-999.44.el9.noarch
  iwl135-firmware-999:18.168.6.1-999.44.el9.noarch
  iwl2000-firmware-999:18.168.6.1-999.44.el9.noarch
  iwl2030-firmware-999:18.168.6.1-999.44.el9.noarch
  iwl3160-firmware-999:25.30.13.0-999.44.el9.noarch
  iwl5000-firmware-999:8.83.5.1_1-999.44.el9.noarch
  iwl5150-firmware-999:8.24.2.2-999.44.el9.noarch
  iwl6000g2a-firmware-999:18.168.6.1-999.44.el9.noarch
  iwl6050-firmware-999:41.28.5.1-999.44.el9.noarch
  iwl7260-firmware-999:25.30.13.0-999.44.el9.noarch
  iwlax2xx-firmware-999:20250909-999.44.el9.noarch
  kernel-headers-5.14.0-570.51.1.0.1.el9_6.x86_64
  kernel-tools-5.14.0-570.51.1.0.1.el9_6.x86_64
  kernel-tools-libs-5.14.0-570.51.1.0.1.el9_6.x86_64
  kexec-tools-2.0.31-1.0.1.el9.x86_64
  kmod-kvdo-8.2.5.14-164.0.1.el9_6.x86_64
  ksplice-2.0.8-1.el9.x86_64
  ksplice-core0-2.0.8-1.el9.x86_64
  ksplice-tools-2.0.8-1.el9.x86_64
  libldb-4.21.3-14.el9_6.x86_64
  libsmbclient-4.21.3-14.el9_6.x86_64
  libwbclient-4.21.3-14.el9_6.x86_64
  linux-firmware-999:20250909-999.44.git260ff424.el9.noarch
  linux-firmware-core-999:20250909-999.44.git260ff424.el9.noarch
  linux-firmware-whence-999:20250909-999.44.git260ff424.el9.noarch
  microcode_ctl-4:20250211-1.20250512.1.0.1.el9_6.noarch
  perf-5.14.0-570.51.1.0.1.el9_6.x86_64
  python3-cryptography-36.0.1-5.el9_6.x86_64
  python3-perf-5.14.0-570.51.1.0.1.el9_6.x86_64
  python39-oci-sdk-2.160.3-1.el9.x86_64
  samba-client-libs-4.21.3-14.el9_6.x86_64
  samba-common-4.21.3-14.el9_6.noarch
  samba-common-libs-4.21.3-14.el9_6.x86_64
  sos-4.10.0-4.0.1.el9_6.noarch
  sudo-1.9.5p2-10.el9_6.2.x86_64
  systemd-252-51.0.4.el9_6.2.x86_64
  systemd-libs-252-51.0.4.el9_6.2.x86_64
  systemd-pam-252-51.0.4.el9_6.2.x86_64
  systemd-rpm-macros-252-51.0.4.el9_6.2.noarch
  systemd-udev-252-51.0.4.el9_6.2.x86_64
Installed:
  kernel-5.14.0-570.51.1.0.1.el9_6.x86_64
  kernel-core-5.14.0-570.51.1.0.1.el9_6.x86_64
  kernel-modules-5.14.0-570.51.1.0.1.el9_6.x86_64
  kernel-modules-core-5.14.0-570.51.1.0.1.el9_6.x86_64
  kernel-uek-6.12.0-103.40.4.4.el9uek.x86_64
  kernel-uek-core-6.12.0-103.40.4.4.el9uek.x86_64
  kernel-uek-modules-6.12.0-103.40.4.4.el9uek.x86_64
  kernel-uek-modules-core-6.12.0-103.40.4.4.el9uek.x86_64
  kernel-uek-modules-desktop-6.12.0-103.40.4.4.el9uek.x86_64
  kernel-uek-modules-extra-netfilter-6.12.0-103.40.4.4.el9uek.x86_64
  kernel-uek-modules-usb-6.12.0-103.40.4.4.el9uek.x86_64
  kernel-uek-modules-wireless-6.12.0-103.40.4.4.el9uek.x86_64

Complete!
[opc@LennoxsDomain ~]$

Coding Day 3:
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

Install the latest PowerShell for new features and improvements! https://aka.ms/PSWindows

PS C:\WINDOWS\system32> ssh -I C:\Users\lenno\.ssh\[REDACTED].key
usage: ssh [-46AaCfGgKkMNnqsTtVvXxYy] [-B bind_interface] [-b bind_address]
           [-c cipher_spec] [-D [bind_address:]port] [-E log_file]
           [-e escape_char] [-F configfile] [-I pkcs11] [-i identity_file]
           [-J destination] [-L address] [-l login_name] [-m mac_spec]
           [-O ctl_cmd] [-o option] [-P tag] [-p port] [-Q query_option]
           [-R address] [-S ctl_path] [-W host:port] [-w local_tun[:remote_tun]]
           destination [command [argument ...]]
PS C:\WINDOWS\system32> ssh -i C:\Users\lenno\.ssh\ [REDACTED].key opc@157.151.194.68
Last login: Thu Oct  9 12:30:14 2025 from 204.126.178.254
[opc@LennoxsDomain ~]$ sudo firewall-cmd --permanent --add-port=3000/tcp
success
[opc@LennoxsDomain ~]$ sudo firewall-cmd --reload
success
[opc@LennoxsDomain ~]$ sudo yum update
Last metadata expiration check: 2:27:42 ago on Wed 15 Oct 2025 01:06:07 PM GMT.
sudo yum install -y nodejs
Dependencies resolved.
========================================================================================================================
 Package                                  Architecture Version                            Repository               Size
========================================================================================================================
Installing:
 kernel                                   x86_64       5.14.0-570.52.1.0.1.el9_6          ol9_baseos_latest       1.8 M
 kernel-core                              x86_64       5.14.0-570.52.1.0.1.el9_6          ol9_baseos_latest        18 M
 kernel-modules                           x86_64       5.14.0-570.52.1.0.1.el9_6          ol9_baseos_latest        40 M
 kernel-modules-core                      x86_64       5.14.0-570.52.1.0.1.el9_6          ol9_baseos_latest        32 M
 kernel-uek                               x86_64       6.12.0-104.43.4.2.el9uek           ol9_UEKR8               1.0 M
 kernel-uek-core                          x86_64       6.12.0-104.43.4.2.el9uek           ol9_UEKR8                19 M
 kernel-uek-modules                       x86_64       6.12.0-104.43.4.2.el9uek           ol9_UEKR8                31 M
 kernel-uek-modules-core                  x86_64       6.12.0-104.43.4.2.el9uek           ol9_UEKR8                38 M
 kernel-uek-modules-desktop               x86_64       6.12.0-104.43.4.2.el9uek           ol9_UEKR8                21 M
 kernel-uek-modules-extra-netfilter       x86_64       6.12.0-104.43.4.2.el9uek           ol9_UEKR8               1.9 M
 kernel-uek-modules-usb                   x86_64       6.12.0-104.43.4.2.el9uek           ol9_UEKR8               1.9 M
 kernel-uek-modules-wireless              x86_64       6.12.0-104.43.4.2.el9uek           ol9_UEKR8               8.8 M
Upgrading:
 iputils                                  x86_64       20210202-11.0.1.el9_6.3            ol9_baseos_latest       191 k
 kernel-headers                           x86_64       5.14.0-570.52.1.0.1.el9_6          ol9_appstream           4.3 M
 kernel-tools                             x86_64       5.14.0-570.52.1.0.1.el9_6          ol9_baseos_latest       2.1 M
 kernel-tools-libs                        x86_64       5.14.0-570.52.1.0.1.el9_6          ol9_baseos_latest       1.8 M
 kexec-tools                              x86_64       2.0.31-1.0.1.el9_6                 ol9_baseos_latest       540 k
 mcelog                                   x86_64       3:207-1.0.1.el9                    ol9_baseos_latest        90 k
 perf                                     x86_64       5.14.0-570.52.1.0.1.el9_6          ol9_appstream           4.3 M
 python3-perf                             x86_64       5.14.0-570.52.1.0.1.el9_6          ol9_baseos_latest       3.2 M
 python39-oci-sdk                         x86_64       2.161.0-1.el9                      ol9_oci_included         90 M
 systemd                                  x86_64       252-51.0.6.el9_6.2                 ol9_baseos_latest       4.6 M
 systemd-libs                             x86_64       252-51.0.6.el9_6.2                 ol9_baseos_latest       684 k
 systemd-pam                              x86_64       252-51.0.6.el9_6.2                 ol9_baseos_latest       278 k
 systemd-rpm-macros                       noarch       252-51.0.6.el9_6.2                 ol9_baseos_latest        70 k
 systemd-udev                             x86_64       252-51.0.6.el9_6.2                 ol9_baseos_latest       2.2 M
 vim-common                               x86_64       2:8.2.2637-22.0.1.el9_6.1          ol9_appstream           8.4 M
 vim-enhanced                             x86_64       2:8.2.2637-22.0.1.el9_6.1          ol9_appstream           1.7 M
 vim-filesystem                           noarch       2:8.2.2637-22.0.1.el9_6.1          ol9_baseos_latest       9.4 k
 vim-minimal                              x86_64       2:8.2.2637-22.0.1.el9_6.1          ol9_baseos_latest       676 k

Transaction Summary
========================================================================================================================
Install  12 Packages
Upgrade  18 Packages

Total download size: 339 M
Is this ok [y/N]: Is this ok [y/N]: y
Downloading Packages:
(1/30): kernel-5.14.0-570.52.1.0.1.el9_6.x86_64.rpm                                     2.1 MB/s | 1.8 MB     00:00
(2/30): kernel-core-5.14.0-570.52.1.0.1.el9_6.x86_64.rpm                                6.9 MB/s |  18 MB     00:02
(3/30): kernel-uek-6.12.0-104.43.4.2.el9uek.x86_64.rpm                                  7.1 MB/s | 1.0 MB     00:00
(4/30): kernel-modules-core-5.14.0-570.52.1.0.1.el9_6.x86_64.rpm                        8.0 MB/s |  32 MB     00:03
(5/30): kernel-uek-core-6.12.0-104.43.4.2.el9uek.x86_64.rpm                             6.8 MB/s |  19 MB     00:02
(6/30): kernel-modules-5.14.0-570.52.1.0.1.el9_6.x86_64.rpm                             6.1 MB/s |  40 MB     00:06
(7/30): kernel-uek-modules-6.12.0-104.43.4.2.el9uek.x86_64.rpm                          5.5 MB/s |  31 MB     00:05
(8/30): kernel-uek-modules-desktop-6.12.0-104.43.4.2.el9uek.x86_64.rpm                  4.9 MB/s |  21 MB     00:04
(9/30): kernel-uek-modules-extra-netfilter-6.12.0-104.43.4.2.el9uek.x86_64.rpm          5.1 MB/s | 1.9 MB     00:00
(10/30): kernel-uek-modules-usb-6.12.0-104.43.4.2.el9uek.x86_64.rpm                      11 MB/s | 1.9 MB     00:00
(11/30): kernel-uek-modules-core-6.12.0-104.43.4.2.el9uek.x86_64.rpm                    5.9 MB/s |  38 MB     00:06
(12/30): kernel-uek-modules-wireless-6.12.0-104.43.4.2.el9uek.x86_64.rpm                6.9 MB/s | 8.8 MB     00:01
(13/30): iputils-20210202-11.0.1.el9_6.3.x86_64.rpm                                     890 kB/s | 191 kB     00:00
(14/30): kernel-tools-libs-5.14.0-570.52.1.0.1.el9_6.x86_64.rpm                          10 MB/s | 1.8 MB     00:00
(15/30): kexec-tools-2.0.31-1.0.1.el9_6.x86_64.rpm                                      8.8 MB/s | 540 kB     00:00
(16/30): kernel-tools-5.14.0-570.52.1.0.1.el9_6.x86_64.rpm                              6.9 MB/s | 2.1 MB     00:00
(17/30): mcelog-207-1.0.1.el9.x86_64.rpm                                                1.2 MB/s |  90 kB     00:00
(18/30): systemd-252-51.0.6.el9_6.2.x86_64.rpm                                          7.6 MB/s | 4.6 MB     00:00
(19/30): python3-perf-5.14.0-570.52.1.0.1.el9_6.x86_64.rpm                              4.6 MB/s | 3.2 MB     00:00
(20/30): systemd-libs-252-51.0.6.el9_6.2.x86_64.rpm                                     6.5 MB/s | 684 kB     00:00
(21/30): systemd-rpm-macros-252-51.0.6.el9_6.2.noarch.rpm                               1.0 MB/s |  70 kB     00:00
(22/30): systemd-pam-252-51.0.6.el9_6.2.x86_64.rpm                                      1.2 MB/s | 278 kB     00:00
(23/30): vim-filesystem-8.2.2637-22.0.1.el9_6.1.noarch.rpm                              105 kB/s | 9.4 kB     00:00
(24/30): systemd-udev-252-51.0.6.el9_6.2.x86_64.rpm                                     4.8 MB/s | 2.2 MB     00:00
(25/30): vim-minimal-8.2.2637-22.0.1.el9_6.1.x86_64.rpm                                 2.2 MB/s | 676 kB     00:00
(26/30): kernel-headers-5.14.0-570.52.1.0.1.el9_6.x86_64.rpm                            9.8 MB/s | 4.3 MB     00:00
(27/30): perf-5.14.0-570.52.1.0.1.el9_6.x86_64.rpm                                      6.1 MB/s | 4.3 MB     00:00
(28/30): vim-enhanced-8.2.2637-22.0.1.el9_6.1.x86_64.rpm                                4.6 MB/s | 1.7 MB     00:00
(29/30): vim-common-8.2.2637-22.0.1.el9_6.1.x86_64.rpm                                  9.6 MB/s | 8.4 MB     00:00
(30/30): python39-oci-sdk-2.161.0-1.el9.x86_64.rpm                                       16 MB/s |  90 MB     00:05
------------------------------------------------------------------------------------------------------------------------
Total                                                                                    20 MB/s | 339 MB     00:16
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                                                                1/1
  Upgrading        : vim-filesystem-2:8.2.2637-22.0.1.el9_6.1.noarch                                               1/48
  Upgrading        : vim-common-2:8.2.2637-22.0.1.el9_6.1.x86_64                                                   2/48
  Upgrading        : systemd-rpm-macros-252-51.0.6.el9_6.2.noarch                                                  3/48
  Upgrading        : systemd-libs-252-51.0.6.el9_6.2.x86_64                                                        4/48
  Running scriptlet: systemd-libs-252-51.0.6.el9_6.2.x86_64                                                        4/48
  Upgrading        : systemd-pam-252-51.0.6.el9_6.2.x86_64                                                         5/48
  Running scriptlet: systemd-252-51.0.6.el9_6.2.x86_64                                                             6/48
  Upgrading        : systemd-252-51.0.6.el9_6.2.x86_64                                                             6/48
  Running scriptlet: systemd-252-51.0.6.el9_6.2.x86_64                                                             6/48
  Upgrading        : systemd-udev-252-51.0.6.el9_6.2.x86_64                                                        7/48
  Running scriptlet: systemd-udev-252-51.0.6.el9_6.2.x86_64                                                        7/48
  Installing       : kernel-modules-core-5.14.0-570.52.1.0.1.el9_6.x86_64                                          8/48
  Installing       : kernel-core-5.14.0-570.52.1.0.1.el9_6.x86_64                                                  9/48
  Running scriptlet: kernel-core-5.14.0-570.52.1.0.1.el9_6.x86_64                                                  9/48
  Installing       : kernel-uek-modules-core-6.12.0-104.43.4.2.el9uek.x86_64                                      10/48
  Running scriptlet: kernel-uek-core-6.12.0-104.43.4.2.el9uek.x86_64                                              11/48
  Installing       : kernel-uek-core-6.12.0-104.43.4.2.el9uek.x86_64                                              11/48
  Running scriptlet: kernel-uek-core-6.12.0-104.43.4.2.el9uek.x86_64                                              11/48
  Installing       : kernel-uek-modules-6.12.0-104.43.4.2.el9uek.x86_64                                           12/48
  Running scriptlet: kernel-uek-modules-6.12.0-104.43.4.2.el9uek.x86_64                                           12/48
  Installing       : kernel-uek-modules-desktop-6.12.0-104.43.4.2.el9uek.x86_64                                   13/48
  Running scriptlet: kernel-uek-modules-desktop-6.12.0-104.43.4.2.el9uek.x86_64                                   13/48
  Installing       : kernel-uek-modules-extra-netfilter-6.12.0-104.43.4.2.el9uek.x86_64                           14/48
  Running scriptlet: kernel-uek-modules-extra-netfilter-6.12.0-104.43.4.2.el9uek.x86_64                           14/48
  Installing       : kernel-uek-modules-usb-6.12.0-104.43.4.2.el9uek.x86_64                                       15/48
  Running scriptlet: kernel-uek-modules-usb-6.12.0-104.43.4.2.el9uek.x86_64                                       15/48
  Installing       : kernel-uek-modules-wireless-6.12.0-104.43.4.2.el9uek.x86_64                                  16/48
  Running scriptlet: kernel-uek-modules-wireless-6.12.0-104.43.4.2.el9uek.x86_64                                  16/48
  Installing       : kernel-modules-5.14.0-570.52.1.0.1.el9_6.x86_64                                              17/48
  Running scriptlet: kernel-modules-5.14.0-570.52.1.0.1.el9_6.x86_64                                              17/48
  Upgrading        : kernel-tools-libs-5.14.0-570.52.1.0.1.el9_6.x86_64                                           18/48
  Running scriptlet: kernel-tools-libs-5.14.0-570.52.1.0.1.el9_6.x86_64                                           18/48
  Upgrading        : kernel-tools-5.14.0-570.52.1.0.1.el9_6.x86_64                                                19/48
  Running scriptlet: kernel-tools-5.14.0-570.52.1.0.1.el9_6.x86_64                                                19/48
  Installing       : kernel-5.14.0-570.52.1.0.1.el9_6.x86_64                                                      20/48
  Installing       : kernel-uek-6.12.0-104.43.4.2.el9uek.x86_64                                                   21/48
  Upgrading        : kexec-tools-2.0.31-1.0.1.el9_6.x86_64                                                        22/48
warning: /etc/kdump.conf created as /etc/kdump.conf.rpmnew
warning: /etc/sysconfig/kdump created as /etc/sysconfig/kdump.rpmnew

  Running scriptlet: kexec-tools-2.0.31-1.0.1.el9_6.x86_64                                                        22/48
  Upgrading        : iputils-20210202-11.0.1.el9_6.3.x86_64                                                       23/48
  Running scriptlet: iputils-20210202-11.0.1.el9_6.3.x86_64                                                       23/48
  Upgrading        : mcelog-3:207-1.0.1.el9.x86_64                                                                24/48
  Running scriptlet: mcelog-3:207-1.0.1.el9.x86_64                                                                24/48
  Upgrading        : vim-enhanced-2:8.2.2637-22.0.1.el9_6.1.x86_64                                                25/48
  Upgrading        : perf-5.14.0-570.52.1.0.1.el9_6.x86_64                                                        26/48
  Upgrading        : kernel-headers-5.14.0-570.52.1.0.1.el9_6.x86_64                                              27/48
  Upgrading        : vim-minimal-2:8.2.2637-22.0.1.el9_6.1.x86_64                                                 28/48
  Upgrading        : python3-perf-5.14.0-570.52.1.0.1.el9_6.x86_64                                                29/48
  Upgrading        : python39-oci-sdk-2.161.0-1.el9.x86_64                                                        30/48
  Cleanup          : kernel-headers-5.14.0-570.51.1.0.1.el9_6.x86_64                                              31/48
  Cleanup          : python39-oci-sdk-2.160.3-1.el9.x86_64                                                        32/48
  Running scriptlet: mcelog-3:204-1.0.1.el9.x86_64                                                                33/48
  Cleanup          : mcelog-3:204-1.0.1.el9.x86_64                                                                33/48
  Running scriptlet: mcelog-3:204-1.0.1.el9.x86_64                                                                33/48
  Running scriptlet: kernel-tools-5.14.0-570.51.1.0.1.el9_6.x86_64                                                34/48
  Cleanup          : kernel-tools-5.14.0-570.51.1.0.1.el9_6.x86_64                                                34/48
  Running scriptlet: kernel-tools-5.14.0-570.51.1.0.1.el9_6.x86_64                                                34/48
  Cleanup          : vim-enhanced-2:8.2.2637-22.0.1.el9_6.x86_64                                                  35/48
  Cleanup          : vim-common-2:8.2.2637-22.0.1.el9_6.x86_64                                                    36/48
  Running scriptlet: kexec-tools-2.0.31-1.0.1.el9.x86_64                                                          37/48
  Cleanup          : kexec-tools-2.0.31-1.0.1.el9.x86_64                                                          37/48
  Running scriptlet: kexec-tools-2.0.31-1.0.1.el9.x86_64                                                          37/48
  Running scriptlet: systemd-udev-252-51.0.4.el9_6.2.x86_64                                                       38/48
  Cleanup          : systemd-udev-252-51.0.4.el9_6.2.x86_64                                                       38/48
  Running scriptlet: systemd-udev-252-51.0.4.el9_6.2.x86_64                                                       38/48
  Running scriptlet: iputils-20210202-11.0.1.el9_6.1.x86_64                                                       39/48
  Cleanup          : iputils-20210202-11.0.1.el9_6.1.x86_64                                                       39/48
  Running scriptlet: iputils-20210202-11.0.1.el9_6.1.x86_64                                                       39/48
  Cleanup          : vim-filesystem-2:8.2.2637-22.0.1.el9_6.noarch                                                40/48
  Cleanup          : systemd-252-51.0.4.el9_6.2.x86_64                                                            41/48
  Running scriptlet: systemd-252-51.0.4.el9_6.2.x86_64                                                            41/48
  Cleanup          : systemd-rpm-macros-252-51.0.4.el9_6.2.noarch                                                 42/48
  Cleanup          : systemd-libs-252-51.0.4.el9_6.2.x86_64                                                       43/48
  Cleanup          : systemd-pam-252-51.0.4.el9_6.2.x86_64                                                        44/48
  Cleanup          : kernel-tools-libs-5.14.0-570.51.1.0.1.el9_6.x86_64                                           45/48
  Running scriptlet: kernel-tools-libs-5.14.0-570.51.1.0.1.el9_6.x86_64                                           45/48
  Cleanup          : perf-5.14.0-570.51.1.0.1.el9_6.x86_64                                                        46/48
  Cleanup          : vim-minimal-2:8.2.2637-22.0.1.el9_6.x86_64                                                   47/48
  Cleanup          : python3-perf-5.14.0-570.51.1.0.1.el9_6.x86_64                                                48/48
  Running scriptlet: kernel-modules-core-5.14.0-570.52.1.0.1.el9_6.x86_64                                         48/48
  Running scriptlet: kernel-core-5.14.0-570.52.1.0.1.el9_6.x86_64                                                 48/48
2025-10-15 15:46:57,483 - INFO - Processing directory: /var/cache/uptrack/Linux/x86_64
2025-10-15 15:46:57,885 - INFO - Kept: /var/cache/uptrack/Linux/x86_64/6.12.0-103.40.4.2.el9uek.x86_64
2025-10-15 15:46:57,885 - INFO - Directory cleaned up successfully: /var/cache/uptrack

  Running scriptlet: kernel-uek-modules-core-6.12.0-104.43.4.2.el9uek.x86_64                                      48/48
  Running scriptlet: kernel-uek-core-6.12.0-104.43.4.2.el9uek.x86_64                                              48/48
2025-10-15 15:51:06,851 - INFO - Processing directory: /var/cache/uptrack/Linux/x86_64
2025-10-15 15:51:07,278 - INFO - Kept: /var/cache/uptrack/Linux/x86_64/6.12.0-103.40.4.2.el9uek.x86_64
2025-10-15 15:51:07,278 - INFO - Directory cleaned up successfully: /var/cache/uptrack

  Running scriptlet: kernel-uek-modules-6.12.0-104.43.4.2.el9uek.x86_64                                           48/48
  Running scriptlet: kernel-modules-5.14.0-570.52.1.0.1.el9_6.x86_64                                              48/48
  Running scriptlet: kexec-tools-2.0.31-1.0.1.el9_6.x86_64                                                        48/48
  Running scriptlet: python3-perf-5.14.0-570.51.1.0.1.el9_6.x86_64                                                48/48
  Verifying        : kernel-5.14.0-570.52.1.0.1.el9_6.x86_64                                                       1/48
  Verifying        : kernel-core-5.14.0-570.52.1.0.1.el9_6.x86_64                                                  2/48
  Verifying        : kernel-modules-5.14.0-570.52.1.0.1.el9_6.x86_64                                               3/48
  Verifying        : kernel-modules-core-5.14.0-570.52.1.0.1.el9_6.x86_64                                          4/48
  Verifying        : kernel-uek-6.12.0-104.43.4.2.el9uek.x86_64                                                    5/48
  Verifying        : kernel-uek-core-6.12.0-104.43.4.2.el9uek.x86_64                                               6/48
  Verifying        : kernel-uek-modules-6.12.0-104.43.4.2.el9uek.x86_64                                            7/48
  Verifying        : kernel-uek-modules-core-6.12.0-104.43.4.2.el9uek.x86_64                                       8/48
  Verifying        : kernel-uek-modules-desktop-6.12.0-104.43.4.2.el9uek.x86_64                                    9/48
  Verifying        : kernel-uek-modules-extra-netfilter-6.12.0-104.43.4.2.el9uek.x86_64                           10/48
  Verifying        : kernel-uek-modules-usb-6.12.0-104.43.4.2.el9uek.x86_64                                       11/48
  Verifying        : kernel-uek-modules-wireless-6.12.0-104.43.4.2.el9uek.x86_64                                  12/48
  Verifying        : python39-oci-sdk-2.161.0-1.el9.x86_64                                                        13/48
  Verifying        : python39-oci-sdk-2.160.3-1.el9.x86_64                                                        14/48
  Verifying        : iputils-20210202-11.0.1.el9_6.3.x86_64                                                       15/48
  Verifying        : iputils-20210202-11.0.1.el9_6.1.x86_64                                                       16/48
  Verifying        : kernel-tools-5.14.0-570.52.1.0.1.el9_6.x86_64                                                17/48
  Verifying        : kernel-tools-5.14.0-570.51.1.0.1.el9_6.x86_64                                                18/48
  Verifying        : kernel-tools-libs-5.14.0-570.52.1.0.1.el9_6.x86_64                                           19/48
  Verifying        : kernel-tools-libs-5.14.0-570.51.1.0.1.el9_6.x86_64                                           20/48
  Verifying        : kexec-tools-2.0.31-1.0.1.el9_6.x86_64                                                        21/48
  Verifying        : kexec-tools-2.0.31-1.0.1.el9.x86_64                                                          22/48
  Verifying        : mcelog-3:207-1.0.1.el9.x86_64                                                                23/48
  Verifying        : mcelog-3:204-1.0.1.el9.x86_64                                                                24/48
  Verifying        : python3-perf-5.14.0-570.52.1.0.1.el9_6.x86_64                                                25/48
  Verifying        : python3-perf-5.14.0-570.51.1.0.1.el9_6.x86_64                                                26/48
  Verifying        : systemd-252-51.0.6.el9_6.2.x86_64                                                            27/48
  Verifying        : systemd-252-51.0.4.el9_6.2.x86_64                                                            28/48
  Verifying        : systemd-libs-252-51.0.6.el9_6.2.x86_64                                                       29/48
  Verifying        : systemd-libs-252-51.0.4.el9_6.2.x86_64                                                       30/48
  Verifying        : systemd-pam-252-51.0.6.el9_6.2.x86_64                                                        31/48
  Verifying        : systemd-pam-252-51.0.4.el9_6.2.x86_64                                                        32/48
  Verifying        : systemd-rpm-macros-252-51.0.6.el9_6.2.noarch                                                 33/48
  Verifying        : systemd-rpm-macros-252-51.0.4.el9_6.2.noarch                                                 34/48
  Verifying        : systemd-udev-252-51.0.6.el9_6.2.x86_64                                                       35/48
  Verifying        : systemd-udev-252-51.0.4.el9_6.2.x86_64                                                       36/48
  Verifying        : vim-filesystem-2:8.2.2637-22.0.1.el9_6.1.noarch                                              37/48
  Verifying        : vim-filesystem-2:8.2.2637-22.0.1.el9_6.noarch                                                38/48
  Verifying        : vim-minimal-2:8.2.2637-22.0.1.el9_6.1.x86_64                                                 39/48
  Verifying        : vim-minimal-2:8.2.2637-22.0.1.el9_6.x86_64                                                   40/48
  Verifying        : kernel-headers-5.14.0-570.52.1.0.1.el9_6.x86_64                                              41/48
  Verifying        : kernel-headers-5.14.0-570.51.1.0.1.el9_6.x86_64                                              42/48
  Verifying        : perf-5.14.0-570.52.1.0.1.el9_6.x86_64                                                        43/48
  Verifying        : perf-5.14.0-570.51.1.0.1.el9_6.x86_64                                                        44/48
  Verifying        : vim-common-2:8.2.2637-22.0.1.el9_6.1.x86_64                                                  45/48
  Verifying        : vim-common-2:8.2.2637-22.0.1.el9_6.x86_64                                                    46/48
  Verifying        : vim-enhanced-2:8.2.2637-22.0.1.el9_6.1.x86_64                                                47/48
  Verifying        : vim-enhanced-2:8.2.2637-22.0.1.el9_6.x86_64                                                  48/48

Upgraded:
  iputils-20210202-11.0.1.el9_6.3.x86_64                    kernel-headers-5.14.0-570.52.1.0.1.el9_6.x86_64
  kernel-tools-5.14.0-570.52.1.0.1.el9_6.x86_64             kernel-tools-libs-5.14.0-570.52.1.0.1.el9_6.x86_64
  kexec-tools-2.0.31-1.0.1.el9_6.x86_64                     mcelog-3:207-1.0.1.el9.x86_64
  perf-5.14.0-570.52.1.0.1.el9_6.x86_64                     python3-perf-5.14.0-570.52.1.0.1.el9_6.x86_64
  python39-oci-sdk-2.161.0-1.el9.x86_64                     systemd-252-51.0.6.el9_6.2.x86_64
  systemd-libs-252-51.0.6.el9_6.2.x86_64                    systemd-pam-252-51.0.6.el9_6.2.x86_64
  systemd-rpm-macros-252-51.0.6.el9_6.2.noarch              systemd-udev-252-51.0.6.el9_6.2.x86_64
  vim-common-2:8.2.2637-22.0.1.el9_6.1.x86_64               vim-enhanced-2:8.2.2637-22.0.1.el9_6.1.x86_64
  vim-filesystem-2:8.2.2637-22.0.1.el9_6.1.noarch           vim-minimal-2:8.2.2637-22.0.1.el9_6.1.x86_64
Installed:
  kernel-5.14.0-570.52.1.0.1.el9_6.x86_64
  kernel-core-5.14.0-570.52.1.0.1.el9_6.x86_64
  kernel-modules-5.14.0-570.52.1.0.1.el9_6.x86_64
  kernel-modules-core-5.14.0-570.52.1.0.1.el9_6.x86_64
  kernel-uek-6.12.0-104.43.4.2.el9uek.x86_64
  kernel-uek-core-6.12.0-104.43.4.2.el9uek.x86_64
  kernel-uek-modules-6.12.0-104.43.4.2.el9uek.x86_64
  kernel-uek-modules-core-6.12.0-104.43.4.2.el9uek.x86_64
  kernel-uek-modules-desktop-6.12.0-104.43.4.2.el9uek.x86_64
  kernel-uek-modules-extra-netfilter-6.12.0-104.43.4.2.el9uek.x86_64
  kernel-uek-modules-usb-6.12.0-104.43.4.2.el9uek.x86_64
  kernel-uek-modules-wireless-6.12.0-104.43.4.2.el9uek.x86_64

Complete!
[opc@LennoxsDomain ~]$ client_loop: send disconnect: Connection reset
PS C:\WINDOWS\system32>
Coding Day 4:
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

Install the latest PowerShell for new features and improvements! https://aka.ms/PSWindows

PS C:\WINDOWS\system32> ssh -i C:\Users\lenno\.ssh\ssh-key-2025-10-05.key opc@157.151.194.68
Last login: Wed Oct 15 15:32:02 2025 from 204.126.178.254
[opc@LennoxsDomain ~]$ sudo yum install -y nodejs
Last metadata expiration check: 2:16:50 ago on Thu 16 Oct 2025 08:15:45 PM GMT.
Dependencies resolved.
========================================================================================================================
 Package                     Architecture      Version                                   Repository                Size
========================================================================================================================
Installing:
 nodejs                      x86_64            1:16.20.2-8.0.1.el9_4                     ol9_appstream            122 k
Installing dependencies:
 nodejs-libs                 x86_64            1:16.20.2-8.0.1.el9_4                     ol9_appstream             14 M
Installing weak dependencies:
 nodejs-docs                 noarch            1:16.20.2-8.0.1.el9_4                     ol9_appstream            7.8 M
 nodejs-full-i18n            x86_64            1:16.20.2-8.0.1.el9_4                     ol9_appstream            8.2 M
 npm                         x86_64            1:8.19.4-1.16.20.2.8.0.1.el9_4            ol9_appstream            3.4 M

Transaction Summary
========================================================================================================================
Install  5 Packages

Total download size: 34 M
Installed size: 168 M
Downloading Packages:
(1/5): nodejs-16.20.2-8.0.1.el9_4.x86_64.rpm                                            520 kB/s | 122 kB     00:00
(2/5): nodejs-full-i18n-16.20.2-8.0.1.el9_4.x86_64.rpm                                  6.1 MB/s | 8.2 MB     00:01
(3/5): nodejs-docs-16.20.2-8.0.1.el9_4.noarch.rpm                                       5.5 MB/s | 7.8 MB     00:01
(4/5): npm-8.19.4-1.16.20.2.8.0.1.el9_4.x86_64.rpm                                      9.5 MB/s | 3.4 MB     00:00
(5/5): nodejs-libs-16.20.2-8.0.1.el9_4.x86_64.rpm                                       8.2 MB/s |  14 MB     00:01
------------------------------------------------------------------------------------------------------------------------
Total                                                                                    17 MB/s |  34 MB     00:02
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Running scriptlet: npm-1:8.19.4-1.16.20.2.8.0.1.el9_4.x86_64                                                      1/1
  Preparing        :                                                                                                1/1
  Installing       : nodejs-libs-1:16.20.2-8.0.1.el9_4.x86_64                                                       1/5
  Installing       : nodejs-docs-1:16.20.2-8.0.1.el9_4.noarch                                                       2/5
  Installing       : nodejs-full-i18n-1:16.20.2-8.0.1.el9_4.x86_64                                                  3/5
  Installing       : npm-1:8.19.4-1.16.20.2.8.0.1.el9_4.x86_64                                                      4/5
  Installing       : nodejs-1:16.20.2-8.0.1.el9_4.x86_64                                                            5/5
  Running scriptlet: nodejs-1:16.20.2-8.0.1.el9_4.x86_64                                                            5/5
  Verifying        : nodejs-1:16.20.2-8.0.1.el9_4.x86_64                                                            1/5
  Verifying        : nodejs-docs-1:16.20.2-8.0.1.el9_4.noarch                                                       2/5
  Verifying        : nodejs-full-i18n-1:16.20.2-8.0.1.el9_4.x86_64                                                  3/5
  Verifying        : nodejs-libs-1:16.20.2-8.0.1.el9_4.x86_64                                                       4/5
  Verifying        : npm-1:8.19.4-1.16.20.2.8.0.1.el9_4.x86_64                                                      5/5

Installed:
  nodejs-1:16.20.2-8.0.1.el9_4.x86_64                           nodejs-docs-1:16.20.2-8.0.1.el9_4.noarch
  nodejs-full-i18n-1:16.20.2-8.0.1.el9_4.x86_64                 nodejs-libs-1:16.20.2-8.0.1.el9_4.x86_64
  npm-1:8.19.4-1.16.20.2.8.0.1.el9_4.x86_64

Complete!
[opc@LennoxsDomain ~]$ node --version
v16.20.2
[opc@LennoxsDomain ~]$ mkdir node-hello-app
[opc@LennoxsDomain ~]$ cd node-hello-app
[opc@LennoxsDomain node-hello-app]$ npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help init` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (hello-app) node-hello-app
version: (1.0.0)
description: Node Express Hello application
entry point: (index.js) app.js
test command:
git repository: https://github.com/ewilson0715/ewilson0715.github.io
[1]+  Stopped                 npm init
[opc@LennoxsDomain node-hello-app]$ npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help init` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (hello-app) node-hello-app
version: (1.0.0)
description: Node Express Hello application
entry point: (index.js) app.js
test command:
git repository: git@github.com:ewilson0715/ewilson0715.github.io.git
keywords:
author: Lennox <lennoxwilson111@gmail.com>
license: (ISC) UPL-1.0
About to write to /home/opc/node-hello-app/package.json:

{
  "name": "node-hello-app",
  "version": "1.0.0",
  "description": "Node Express Hello application",
  "main": "app.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "git+ssh://git@github.com/ewilson0715/ewilson0715.github.io.git"
  },
  "author": "Lennox <lennoxwilson111@gmail.com>",
  "license": "UPL-1.0",
  "bugs": {
    "url": "https://github.com/ewilson0715/ewilson0715.github.io/issues"
  },
  "homepage": "https://github.com/ewilson0715/ewilson0715.github.io#readme"
}


Is this OK? (yes) yes
[opc@LennoxsDomain node-hello-app]$ npm install express --save
npm WARN EBADENGINE Unsupported engine {
npm WARN EBADENGINE   package: 'express@5.1.0',
npm WARN EBADENGINE   required: { node: '>= 18' },
npm WARN EBADENGINE   current: { node: 'v16.20.2', npm: '8.19.4' }
npm WARN EBADENGINE }
npm WARN EBADENGINE Unsupported engine {
npm WARN EBADENGINE   package: 'body-parser@2.2.0',
npm WARN EBADENGINE   required: { node: '>=18' },
npm WARN EBADENGINE   current: { node: 'v16.20.2', npm: '8.19.4' }
npm WARN EBADENGINE }
npm WARN EBADENGINE Unsupported engine {
npm WARN EBADENGINE   package: 'merge-descriptors@2.0.0',
npm WARN EBADENGINE   required: { node: '>=18' },
npm WARN EBADENGINE   current: { node: 'v16.20.2', npm: '8.19.4' }
npm WARN EBADENGINE }
npm WARN EBADENGINE Unsupported engine {
npm WARN EBADENGINE   package: 'router@2.2.0',
npm WARN EBADENGINE   required: { node: '>= 18' },
npm WARN EBADENGINE   current: { node: 'v16.20.2', npm: '8.19.4' }
npm WARN EBADENGINE }
npm WARN EBADENGINE Unsupported engine {
npm WARN EBADENGINE   package: 'send@1.2.0',
npm WARN EBADENGINE   required: { node: '>= 18' },
npm WARN EBADENGINE   current: { node: 'v16.20.2', npm: '8.19.4' }
npm WARN EBADENGINE }
npm WARN EBADENGINE Unsupported engine {
npm WARN EBADENGINE   package: 'serve-static@2.2.0',
npm WARN EBADENGINE   required: { node: '>= 18' },
npm WARN EBADENGINE   current: { node: 'v16.20.2', npm: '8.19.4' }
npm WARN EBADENGINE }

added 68 packages, and audited 69 packages in 9s

16 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
[opc@LennoxsDomain node-hello-app]$ cat package.json
{
  "name": "node-hello-app",
  "version": "1.0.0",
  "description": "Node Express Hello application",
  "main": "app.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "git+ssh://git@github.com/ewilson0715/ewilson0715.github.io.git"
  },
  "author": "Lennox <lennoxwilson111@gmail.com>",
  "license": "UPL-1.0",
  "bugs": {
    "url": "https://github.com/ewilson0715/ewilson0715.github.io/issues"
  },
  "homepage": "https://github.com/ewilson0715/ewilson0715.github.io#readme",
  "dependencies": {
    "express": "^5.1.0"
  }
}
[opc@LennoxsDomain node-hello-app]$ "dependencies": {
-bash: dependencies:: command not found
[opc@LennoxsDomain node-hello-app]$ "dependencies": {
-bash: dependencies:: command not found
[opc@LennoxsDomain node-hello-app]$ "dependencies": {
-bash: dependencies:: command not found
[opc@LennoxsDomain node-hello-app]$ "dependencies": { "express": "^4.17.1" }
-bash: dependencies:: command not found
[opc@LennoxsDomain node-hello-app]$ vi app.js
[opc@LennoxsDomain node-hello-app]$ vi app.js
[opc@LennoxsDomain node-hello-app]$ node app.js
Hello World app listening on port 3000!

PART 2:
PS C:\WINDOWS\system32> ssh -i C:\Users\lenno\.ssh\ssh-key-2025-10-05.key opc@157.151.194.68
Last login: Thu Oct 16 23:17:29 2025 from 204.126.178.254
[opc@LennoxsDomain ~]$ cd node-hello-app
[opc@LennoxsDomain node-hello-app]$ curl -X GET http://localhost:3000
Hello World![opc@LennoxsDomain node-hello-app]$

Coding Day 5:

Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

Install the latest PowerShell for new features and improvements! https://aka.ms/PSWindows

PS C:\WINDOWS\system32> shh -i C:\Users\lenno\.ssh\ssh-key-2025-10-05.key opc@157.151.194.68
shh : The term 'shh' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the
spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ shh -i C:\Users\lenno\.ssh\ssh-key-2025-10-05.key opc@157.151.194.68
+ ~~~
    + CategoryInfo          : ObjectNotFound: (shh:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException

PS C:\WINDOWS\system32> ssh -i C:\Users\lenno\.ssh\ssh-key-2025-10-05.key opc@157.151.194.68
Last login: Tue Oct 28 23:38:03 2025 from 204.126.178.254
[opc@LennoxsDomain ~]$ cd node-hello-app
[opc@LennoxsDomain node-hello-app]$ curl -X GET http://localhost:3000
Hello World![opc@LennoxsDomain node-hello-app]$ cd /
[opc@LennoxsDomain /]$ ls
afs  bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  swapfile  sys  tmp  usr  var
[opc@LennoxsDomain /]$ cd var
[opc@LennoxsDomain var]$ ls
account  cache  db     ftp    kerberos  local  log   nis   opt       run    tmp
adm      crash  empty  games  lib       lock   mail  oled  preserve  spool  yp
[opc@LennoxsDomain var]$ cd /
[opc@LennoxsDomain /]$ cd node-hello-app
-bash: cd: node-hello-app: No such file or directory
[opc@LennoxsDomain /]$ cd ~/node-hello-app/
[opc@LennoxsDomain node-hello-app]$ ls
app.js  node_modules  package.json  package-lock.json
[opc@LennoxsDomain node-hello-app]$ more package.json
{
  "name": "node-hello-app",
  "version": "1.0.0",
  "description": "Node Express Hello application",
  "main": "app.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "git+ssh://git@github.com/ewilson0715/ewilson0715.github.io.git"
  },
  "author": "Lennox <lennoxwilson111@gmail.com>",
  "license": "UPL-1.0",
  "bugs": {
    "url": "https://github.com/ewilson0715/ewilson0715.github.io/issues"
  },
  "homepage": "https://github.com/ewilson0715/ewilson0715.github.io#readme",
  "dependencies": {
    "express": "^5.1.0"
  }
}
[opc@LennoxsDomain node-hello-app]$ nano app.js
[opc@LennoxsDomain node-hello-app]$ [opc@LennoxsDomain node-hello-app]$ nano index.html
[opc@LennoxsDomain node-hello-app]$ [opc@LennoxsDomain node-hello-app]$ nano index.js
[opc@LennoxsDomain node-hello-app]$ [opc@LennoxsDomain node-hello-app]$ nano package.json
[opc@LennoxsDomain node-hello-app]$
