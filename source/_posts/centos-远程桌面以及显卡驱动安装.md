---
title: centos 远程桌面以及显卡驱动安装
date: 2023-08-22 18:11:41
tags:
---

```bash
Last login: Tue Aug 22 17:20:39 on ttys000


Identity added: /Users/andrew/Documents/zengjunjie-jumpserver.pem (/Users/andrew/Documents/zengjunjie-jumpserver.pem)
(base) andrew@imac:~#
(base) andrew@imac:~#
(base) andrew@imac:~#ssh root@10.0.0.119
root@10.0.0.119's password: 
Last login: Tue Aug 22 17:43:40 2023 from 10.0.0.202
[root@centos ~]# 
[root@centos ~]# 
[root@centos ~]# 
[root@centos ~]# 
[root@centos ~]# 
[root@centos ~]# useradd -m andrew
[root@centos ~]# passwd andrew
Changing password for user andrew.
New password: 
BAD PASSWORD: The password is shorter than 8 characters
Retype new password: 
Sorry, passwords do not match.
New password: 
[root@centos ~]# ^C
[root@centos ~]# passwd andrew
Changing password for user andrew.
New password: 
BAD PASSWORD: The password is shorter than 8 characters
Retype new password: 
passwd: all authentication tokens updated successfully.
[root@centos ~]# 
[root@centos ~]# 
[root@centos ~]# yum install tigervnc-server
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirrors.tuna.tsinghua.edu.cn
 * epel: mirrors.tuna.tsinghua.edu.cn
 * extras: mirrors.bupt.edu.cn
 * updates: mirrors.tuna.tsinghua.edu.cn
Resolving Dependencies
--> Running transaction check
---> Package tigervnc-server.x86_64 0:1.8.0-25.el7_9 will be installed
--> Processing Dependency: xorg-x11-xinit for package: tigervnc-server-1.8.0-25.el7_9.x86_64
--> Processing Dependency: xorg-x11-xauth for package: tigervnc-server-1.8.0-25.el7_9.x86_64
--> Processing Dependency: tigervnc-server-minimal for package: tigervnc-server-1.8.0-25.el7_9.x86_64
--> Processing Dependency: libgnutls.so.28(GNUTLS_2_12)(64bit) for package: tigervnc-server-1.8.0-25.el7_9.x86_64
--> Processing Dependency: libgnutls.so.28(GNUTLS_1_4)(64bit) for package: tigervnc-server-1.8.0-25.el7_9.x86_64
--> Processing Dependency: libpixman-1.so.0()(64bit) for package: tigervnc-server-1.8.0-25.el7_9.x86_64
--> Processing Dependency: libgnutls.so.28()(64bit) for package: tigervnc-server-1.8.0-25.el7_9.x86_64
--> Processing Dependency: libXtst.so.6()(64bit) for package: tigervnc-server-1.8.0-25.el7_9.x86_64
--> Processing Dependency: libXext.so.6()(64bit) for package: tigervnc-server-1.8.0-25.el7_9.x86_64
--> Processing Dependency: libXdamage.so.1()(64bit) for package: tigervnc-server-1.8.0-25.el7_9.x86_64
--> Processing Dependency: libX11.so.6()(64bit) for package: tigervnc-server-1.8.0-25.el7_9.x86_64
--> Processing Dependency: libSM.so.6()(64bit) for package: tigervnc-server-1.8.0-25.el7_9.x86_64
--> Processing Dependency: libICE.so.6()(64bit) for package: tigervnc-server-1.8.0-25.el7_9.x86_64
--> Running transaction check
---> Package gnutls.x86_64 0:3.3.29-9.el7_6 will be installed
--> Processing Dependency: trousers >= 0.3.11.2 for package: gnutls-3.3.29-9.el7_6.x86_64
--> Processing Dependency: libnettle.so.4()(64bit) for package: gnutls-3.3.29-9.el7_6.x86_64
--> Processing Dependency: libhogweed.so.2()(64bit) for package: gnutls-3.3.29-9.el7_6.x86_64
---> Package libICE.x86_64 0:1.0.9-9.el7 will be installed
---> Package libSM.x86_64 0:1.2.2-2.el7 will be installed
---> Package libX11.x86_64 0:1.6.7-4.el7_9 will be installed
--> Processing Dependency: libX11-common >= 1.6.7-4.el7_9 for package: libX11-1.6.7-4.el7_9.x86_64
--> Processing Dependency: libxcb.so.1()(64bit) for package: libX11-1.6.7-4.el7_9.x86_64
---> Package libXdamage.x86_64 0:1.1.4-4.1.el7 will be installed
--> Processing Dependency: libXfixes.so.3()(64bit) for package: libXdamage-1.1.4-4.1.el7.x86_64
---> Package libXext.x86_64 0:1.3.3-3.el7 will be installed
---> Package libXtst.x86_64 0:1.2.3-1.el7 will be installed
--> Processing Dependency: libXi.so.6()(64bit) for package: libXtst-1.2.3-1.el7.x86_64
---> Package pixman.x86_64 0:0.34.0-1.el7 will be installed
---> Package tigervnc-server-minimal.x86_64 0:1.8.0-25.el7_9 will be installed
--> Processing Dependency: xorg-x11-xkb-utils for package: tigervnc-server-minimal-1.8.0-25.el7_9.x86_64
--> Processing Dependency: xkeyboard-config for package: tigervnc-server-minimal-1.8.0-25.el7_9.x86_64
--> Processing Dependency: tigervnc-license for package: tigervnc-server-minimal-1.8.0-25.el7_9.x86_64
--> Processing Dependency: mesa-dri-drivers for package: tigervnc-server-minimal-1.8.0-25.el7_9.x86_64
--> Processing Dependency: libxshmfence.so.1()(64bit) for package: tigervnc-server-minimal-1.8.0-25.el7_9.x86_64
--> Processing Dependency: libXfont2.so.2()(64bit) for package: tigervnc-server-minimal-1.8.0-25.el7_9.x86_64
--> Processing Dependency: libXdmcp.so.6()(64bit) for package: tigervnc-server-minimal-1.8.0-25.el7_9.x86_64
--> Processing Dependency: libXau.so.6()(64bit) for package: tigervnc-server-minimal-1.8.0-25.el7_9.x86_64
--> Processing Dependency: libGL.so.1()(64bit) for package: tigervnc-server-minimal-1.8.0-25.el7_9.x86_64
---> Package xorg-x11-xauth.x86_64 1:1.0.9-1.el7 will be installed
--> Processing Dependency: libXmuu.so.1()(64bit) for package: 1:xorg-x11-xauth-1.0.9-1.el7.x86_64
---> Package xorg-x11-xinit.x86_64 0:1.3.4-2.el7 will be installed
--> Processing Dependency: xorg-x11-server-utils for package: xorg-x11-xinit-1.3.4-2.el7.x86_64
--> Running transaction check
---> Package libX11-common.noarch 0:1.6.7-4.el7_9 will be installed
---> Package libXau.x86_64 0:1.0.8-2.1.el7 will be installed
---> Package libXdmcp.x86_64 0:1.1.2-6.el7 will be installed
---> Package libXfixes.x86_64 0:5.0.3-1.el7 will be installed
---> Package libXfont2.x86_64 0:2.0.3-1.el7 will be installed
--> Processing Dependency: libfontenc.so.1()(64bit) for package: libXfont2-2.0.3-1.el7.x86_64
---> Package libXi.x86_64 0:1.7.9-1.el7 will be installed
---> Package libXmu.x86_64 0:1.1.2-2.el7 will be installed
--> Processing Dependency: libXt.so.6()(64bit) for package: libXmu-1.1.2-2.el7.x86_64
---> Package libglvnd-glx.x86_64 1:1.0.1-0.8.git5baa1e5.el7 will be installed
--> Processing Dependency: libglvnd(x86-64) = 1:1.0.1-0.8.git5baa1e5.el7 for package: 1:libglvnd-glx-1.0.1-0.8.git5baa1e5.el7.x86_64
--> Processing Dependency: mesa-libGL(x86-64) >= 13.0.4-1 for package: 1:libglvnd-glx-1.0.1-0.8.git5baa1e5.el7.x86_64
--> Processing Dependency: libGLdispatch.so.0()(64bit) for package: 1:libglvnd-glx-1.0.1-0.8.git5baa1e5.el7.x86_64
---> Package libxcb.x86_64 0:1.13-1.el7 will be installed
---> Package libxshmfence.x86_64 0:1.2-1.el7 will be installed
---> Package mesa-dri-drivers.x86_64 0:18.3.4-12.el7_9 will be installed
--> Processing Dependency: mesa-filesystem(x86-64) for package: mesa-dri-drivers-18.3.4-12.el7_9.x86_64
--> Processing Dependency: libLLVM-7-rhel.so(LLVM_7)(64bit) for package: mesa-dri-drivers-18.3.4-12.el7_9.x86_64
--> Processing Dependency: libglapi.so.0()(64bit) for package: mesa-dri-drivers-18.3.4-12.el7_9.x86_64
--> Processing Dependency: libLLVM-7-rhel.so()(64bit) for package: mesa-dri-drivers-18.3.4-12.el7_9.x86_64
---> Package nettle.x86_64 0:2.7.1-9.el7_9 will be installed
---> Package tigervnc-license.noarch 0:1.8.0-25.el7_9 will be installed
---> Package trousers.x86_64 0:0.3.14-2.el7 will be installed
---> Package xkeyboard-config.noarch 0:2.24-1.el7 will be installed
---> Package xorg-x11-server-utils.x86_64 0:7.7-20.el7 will be installed
--> Processing Dependency: libXxf86vm.so.1()(64bit) for package: xorg-x11-server-utils-7.7-20.el7.x86_64
--> Processing Dependency: libXxf86misc.so.1()(64bit) for package: xorg-x11-server-utils-7.7-20.el7.x86_64
--> Processing Dependency: libXrender.so.1()(64bit) for package: xorg-x11-server-utils-7.7-20.el7.x86_64
--> Processing Dependency: libXrandr.so.2()(64bit) for package: xorg-x11-server-utils-7.7-20.el7.x86_64
--> Processing Dependency: libXinerama.so.1()(64bit) for package: xorg-x11-server-utils-7.7-20.el7.x86_64
--> Processing Dependency: libXcursor.so.1()(64bit) for package: xorg-x11-server-utils-7.7-20.el7.x86_64
---> Package xorg-x11-xkb-utils.x86_64 0:7.7-14.el7 will be installed
--> Processing Dependency: libxkbfile.so.1()(64bit) for package: xorg-x11-xkb-utils-7.7-14.el7.x86_64
--> Running transaction check
---> Package libXcursor.x86_64 0:1.1.15-1.el7 will be installed
---> Package libXinerama.x86_64 0:1.1.3-2.1.el7 will be installed
---> Package libXrandr.x86_64 0:1.5.1-2.el7 will be installed
---> Package libXrender.x86_64 0:0.9.10-1.el7 will be installed
---> Package libXt.x86_64 0:1.1.5-3.el7 will be installed
---> Package libXxf86misc.x86_64 0:1.0.3-7.1.el7 will be installed
---> Package libXxf86vm.x86_64 0:1.1.4-1.el7 will be installed
---> Package libfontenc.x86_64 0:1.1.3-3.el7 will be installed
---> Package libglvnd.x86_64 1:1.0.1-0.8.git5baa1e5.el7 will be installed
---> Package libxkbfile.x86_64 0:1.0.9-3.el7 will be installed
---> Package llvm-private.x86_64 0:7.0.1-1.el7 will be installed
---> Package mesa-filesystem.x86_64 0:18.3.4-12.el7_9 will be installed
---> Package mesa-libGL.x86_64 0:18.3.4-12.el7_9 will be installed
---> Package mesa-libglapi.x86_64 0:18.3.4-12.el7_9 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

========================================================================================================================
 Package                            Arch              Version                                  Repository          Size
========================================================================================================================
Installing:
 tigervnc-server                    x86_64            1.8.0-25.el7_9                           updates            212 k
Installing for dependencies:
 gnutls                             x86_64            3.3.29-9.el7_6                           base               680 k
 libICE                             x86_64            1.0.9-9.el7                              base                66 k
 libSM                              x86_64            1.2.2-2.el7                              base                39 k
 libX11                             x86_64            1.6.7-4.el7_9                            updates            607 k
 libX11-common                      noarch            1.6.7-4.el7_9                            updates            164 k
 libXau                             x86_64            1.0.8-2.1.el7                            base                29 k
 libXcursor                         x86_64            1.1.15-1.el7                             base                30 k
 libXdamage                         x86_64            1.1.4-4.1.el7                            base                20 k
 libXdmcp                           x86_64            1.1.2-6.el7                              base                34 k
 libXext                            x86_64            1.3.3-3.el7                              base                39 k
 libXfixes                          x86_64            5.0.3-1.el7                              base                18 k
 libXfont2                          x86_64            2.0.3-1.el7                              base               143 k
 libXi                              x86_64            1.7.9-1.el7                              base                40 k
 libXinerama                        x86_64            1.1.3-2.1.el7                            base                14 k
 libXmu                             x86_64            1.1.2-2.el7                              base                71 k
 libXrandr                          x86_64            1.5.1-2.el7                              base                27 k
 libXrender                         x86_64            0.9.10-1.el7                             base                26 k
 libXt                              x86_64            1.1.5-3.el7                              base               173 k
 libXtst                            x86_64            1.2.3-1.el7                              base                20 k
 libXxf86misc                       x86_64            1.0.3-7.1.el7                            base                19 k
 libXxf86vm                         x86_64            1.1.4-1.el7                              base                18 k
 libfontenc                         x86_64            1.1.3-3.el7                              base                31 k
 libglvnd                           x86_64            1:1.0.1-0.8.git5baa1e5.el7               base                89 k
 libglvnd-glx                       x86_64            1:1.0.1-0.8.git5baa1e5.el7               base               125 k
 libxcb                             x86_64            1.13-1.el7                               base               214 k
 libxkbfile                         x86_64            1.0.9-3.el7                              base                83 k
 libxshmfence                       x86_64            1.2-1.el7                                base               7.2 k
 llvm-private                       x86_64            7.0.1-1.el7                              base                23 M
 mesa-dri-drivers                   x86_64            18.3.4-12.el7_9                          updates            7.2 M
 mesa-filesystem                    x86_64            18.3.4-12.el7_9                          updates             19 k
 mesa-libGL                         x86_64            18.3.4-12.el7_9                          updates            166 k
 mesa-libglapi                      x86_64            18.3.4-12.el7_9                          updates             46 k
 nettle                             x86_64            2.7.1-9.el7_9                            updates            328 k
 pixman                             x86_64            0.34.0-1.el7                             base               248 k
 tigervnc-license                   noarch            1.8.0-25.el7_9                           updates             31 k
 tigervnc-server-minimal            x86_64            1.8.0-25.el7_9                           updates            1.0 M
 trousers                           x86_64            0.3.14-2.el7                             base               289 k
 xkeyboard-config                   noarch            2.24-1.el7                               base               834 k
 xorg-x11-server-utils              x86_64            7.7-20.el7                               base               178 k
 xorg-x11-xauth                     x86_64            1:1.0.9-1.el7                            base                30 k
 xorg-x11-xinit                     x86_64            1.3.4-2.el7                              base                58 k
 xorg-x11-xkb-utils                 x86_64            7.7-14.el7                               base               103 k

Transaction Summary
========================================================================================================================
Install  1 Package (+42 Dependent packages)

Total download size: 36 M
Installed size: 122 M
Is this ok [y/d/N]: y
Downloading packages:
(1/43): libICE-1.0.9-9.el7.x86_64.rpm                                                            |  66 kB  00:00:00     
(2/43): libXau-1.0.8-2.1.el7.x86_64.rpm                                                          |  29 kB  00:00:00     
(3/43): libXcursor-1.1.15-1.el7.x86_64.rpm                                                       |  30 kB  00:00:00     
(4/43): libSM-1.2.2-2.el7.x86_64.rpm                                                             |  39 kB  00:00:00     
(5/43): libXdamage-1.1.4-4.1.el7.x86_64.rpm                                                      |  20 kB  00:00:00     
(6/43): libXext-1.3.3-3.el7.x86_64.rpm                                                           |  39 kB  00:00:00     
(7/43): libXdmcp-1.1.2-6.el7.x86_64.rpm                                                          |  34 kB  00:00:00     
(8/43): libXfixes-5.0.3-1.el7.x86_64.rpm                                                         |  18 kB  00:00:00     
(9/43): libXi-1.7.9-1.el7.x86_64.rpm                                                             |  40 kB  00:00:00     
(10/43): libXinerama-1.1.3-2.1.el7.x86_64.rpm                                                    |  14 kB  00:00:00     
(11/43): libX11-common-1.6.7-4.el7_9.noarch.rpm                                                  | 164 kB  00:00:00     
(12/43): libXfont2-2.0.3-1.el7.x86_64.rpm                                                        | 143 kB  00:00:00     
(13/43): libXmu-1.1.2-2.el7.x86_64.rpm                                                           |  71 kB  00:00:00     
(14/43): libXrender-0.9.10-1.el7.x86_64.rpm                                                      |  26 kB  00:00:00     
(15/43): libX11-1.6.7-4.el7_9.x86_64.rpm                                                         | 607 kB  00:00:00     
(16/43): libXtst-1.2.3-1.el7.x86_64.rpm                                                          |  20 kB  00:00:00     
(17/43): libXt-1.1.5-3.el7.x86_64.rpm                                                            | 173 kB  00:00:00     
(18/43): gnutls-3.3.29-9.el7_6.x86_64.rpm                                                        | 680 kB  00:00:00     
(19/43): libfontenc-1.1.3-3.el7.x86_64.rpm                                                       |  31 kB  00:00:00     
(20/43): libXxf86misc-1.0.3-7.1.el7.x86_64.rpm                                                   |  19 kB  00:00:00     
(21/43): libXxf86vm-1.1.4-1.el7.x86_64.rpm                                                       |  18 kB  00:00:00     
(22/43): libXrandr-1.5.1-2.el7.x86_64.rpm                                                        |  27 kB  00:00:00     
(23/43): libglvnd-glx-1.0.1-0.8.git5baa1e5.el7.x86_64.rpm                                        | 125 kB  00:00:00     
(24/43): libglvnd-1.0.1-0.8.git5baa1e5.el7.x86_64.rpm                                            |  89 kB  00:00:00     
(25/43): libxshmfence-1.2-1.el7.x86_64.rpm                                                       | 7.2 kB  00:00:00     
(26/43): libxcb-1.13-1.el7.x86_64.rpm                                                            | 214 kB  00:00:00     
(27/43): libxkbfile-1.0.9-3.el7.x86_64.rpm                                                       |  83 kB  00:00:00     
(28/43): mesa-filesystem-18.3.4-12.el7_9.x86_64.rpm                                              |  19 kB  00:00:00     
(29/43): mesa-libGL-18.3.4-12.el7_9.x86_64.rpm                                                   | 166 kB  00:00:00     
(30/43): mesa-libglapi-18.3.4-12.el7_9.x86_64.rpm                                                |  46 kB  00:00:00     
(31/43): nettle-2.7.1-9.el7_9.x86_64.rpm                                                         | 328 kB  00:00:00     
(32/43): tigervnc-license-1.8.0-25.el7_9.noarch.rpm                                              |  31 kB  00:00:00     
(33/43): tigervnc-server-1.8.0-25.el7_9.x86_64.rpm                                               | 212 kB  00:00:00     
(34/43): pixman-0.34.0-1.el7.x86_64.rpm                                                          | 248 kB  00:00:00     
(35/43): trousers-0.3.14-2.el7.x86_64.rpm                                                        | 289 kB  00:00:00     
(36/43): xorg-x11-server-utils-7.7-20.el7.x86_64.rpm                                             | 178 kB  00:00:00     
(37/43): tigervnc-server-minimal-1.8.0-25.el7_9.x86_64.rpm                                       | 1.0 MB  00:00:00     
(38/43): xorg-x11-xauth-1.0.9-1.el7.x86_64.rpm                                                   |  30 kB  00:00:00     
(39/43): xorg-x11-xinit-1.3.4-2.el7.x86_64.rpm                                                   |  58 kB  00:00:00     
(40/43): xorg-x11-xkb-utils-7.7-14.el7.x86_64.rpm                                                | 103 kB  00:00:00     
(41/43): xkeyboard-config-2.24-1.el7.noarch.rpm                                                  | 834 kB  00:00:00     
(42/43): mesa-dri-drivers-18.3.4-12.el7_9.x86_64.rpm                                             | 7.2 MB  00:00:01     
(43/43): llvm-private-7.0.1-1.el7.x86_64.rpm                                                     |  23 MB  00:00:03     
------------------------------------------------------------------------------------------------------------------------
Total                                                                                   9.0 MB/s |  36 MB  00:00:04     
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : libICE-1.0.9-9.el7.x86_64                                                                           1/43 
  Installing : libSM-1.2.2-2.el7.x86_64                                                                            2/43 
  Installing : libXau-1.0.8-2.1.el7.x86_64                                                                         3/43 
  Installing : libxcb-1.13-1.el7.x86_64                                                                            4/43 
  Installing : libxshmfence-1.2-1.el7.x86_64                                                                       5/43 
  Installing : nettle-2.7.1-9.el7_9.x86_64                                                                         6/43 
  Installing : mesa-libglapi-18.3.4-12.el7_9.x86_64                                                                7/43 
  Installing : pixman-0.34.0-1.el7.x86_64                                                                          8/43 
  Installing : libX11-common-1.6.7-4.el7_9.noarch                                                                  9/43 
  Installing : libX11-1.6.7-4.el7_9.x86_64                                                                        10/43 
  Installing : libXext-1.3.3-3.el7.x86_64                                                                         11/43 
  Installing : libXrender-0.9.10-1.el7.x86_64                                                                     12/43 
  Installing : libXfixes-5.0.3-1.el7.x86_64                                                                       13/43 
  Installing : libXdamage-1.1.4-4.1.el7.x86_64                                                                    14/43 
  Installing : libXi-1.7.9-1.el7.x86_64                                                                           15/43 
  Installing : libXxf86vm-1.1.4-1.el7.x86_64                                                                      16/43 
  Installing : libXt-1.1.5-3.el7.x86_64                                                                           17/43 
  Installing : libXmu-1.1.2-2.el7.x86_64                                                                          18/43 
  Installing : 1:xorg-x11-xauth-1.0.9-1.el7.x86_64                                                                19/43 
  Installing : libXtst-1.2.3-1.el7.x86_64                                                                         20/43 
  Installing : libXcursor-1.1.15-1.el7.x86_64                                                                     21/43 
  Installing : libXrandr-1.5.1-2.el7.x86_64                                                                       22/43 
  Installing : libXinerama-1.1.3-2.1.el7.x86_64                                                                   23/43 
  Installing : libXxf86misc-1.0.3-7.1.el7.x86_64                                                                  24/43 
  Installing : xorg-x11-server-utils-7.7-20.el7.x86_64                                                            25/43 
  Installing : xorg-x11-xinit-1.3.4-2.el7.x86_64                                                                  26/43 
  Installing : libxkbfile-1.0.9-3.el7.x86_64                                                                      27/43 
  Installing : xorg-x11-xkb-utils-7.7-14.el7.x86_64                                                               28/43 
  Installing : libfontenc-1.1.3-3.el7.x86_64                                                                      29/43 
  Installing : libXfont2-2.0.3-1.el7.x86_64                                                                       30/43 
  Installing : libXdmcp-1.1.2-6.el7.x86_64                                                                        31/43 
  Installing : 1:libglvnd-1.0.1-0.8.git5baa1e5.el7.x86_64                                                         32/43 
  Installing : 1:libglvnd-glx-1.0.1-0.8.git5baa1e5.el7.x86_64                                                     33/43 
  Installing : mesa-libGL-18.3.4-12.el7_9.x86_64                                                                  34/43 
  Installing : xkeyboard-config-2.24-1.el7.noarch                                                                 35/43 
  Installing : llvm-private-7.0.1-1.el7.x86_64                                                                    36/43 
  Installing : mesa-filesystem-18.3.4-12.el7_9.x86_64                                                             37/43 
  Installing : mesa-dri-drivers-18.3.4-12.el7_9.x86_64                                                            38/43 
  Installing : tigervnc-license-1.8.0-25.el7_9.noarch                                                             39/43 
  Installing : trousers-0.3.14-2.el7.x86_64                                                                       40/43 
  Installing : gnutls-3.3.29-9.el7_6.x86_64                                                                       41/43 
  Installing : tigervnc-server-minimal-1.8.0-25.el7_9.x86_64                                                      42/43 
  Installing : tigervnc-server-1.8.0-25.el7_9.x86_64                                                              43/43 
  Verifying  : libXext-1.3.3-3.el7.x86_64                                                                          1/43 
  Verifying  : trousers-0.3.14-2.el7.x86_64                                                                        2/43 
  Verifying  : libXi-1.7.9-1.el7.x86_64                                                                            3/43 
  Verifying  : libICE-1.0.9-9.el7.x86_64                                                                           4/43 
  Verifying  : libXinerama-1.1.3-2.1.el7.x86_64                                                                    5/43 
  Verifying  : libXrender-0.9.10-1.el7.x86_64                                                                      6/43 
  Verifying  : 1:libglvnd-glx-1.0.1-0.8.git5baa1e5.el7.x86_64                                                      7/43 
  Verifying  : libXxf86vm-1.1.4-1.el7.x86_64                                                                       8/43 
  Verifying  : tigervnc-license-1.8.0-25.el7_9.noarch                                                              9/43 
  Verifying  : libXxf86misc-1.0.3-7.1.el7.x86_64                                                                  10/43 
  Verifying  : libXt-1.1.5-3.el7.x86_64                                                                           11/43 
  Verifying  : xorg-x11-xkb-utils-7.7-14.el7.x86_64                                                               12/43 
  Verifying  : mesa-filesystem-18.3.4-12.el7_9.x86_64                                                             13/43 
  Verifying  : xorg-x11-xinit-1.3.4-2.el7.x86_64                                                                  14/43 
  Verifying  : libxkbfile-1.0.9-3.el7.x86_64                                                                      15/43 
  Verifying  : llvm-private-7.0.1-1.el7.x86_64                                                                    16/43 
  Verifying  : xkeyboard-config-2.24-1.el7.noarch                                                                 17/43 
  Verifying  : tigervnc-server-minimal-1.8.0-25.el7_9.x86_64                                                      18/43 
  Verifying  : mesa-dri-drivers-18.3.4-12.el7_9.x86_64                                                            19/43 
  Verifying  : libXtst-1.2.3-1.el7.x86_64                                                                         20/43 
  Verifying  : 1:libglvnd-1.0.1-0.8.git5baa1e5.el7.x86_64                                                         21/43 
  Verifying  : libxcb-1.13-1.el7.x86_64                                                                           22/43 
  Verifying  : mesa-libGL-18.3.4-12.el7_9.x86_64                                                                  23/43 
  Verifying  : gnutls-3.3.29-9.el7_6.x86_64                                                                       24/43 
  Verifying  : tigervnc-server-1.8.0-25.el7_9.x86_64                                                              25/43 
  Verifying  : libXfont2-2.0.3-1.el7.x86_64                                                                       26/43 
  Verifying  : libXmu-1.1.2-2.el7.x86_64                                                                          27/43 
  Verifying  : libXrandr-1.5.1-2.el7.x86_64                                                                       28/43 
  Verifying  : pixman-0.34.0-1.el7.x86_64                                                                         29/43 
  Verifying  : mesa-libglapi-18.3.4-12.el7_9.x86_64                                                               30/43 
  Verifying  : 1:xorg-x11-xauth-1.0.9-1.el7.x86_64                                                                31/43 
  Verifying  : nettle-2.7.1-9.el7_9.x86_64                                                                        32/43 
  Verifying  : libxshmfence-1.2-1.el7.x86_64                                                                      33/43 
  Verifying  : libXau-1.0.8-2.1.el7.x86_64                                                                        34/43 
  Verifying  : libSM-1.2.2-2.el7.x86_64                                                                           35/43 
  Verifying  : libX11-1.6.7-4.el7_9.x86_64                                                                        36/43 
  Verifying  : libXcursor-1.1.15-1.el7.x86_64                                                                     37/43 
  Verifying  : libXdmcp-1.1.2-6.el7.x86_64                                                                        38/43 
  Verifying  : xorg-x11-server-utils-7.7-20.el7.x86_64                                                            39/43 
  Verifying  : libXdamage-1.1.4-4.1.el7.x86_64                                                                    40/43 
  Verifying  : libXfixes-5.0.3-1.el7.x86_64                                                                       41/43 
  Verifying  : libfontenc-1.1.3-3.el7.x86_64                                                                      42/43 
  Verifying  : libX11-common-1.6.7-4.el7_9.noarch                                                                 43/43 

Installed:
  tigervnc-server.x86_64 0:1.8.0-25.el7_9                                                                               

Dependency Installed:
  gnutls.x86_64 0:3.3.29-9.el7_6                           libICE.x86_64 0:1.0.9-9.el7                                  
  libSM.x86_64 0:1.2.2-2.el7                               libX11.x86_64 0:1.6.7-4.el7_9                                
  libX11-common.noarch 0:1.6.7-4.el7_9                     libXau.x86_64 0:1.0.8-2.1.el7                                
  libXcursor.x86_64 0:1.1.15-1.el7                         libXdamage.x86_64 0:1.1.4-4.1.el7                            
  libXdmcp.x86_64 0:1.1.2-6.el7                            libXext.x86_64 0:1.3.3-3.el7                                 
  libXfixes.x86_64 0:5.0.3-1.el7                           libXfont2.x86_64 0:2.0.3-1.el7                               
  libXi.x86_64 0:1.7.9-1.el7                               libXinerama.x86_64 0:1.1.3-2.1.el7                           
  libXmu.x86_64 0:1.1.2-2.el7                              libXrandr.x86_64 0:1.5.1-2.el7                               
  libXrender.x86_64 0:0.9.10-1.el7                         libXt.x86_64 0:1.1.5-3.el7                                   
  libXtst.x86_64 0:1.2.3-1.el7                             libXxf86misc.x86_64 0:1.0.3-7.1.el7                          
  libXxf86vm.x86_64 0:1.1.4-1.el7                          libfontenc.x86_64 0:1.1.3-3.el7                              
  libglvnd.x86_64 1:1.0.1-0.8.git5baa1e5.el7               libglvnd-glx.x86_64 1:1.0.1-0.8.git5baa1e5.el7               
  libxcb.x86_64 0:1.13-1.el7                               libxkbfile.x86_64 0:1.0.9-3.el7                              
  libxshmfence.x86_64 0:1.2-1.el7                          llvm-private.x86_64 0:7.0.1-1.el7                            
  mesa-dri-drivers.x86_64 0:18.3.4-12.el7_9                mesa-filesystem.x86_64 0:18.3.4-12.el7_9                     
  mesa-libGL.x86_64 0:18.3.4-12.el7_9                      mesa-libglapi.x86_64 0:18.3.4-12.el7_9                       
  nettle.x86_64 0:2.7.1-9.el7_9                            pixman.x86_64 0:0.34.0-1.el7                                 
  tigervnc-license.noarch 0:1.8.0-25.el7_9                 tigervnc-server-minimal.x86_64 0:1.8.0-25.el7_9              
  trousers.x86_64 0:0.3.14-2.el7                           xkeyboard-config.noarch 0:2.24-1.el7                         
  xorg-x11-server-utils.x86_64 0:7.7-20.el7                xorg-x11-xauth.x86_64 1:1.0.9-1.el7                          
  xorg-x11-xinit.x86_64 0:1.3.4-2.el7                      xorg-x11-xkb-utils.x86_64 0:7.7-14.el7                       

Complete!
[root@centos ~]# yum install xrdp -y 
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirrors.tuna.tsinghua.edu.cn
 * epel: mirrors.tuna.tsinghua.edu.cn
 * extras: mirrors.bupt.edu.cn
 * updates: mirrors.tuna.tsinghua.edu.cn
Resolving Dependencies
--> Running transaction check
---> Package xrdp.x86_64 1:0.9.22.1-2.el7 will be installed
--> Processing Dependency: libfuse.so.2(FUSE_2.4)(64bit) for package: 1:xrdp-0.9.22.1-2.el7.x86_64
--> Processing Dependency: libfuse.so.2(FUSE_2.5)(64bit) for package: 1:xrdp-0.9.22.1-2.el7.x86_64
--> Processing Dependency: libfuse.so.2(FUSE_2.6)(64bit) for package: 1:xrdp-0.9.22.1-2.el7.x86_64
--> Processing Dependency: libImlib2.so.1()(64bit) for package: 1:xrdp-0.9.22.1-2.el7.x86_64
--> Processing Dependency: libfuse.so.2()(64bit) for package: 1:xrdp-0.9.22.1-2.el7.x86_64
--> Running transaction check
---> Package fuse-libs.x86_64 0:2.9.2-11.el7 will be installed
---> Package imlib2.x86_64 0:1.4.9-8.el7 will be installed
--> Processing Dependency: libtiff.so.5(LIBTIFF_4.0)(64bit) for package: imlib2-1.4.9-8.el7.x86_64
--> Processing Dependency: libgif.so.4()(64bit) for package: imlib2-1.4.9-8.el7.x86_64
--> Processing Dependency: libtiff.so.5()(64bit) for package: imlib2-1.4.9-8.el7.x86_64
--> Running transaction check
---> Package giflib.x86_64 0:4.1.6-9.el7 will be installed
---> Package libtiff.x86_64 0:4.0.3-35.el7 will be installed
--> Processing Dependency: libjbig.so.2.0()(64bit) for package: libtiff-4.0.3-35.el7.x86_64
--> Running transaction check
---> Package jbigkit-libs.x86_64 0:2.0-11.el7 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

========================================================================================================================
 Package                       Arch                    Version                              Repository             Size
========================================================================================================================
Installing:
 xrdp                          x86_64                  1:0.9.22.1-2.el7                     epel                  462 k
Installing for dependencies:
 fuse-libs                     x86_64                  2.9.2-11.el7                         base                   93 k
 giflib                        x86_64                  4.1.6-9.el7                          base                   40 k
 imlib2                        x86_64                  1.4.9-8.el7                          epel                  210 k
 jbigkit-libs                  x86_64                  2.0-11.el7                           base                   46 k
 libtiff                       x86_64                  4.0.3-35.el7                         base                  172 k

Transaction Summary
========================================================================================================================
Install  1 Package (+5 Dependent packages)

Total download size: 1.0 M
Installed size: 3.8 M
Downloading packages:
(1/6): giflib-4.1.6-9.el7.x86_64.rpm                                                             |  40 kB  00:00:00     
(2/6): libtiff-4.0.3-35.el7.x86_64.rpm                                                           | 172 kB  00:00:00     
(3/6): xrdp-0.9.22.1-2.el7.x86_64.rpm                                                            | 462 kB  00:00:00     
(4/6): fuse-libs-2.9.2-11.el7.x86_64.rpm                                                         |  93 kB  00:00:00     
(5/6): jbigkit-libs-2.0-11.el7.x86_64.rpm                                                        |  46 kB  00:00:00     
(6/6): imlib2-1.4.9-8.el7.x86_64.rpm                                                             | 210 kB  00:00:00     
------------------------------------------------------------------------------------------------------------------------
Total                                                                                   2.6 MB/s | 1.0 MB  00:00:00     
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : jbigkit-libs-2.0-11.el7.x86_64                                                                       1/6 
  Installing : libtiff-4.0.3-35.el7.x86_64                                                                          2/6 
  Installing : giflib-4.1.6-9.el7.x86_64                                                                            3/6 
  Installing : imlib2-1.4.9-8.el7.x86_64                                                                            4/6 
  Installing : fuse-libs-2.9.2-11.el7.x86_64                                                                        5/6 
  Installing : 1:xrdp-0.9.22.1-2.el7.x86_64                                                                         6/6 
  Verifying  : fuse-libs-2.9.2-11.el7.x86_64                                                                        1/6 
  Verifying  : giflib-4.1.6-9.el7.x86_64                                                                            2/6 
  Verifying  : libtiff-4.0.3-35.el7.x86_64                                                                          3/6 
  Verifying  : 1:xrdp-0.9.22.1-2.el7.x86_64                                                                         4/6 
  Verifying  : imlib2-1.4.9-8.el7.x86_64                                                                            5/6 
  Verifying  : jbigkit-libs-2.0-11.el7.x86_64                                                                       6/6 

Installed:
  xrdp.x86_64 1:0.9.22.1-2.el7                                                                                          

Dependency Installed:
  fuse-libs.x86_64 0:2.9.2-11.el7           giflib.x86_64 0:4.1.6-9.el7            imlib2.x86_64 0:1.4.9-8.el7         
  jbigkit-libs.x86_64 0:2.0-11.el7          libtiff.x86_64 0:4.0.3-35.el7         

Complete!
[root@centos ~]# groupinstall "X Window System" -y 
-bash: groupinstall: command not found
[root@centos ~]# yum group install "GNOME" -y
Loaded plugins: fastestmirror
There is no installed groups file.
Maybe run: yum groups mark convert (see man yum)
Loading mirror speeds from cached hostfile
 * base: mirrors.tuna.tsinghua.edu.cn
 * epel: mirrors.tuna.tsinghua.edu.cn
 * extras: mirrors.bupt.edu.cn
 * updates: mirrors.tuna.tsinghua.edu.cn
Resolving Dependencies
--> Running transaction check
---> Package NetworkManager-libreswan-gnome.x86_64 0:1.2.4-2.el7 will be installed
--> Processing Dependency: NetworkManager-libreswan(x86-64) = 1.2.4-2.el7 for package: NetworkManager-libreswan-gnome-1.2.4-2.el7.x86_64
--> Processing Dependency: libnma.so.0(libnma_1_2_0)(64bit) for package: NetworkManager-libreswan-gnome-1.2.4-2.el7.x86_64
--> Processing Dependency: libnm-gtk.so.0(libnm_gtk_1_0_6)(64bit) for package: NetworkManager-libreswan-gnome-1.2.4-2.el7.x86_64
--> Processing Dependency: libsecret-1.so.0()(64bit) for package: NetworkManager-libreswan-gnome-1.2.4-2.el7.x86_64
--> Processing Dependency: libpangocairo-1.0.so.0()(64bit) for package: NetworkManager-libreswan-gnome-1.2.4-2.el7.x86_64
--> Processing Dependency: libpango-1.0.so.0()(64bit) for package: NetworkManager-libreswan-gnome-1.2.4-2.el7.x86_64
--> Processing Dependency: libnma.so.0()(64bit) for package: NetworkManager-libreswan-gnome-1.2.4-2.el7.x86_64
--> Processing Dependency: libnm-util.so.2()(64bit) for package: NetworkManager-libreswan-gnome-1.2.4-2.el7.x86_64
--> Processing Dependency: libnm-gtk.so.0()(64bit) for package: NetworkManager-libreswan-gnome-1.2.4-2.el7.x86_64
--> Processing Dependency: libnm-glib.so.4()(64bit) for package: NetworkManager-libreswan-gnome-1.2.4-2.el7.x86_64
--> Processing Dependency: libnm-glib-vpn.so.1()(64bit) for package: NetworkManager-libreswan-gnome-1.2.4-2.el7.x86_64
--> Processing Dependency: libgtk-3.so.0()(64bit) for package: NetworkManager-libreswan-gnome-1.2.4-2.el7.x86_64
--> Processing Dependency: libgdk_pixbuf-2.0.so.0()(64bit) for package: NetworkManager-libreswan-gnome-1.2.4-2.el7.x86_64
--> Processing Dependency: libgdk-3.so.0()(64bit) for package: NetworkManager-libreswan-gnome-1.2.4-2.el7.x86_64
--> Processing Dependency: libcairo.so.2()(64bit) for package: NetworkManager-libreswan-gnome-1.2.4-2.el7.x86_64
--> Processing Dependency: libcairo-gobject.so.2()(64bit) for package: NetworkManager-libreswan-gnome-1.2.4-2.el7.x86_64
--> Processing Dependency: libatk-1.0.so.0()(64bit) for package: NetworkManager-libreswan-gnome-1.2.4-2.el7.x86_64
---> Package PackageKit-command-not-found.x86_64 0:1.1.10-2.el7.centos will be installed
--> Processing Dependency: PackageKit-glib(x86-64) = 1.1.10-2.el7.centos for package: PackageKit-command-not-found-1.1.10-2.el7.centos.x86_64
--> Processing Dependency: libpackagekit-glib2.so.18()(64bit) for package: PackageKit-command-not-found-1.1.10-2.el7.centos.x86_64
---> Package PackageKit-gtk3-module.x86_64 0:1.1.10-2.el7.centos will be installed
--> Processing Dependency: libgtk-x11-2.0.so.0()(64bit) for package: PackageKit-gtk3-module-1.1.10-2.el7.centos.x86_64
--> Processing Dependency: libgdk-x11-2.0.so.0()(64bit) for package: PackageKit-gtk3-module-1.1.10-2.el7.centos.x86_64
--> Processing Dependency: libfontconfig.so.1()(64bit) for package: PackageKit-gtk3-module-1.1.10-2.el7.centos.x86_64
---> Package abrt-desktop.x86_64 0:2.1.11-60.el7.centos will be installed
--> Processing Dependency: abrt = 2.1.11-60.el7.centos for package: abrt-desktop-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: libreport-plugin-mantisbt >= 2.1.11-46 for package: abrt-desktop-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: libreport-centos >= 2.1.11-46 for package: abrt-desktop-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: gdb >= 7.6.1-63 for package: abrt-desktop-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: gnome-abrt for package: abrt-desktop-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: elfutils for package: abrt-desktop-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: abrt-gui for package: abrt-desktop-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: abrt-addon-xorg for package: abrt-desktop-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: abrt-addon-vmcore for package: abrt-desktop-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: abrt-addon-python for package: abrt-desktop-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: abrt-addon-pstoreoops for package: abrt-desktop-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: abrt-addon-kerneloops for package: abrt-desktop-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: abrt-addon-ccpp for package: abrt-desktop-2.1.11-60.el7.centos.x86_64
---> Package at-spi2-atk.x86_64 0:2.26.2-1.el7 will be installed
---> Package at-spi2-core.x86_64 0:2.28.0-1.el7 will be installed
---> Package avahi.x86_64 0:0.6.31-20.el7 will be installed
--> Processing Dependency: avahi-libs = 0.6.31-20.el7 for package: avahi-0.6.31-20.el7.x86_64
--> Processing Dependency: libavahi-common.so.3()(64bit) for package: avahi-0.6.31-20.el7.x86_64
---> Package baobab.x86_64 0:3.28.0-2.el7 will be installed
---> Package cheese.x86_64 2:3.28.0-1.el7 will be installed
--> Processing Dependency: cheese-libs(x86-64) = 2:3.28.0-1.el7 for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: gstreamer1-plugins-good for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: gstreamer1-plugins-bad-free for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: gnome-video-effects for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libxkbcommon.so.0()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libwayland-server.so.0()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libwayland-egl.so.1()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libwayland-cursor.so.0()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libwayland-client.so.0()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libjson-glib-1.0.so.0()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libgstvideo-1.0.so.0()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libgstreamer-1.0.so.0()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libgstpbutils-1.0.so.0()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libgstbase-1.0.so.0()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libgnome-desktop-3.so.17()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libgbm.so.1()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libcogl.so.20()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libcogl-path.so.20()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libcogl-pango.so.20()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libclutter-gtk-1.0.so.0()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libclutter-gst-3.0.so.0()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libclutter-1.0.so.0()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libcheese.so.8()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libcheese-gtk.so.25()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libcanberra.so.0()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libXcomposite.so.1()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
--> Processing Dependency: libEGL.so.1()(64bit) for package: 2:cheese-3.28.0-1.el7.x86_64
---> Package compat-cheese314.x86_64 0:3.14.2-1.el7 will be installed
--> Processing Dependency: libgudev-1.0.so.0()(64bit) for package: compat-cheese314-3.14.2-1.el7.x86_64
--> Processing Dependency: libgnome-desktop-3.so.10()(64bit) for package: compat-cheese314-3.14.2-1.el7.x86_64
--> Processing Dependency: libclutter-gst-2.0.so.0()(64bit) for package: compat-cheese314-3.14.2-1.el7.x86_64
---> Package control-center.x86_64 1:3.28.1-8.el7_9.1 will be installed
--> Processing Dependency: control-center-filesystem = 1:3.28.1-8.el7_9.1 for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: upower(x86-64) >= 0.99.6 for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: gsettings-desktop-schemas(x86-64) >= 3.27.2 for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: gnome-online-accounts(x86-64) >= 3.25.3 for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: libsmbclient.so.0(SMBCLIENT_0.1.0)(64bit) for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: libpulse.so.0(PULSE_0)(64bit) for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: libpulse-mainloop-glib.so.0(PULSE_0)(64bit) for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: iso-codes for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: glx-utils for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: dbus-x11 for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: cups-pk-helper for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: colord for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: bolt for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: accountsservice for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: NetworkManager-wifi for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: /usr/bin/gkbd-keyboard-display for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: libwacom.so.2()(64bit) for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: libupower-glib.so.3()(64bit) for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: libsoup-2.4.so.1()(64bit) for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: libsmbclient.so.0()(64bit) for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: libpulse.so.0()(64bit) for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: libpulse-mainloop-glib.so.0()(64bit) for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: libmm-glib.so.0()(64bit) for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: libibus-1.0.so.5()(64bit) for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: libgtop-2.0.so.11()(64bit) for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: libgrilo-0.3.so.0()(64bit) for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: libgoa-backend-1.0.so.1()(64bit) for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: libgoa-1.0.so.0()(64bit) for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: libgnome-bluetooth.so.13()(64bit) for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: libcups.so.2()(64bit) for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: libcolordprivate.so.2()(64bit) for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: libcolord.so.2()(64bit) for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: libcolord-gtk.so.1()(64bit) for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
--> Processing Dependency: libaccountsservice.so.0()(64bit) for package: 1:control-center-3.28.1-8.el7_9.1.x86_64
---> Package dconf.x86_64 0:0.28.0-4.el7 will be installed
---> Package empathy.x86_64 0:3.12.13-1.el7 will be installed
--> Processing Dependency: telepathy-salut >= 0.8.0 for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: telepathy-mission-control >= 5.12.0 for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: telepathy-haze >= 0.6.0 for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: telepathy-gabble >= 0.16.0 for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: telepathy-filesystem for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.9.2)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.9.0)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.7.9)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.7.6)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.7.36)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.7.35)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.7.34)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.7.32)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.7.29)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.7.27)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.7.26)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.7.24)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.7.23)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.7.21)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.7.2)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.7.18)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.7.17)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.7.16)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.7.15)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.7.14)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.7.12)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.7.1)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.7.0)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.23.2)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.23.0)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.19.9)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.19.4)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.19.3)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.19.1)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.19.0)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.17.6)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.17.5)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.17.1)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.17.0)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.15.8)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.15.6)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.15.5)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.15.3)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.15.2)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.15.1)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.15.0)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.14.3)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.14.2)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.13.9)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.13.8)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.13.7)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.13.3)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.13.2)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.13.16)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.13.14)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.13.12)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.13.11)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.13.10)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.13.1)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.13.0)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.11.9)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.11.7)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.11.6)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.11.5)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.11.4)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.11.3)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.11.16)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.11.15)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.11.14)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.11.13)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.11.12)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.11.11)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.11.1)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0(TELEPATHY_GLIB_0.11.0)(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libwebkitgtk-3.0.so.0()(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-logger.so.3()(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-glib.so.0()(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libtelepathy-farstream.so.3()(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libnotify.so.4()(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libmission-control-plugins.so.0()(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libjavascriptcoregtk-3.0.so.0()(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libgeocode-glib.so.0()(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libgee-0.8.so.2()(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libgcr-ui-3.so.1()(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libgcr-base-3.so.1()(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libgck-1.so.0()(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libfolks.so.25()(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libfolks-telepathy.so.25()(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libfarstream-0.2.so.2()(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libenchant.so.1()(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libchamplain-gtk-0.12.so.0()(64bit) for package: empathy-3.12.13-1.el7.x86_64
--> Processing Dependency: libchamplain-0.12.so.0()(64bit) for package: empathy-3.12.13-1.el7.x86_64
---> Package eog.x86_64 0:3.28.3-1.el7 will be installed
--> Processing Dependency: libpeas-gtk-1.0.so.0()(64bit) for package: eog-3.28.3-1.el7.x86_64
--> Processing Dependency: libpeas-1.0.so.0()(64bit) for package: eog-3.28.3-1.el7.x86_64
--> Processing Dependency: liblcms2.so.2()(64bit) for package: eog-3.28.3-1.el7.x86_64
--> Processing Dependency: libexif.so.12()(64bit) for package: eog-3.28.3-1.el7.x86_64
--> Processing Dependency: libexempi.so.3()(64bit) for package: eog-3.28.3-1.el7.x86_64
---> Package evince.x86_64 0:3.28.2-10.el7 will be installed
--> Processing Dependency: evince-libs(x86-64) = 3.28.2-10.el7 for package: evince-3.28.2-10.el7.x86_64
--> Processing Dependency: libevview3.so.3()(64bit) for package: evince-3.28.2-10.el7.x86_64
--> Processing Dependency: libevdocument3.so.4()(64bit) for package: evince-3.28.2-10.el7.x86_64
---> Package evince-nautilus.x86_64 0:3.28.2-10.el7 will be installed
--> Processing Dependency: libnautilus-extension.so.1()(64bit) for package: evince-nautilus-3.28.2-10.el7.x86_64
---> Package file-roller.x86_64 0:3.28.1-2.el7 will be installed
--> Processing Dependency: /usr/bin/lzop for package: file-roller-3.28.1-2.el7.x86_64
--> Processing Dependency: /usr/bin/isoinfo for package: file-roller-3.28.1-2.el7.x86_64
--> Processing Dependency: /usr/bin/compress for package: file-roller-3.28.1-2.el7.x86_64
---> Package file-roller-nautilus.x86_64 0:3.28.1-2.el7 will be installed
---> Package firewall-config.noarch 0:0.6.3-13.el7_9 will be installed
--> Processing Dependency: hicolor-icon-theme for package: firewall-config-0.6.3-13.el7_9.noarch
---> Package firstboot.x86_64 0:19.12-1.el7 will be installed
--> Processing Dependency: python-meh for package: firstboot-19.12-1.el7.x86_64
--> Processing Dependency: python-ethtool for package: firstboot-19.12-1.el7.x86_64
--> Processing Dependency: pygtk2 for package: firstboot-19.12-1.el7.x86_64
--> Processing Dependency: libreport-python for package: firstboot-19.12-1.el7.x86_64
---> Package fprintd-pam.x86_64 0:0.8.1-2.el7 will be installed
--> Processing Dependency: fprintd = 0.8.1-2.el7 for package: fprintd-pam-0.8.1-2.el7.x86_64
---> Package gdm.x86_64 1:3.28.2-26.el7 will be installed
--> Processing Dependency: pulseaudio-gdm-hooks for package: 1:gdm-3.28.2-26.el7.x86_64
--> Processing Dependency: gnome-keyring-pam for package: 1:gdm-3.28.2-26.el7.x86_64
---> Package gedit.x86_64 2:3.28.1-3.el7 will be installed
--> Processing Dependency: gtksourceview3(x86-64) >= 3.22.0 for package: 2:gedit-3.28.1-3.el7.x86_64
--> Processing Dependency: gspell(x86-64) >= 0.2.5 for package: 2:gedit-3.28.1-3.el7.x86_64
--> Processing Dependency: zenity for package: 2:gedit-3.28.1-3.el7.x86_64
--> Processing Dependency: libpeas-loader-python(x86-64) for package: 2:gedit-3.28.1-3.el7.x86_64
--> Processing Dependency: gvfs for package: 2:gedit-3.28.1-3.el7.x86_64
--> Processing Dependency: libgtksourceview-3.0.so.1()(64bit) for package: 2:gedit-3.28.1-3.el7.x86_64
--> Processing Dependency: libgspell-1.so.1()(64bit) for package: 2:gedit-3.28.1-3.el7.x86_64
---> Package glib-networking.x86_64 0:2.56.1-1.el7 will be installed
--> Processing Dependency: libproxy.so.1()(64bit) for package: glib-networking-2.56.1-1.el7.x86_64
---> Package gnome-bluetooth.x86_64 1:3.28.2-1.el7 will be installed
--> Processing Dependency: bluez >= 5.0 for package: 1:gnome-bluetooth-3.28.2-1.el7.x86_64
--> Processing Dependency: pulseaudio-module-bluetooth for package: 1:gnome-bluetooth-3.28.2-1.el7.x86_64
--> Processing Dependency: desktop-file-utils for package: 1:gnome-bluetooth-3.28.2-1.el7.x86_64
--> Processing Dependency: desktop-file-utils for package: 1:gnome-bluetooth-3.28.2-1.el7.x86_64
---> Package gnome-boxes.x86_64 0:3.28.5-4.el7 will be installed
--> Processing Dependency: mtools for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gobject-1.0.so.0(LIBVIRT_GOBJECT_0.2.3)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gobject-1.0.so.0(LIBVIRT_GOBJECT_0.2.2)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gobject-1.0.so.0(LIBVIRT_GOBJECT_0.2.1)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gobject-1.0.so.0(LIBVIRT_GOBJECT_0.2.0)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gobject-1.0.so.0(LIBVIRT_GOBJECT_0.1.9)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gobject-1.0.so.0(LIBVIRT_GOBJECT_0.1.5)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gobject-1.0.so.0(LIBVIRT_GOBJECT_0.1.4)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gobject-1.0.so.0(LIBVIRT_GOBJECT_0.1.3)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gobject-1.0.so.0(LIBVIRT_GOBJECT_0.1.2)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gobject-1.0.so.0(LIBVIRT_GOBJECT_0.0.9)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gobject-1.0.so.0(LIBVIRT_GOBJECT_0.0.8)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gconfig-1.0.so.0(LIBVIRT_GCONFIG_0.1.9)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gconfig-1.0.so.0(LIBVIRT_GCONFIG_0.1.8)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gconfig-1.0.so.0(LIBVIRT_GCONFIG_0.1.7)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gconfig-1.0.so.0(LIBVIRT_GCONFIG_0.1.6)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gconfig-1.0.so.0(LIBVIRT_GCONFIG_0.1.5)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gconfig-1.0.so.0(LIBVIRT_GCONFIG_0.1.4)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gconfig-1.0.so.0(LIBVIRT_GCONFIG_0.1.0)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gconfig-1.0.so.0(LIBVIRT_GCONFIG_0.0.9)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gconfig-1.0.so.0(LIBVIRT_GCONFIG_0.0.8)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-daemon-kvm for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-daemon-config-network for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libspice-client-gtk-3.0.so.5(SPICEGTK_1)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libspice-client-glib-2.0.so.8(SPICEGTK_1)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libosinfo-1.0.so.0(LIBOSINFO_0.2.9)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libosinfo-1.0.so.0(LIBOSINFO_0.2.8)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libosinfo-1.0.so.0(LIBOSINFO_0.2.6)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libosinfo-1.0.so.0(LIBOSINFO_0.2.3)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libosinfo-1.0.so.0(LIBOSINFO_0.2.2)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libosinfo-1.0.so.0(LIBOSINFO_0.2.12)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libosinfo-1.0.so.0(LIBOSINFO_0.2.11)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libosinfo-1.0.so.0(LIBOSINFO_0.2.10)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libosinfo-1.0.so.0(LIBOSINFO_0.2.1)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libosinfo-1.0.so.0(LIBOSINFO_0.2.0)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libosinfo-1.0.so.0(LIBOSINFO_0.0.5)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libosinfo-1.0.so.0(LIBOSINFO_0.0.1)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libgovirt.so.2(GOVIRT_0.2.0)(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: adwaita-icon-theme for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libwebkit2gtk-4.0.so.37()(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gobject-1.0.so.0()(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libvirt-gconfig-1.0.so.0()(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libusb-1.0.so.0()(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libtracker-sparql-1.0.so.0()(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libspice-client-gtk-3.0.so.5()(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libspice-client-glib-2.0.so.8()(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: librest-0.7.so.0()(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libosinfo-1.0.so.0()(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libgtk-vnc-2.0.so.0()(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
--> Processing Dependency: libgovirt.so.2()(64bit) for package: gnome-boxes-3.28.5-4.el7.x86_64
---> Package gnome-calculator.x86_64 0:3.28.2-1.el7 will be installed
---> Package gnome-classic-session.noarch 0:3.28.1-17.el7_9 will be installed
--> Processing Dependency: gnome-shell-extension-window-list = 3.28.1-17.el7_9 for package: gnome-classic-session-3.28.1-17.el7_9.noarch
--> Processing Dependency: gnome-shell-extension-top-icons = 3.28.1-17.el7_9 for package: gnome-classic-session-3.28.1-17.el7_9.noarch
--> Processing Dependency: gnome-shell-extension-places-menu = 3.28.1-17.el7_9 for package: gnome-classic-session-3.28.1-17.el7_9.noarch
--> Processing Dependency: gnome-shell-extension-launch-new-instance = 3.28.1-17.el7_9 for package: gnome-classic-session-3.28.1-17.el7_9.noarch
--> Processing Dependency: gnome-shell-extension-horizontal-workspaces = 3.28.1-17.el7_9 for package: gnome-classic-session-3.28.1-17.el7_9.noarch
--> Processing Dependency: gnome-shell-extension-apps-menu = 3.28.1-17.el7_9 for package: gnome-classic-session-3.28.1-17.el7_9.noarch
--> Processing Dependency: gnome-shell-extension-alternate-tab = 3.28.1-17.el7_9 for package: gnome-classic-session-3.28.1-17.el7_9.noarch
---> Package gnome-clocks.x86_64 0:3.28.0-1.el7 will be installed
--> Processing Dependency: libgweather(x86-64) >= 3.27.2 for package: gnome-clocks-3.28.0-1.el7.x86_64
--> Processing Dependency: libgweather-3.so.15()(64bit) for package: gnome-clocks-3.28.0-1.el7.x86_64
--> Processing Dependency: libgsound.so.0()(64bit) for package: gnome-clocks-3.28.0-1.el7.x86_64
--> Processing Dependency: libgeoclue-2.so.0()(64bit) for package: gnome-clocks-3.28.0-1.el7.x86_64
---> Package gnome-color-manager.x86_64 0:3.28.0-1.el7 will be installed
--> Processing Dependency: libvte-2.91.so.0()(64bit) for package: gnome-color-manager-3.28.0-1.el7.x86_64
--> Processing Dependency: libexiv2.so.26()(64bit) for package: gnome-color-manager-3.28.0-1.el7.x86_64
---> Package gnome-contacts.x86_64 0:3.28.2-1.el7 will be installed
--> Processing Dependency: libedataserverui-1.2.so.2()(64bit) for package: gnome-contacts-3.28.2-1.el7.x86_64
--> Processing Dependency: libedataserver-1.2.so.23()(64bit) for package: gnome-contacts-3.28.2-1.el7.x86_64
---> Package gnome-dictionary.x86_64 0:3.26.1-2.el7 will be installed
---> Package gnome-disk-utility.x86_64 0:3.28.3-1.el7 will be installed
--> Processing Dependency: udisks2 for package: gnome-disk-utility-3.28.3-1.el7.x86_64
--> Processing Dependency: libudisks2.so.0()(64bit) for package: gnome-disk-utility-3.28.3-1.el7.x86_64
--> Processing Dependency: libdvdread.so.4()(64bit) for package: gnome-disk-utility-3.28.3-1.el7.x86_64
---> Package gnome-font-viewer.x86_64 0:3.28.0-1.el7 will be installed
--> Processing Dependency: libharfbuzz.so.0()(64bit) for package: gnome-font-viewer-3.28.0-1.el7.x86_64
---> Package gnome-getting-started-docs.noarch 0:3.28.2-1.el7 will be installed
---> Package gnome-icon-theme.noarch 0:3.12.0-1.el7 will be installed
---> Package gnome-icon-theme-extras.noarch 0:3.12.0-1.el7 will be installed
---> Package gnome-icon-theme-symbolic.noarch 0:3.12.0-2.el7 will be installed
---> Package gnome-initial-setup.x86_64 0:3.28.0-2.el7_9.1 will be installed
--> Processing Dependency: libjavascriptcoregtk-4.0.so.18()(64bit) for package: gnome-initial-setup-3.28.0-2.el7_9.1.x86_64
---> Package gnome-packagekit.x86_64 0:3.28.0-1.el7 will be installed
--> Processing Dependency: gnome-packagekit-installer for package: gnome-packagekit-3.28.0-1.el7.x86_64
---> Package gnome-packagekit-updater.x86_64 0:3.28.0-1.el7 will be installed
--> Processing Dependency: gnome-packagekit-common(x86-64) = 3.28.0-1.el7 for package: gnome-packagekit-updater-3.28.0-1.el7.x86_64
---> Package gnome-screenshot.x86_64 0:3.26.0-1.el7 will be installed
---> Package gnome-session.x86_64 0:3.28.1-8.el7 will be installed
--> Processing Dependency: libepoxy.so.0()(64bit) for package: gnome-session-3.28.1-8.el7.x86_64
--> Processing Dependency: libGLESv2.so.2()(64bit) for package: gnome-session-3.28.1-8.el7.x86_64
---> Package gnome-session-xsession.x86_64 0:3.28.1-8.el7 will be installed
---> Package gnome-settings-daemon.x86_64 0:3.28.1-11.el7_9 will be installed
--> Processing Dependency: geoclue2 >= 2.3.1 for package: gnome-settings-daemon-3.28.1-11.el7_9.x86_64
---> Package gnome-shell.x86_64 0:3.28.3-34.el7_9 will be installed
--> Processing Dependency: mutter(x86-64) >= 3.28.0 for package: gnome-shell-3.28.3-34.el7_9.x86_64
--> Processing Dependency: ibus(x86-64) >= 1.5.2 for package: gnome-shell-3.28.3-34.el7_9.x86_64
--> Processing Dependency: gjs(x86-64) >= 1.51.90 for package: gnome-shell-3.28.3-34.el7_9.x86_64
--> Processing Dependency: libstartup-notification-1.so.0()(64bit) for package: gnome-shell-3.28.3-34.el7_9.x86_64
--> Processing Dependency: libmutter-cogl-pango-2.so()(64bit) for package: gnome-shell-3.28.3-34.el7_9.x86_64
--> Processing Dependency: libmutter-cogl-2.so()(64bit) for package: gnome-shell-3.28.3-34.el7_9.x86_64
--> Processing Dependency: libmutter-clutter-2.so()(64bit) for package: gnome-shell-3.28.3-34.el7_9.x86_64
--> Processing Dependency: libmutter-2.so.0()(64bit) for package: gnome-shell-3.28.3-34.el7_9.x86_64
--> Processing Dependency: libical.so.3()(64bit) for package: gnome-shell-3.28.3-34.el7_9.x86_64
--> Processing Dependency: libgjs.so.0()(64bit) for package: gnome-shell-3.28.3-34.el7_9.x86_64
---> Package gnome-software.x86_64 0:3.28.2-3.el7 will be installed
--> Processing Dependency: libappstream-glib(x86-64) >= 0.7.8 for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: fwupd(x86-64) >= 1.0.7 for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: flatpak-libs(x86-64) >= 0.9.4 for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: flatpak(x86-64) >= 0.9.4 for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: PackageKit(x86-64) >= 1.1.1 for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: libfwupd.so.2(LIBFWUPD_1.0.7)(64bit) for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: libfwupd.so.2(LIBFWUPD_1.0.3)(64bit) for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: libfwupd.so.2(LIBFWUPD_1.0.0)(64bit) for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: libfwupd.so.2(LIBFWUPD_0.9.8)(64bit) for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: libfwupd.so.2(LIBFWUPD_0.9.7)(64bit) for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: libfwupd.so.2(LIBFWUPD_0.9.6)(64bit) for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: libfwupd.so.2(LIBFWUPD_0.9.5)(64bit) for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: libfwupd.so.2(LIBFWUPD_0.9.4)(64bit) for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: libfwupd.so.2(LIBFWUPD_0.9.3)(64bit) for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: libfwupd.so.2(LIBFWUPD_0.9.2)(64bit) for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: libfwupd.so.2(LIBFWUPD_0.7.3)(64bit) for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: libfwupd.so.2(LIBFWUPD_0.7.0)(64bit) for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: libfwupd.so.2(LIBFWUPD_0.1.1)(64bit) for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: gnome-menus(x86-64) for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: appstream-data for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: libfwupd.so.2()(64bit) for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: libflatpak.so.0()(64bit) for package: gnome-software-3.28.2-3.el7.x86_64
--> Processing Dependency: libappstream-glib.so.8()(64bit) for package: gnome-software-3.28.2-3.el7.x86_64
---> Package gnome-system-log.x86_64 1:3.9.90-3.el7 will be installed
---> Package gnome-system-monitor.x86_64 0:3.28.2-1.el7 will be installed
--> Processing Dependency: libsigc-2.0.so.0()(64bit) for package: gnome-system-monitor-3.28.2-1.el7.x86_64
--> Processing Dependency: libpangomm-1.4.so.1()(64bit) for package: gnome-system-monitor-3.28.2-1.el7.x86_64
--> Processing Dependency: libgtkmm-3.0.so.1()(64bit) for package: gnome-system-monitor-3.28.2-1.el7.x86_64
--> Processing Dependency: libglibmm-2.4.so.1()(64bit) for package: gnome-system-monitor-3.28.2-1.el7.x86_64
--> Processing Dependency: libgiomm-2.4.so.1()(64bit) for package: gnome-system-monitor-3.28.2-1.el7.x86_64
--> Processing Dependency: libgdkmm-3.0.so.1()(64bit) for package: gnome-system-monitor-3.28.2-1.el7.x86_64
--> Processing Dependency: libcairomm-1.0.so.1()(64bit) for package: gnome-system-monitor-3.28.2-1.el7.x86_64
--> Processing Dependency: libatkmm-1.6.so.1()(64bit) for package: gnome-system-monitor-3.28.2-1.el7.x86_64
---> Package gnome-terminal.x86_64 0:3.28.2-3.el7 will be installed
--> Processing Dependency: libpcre2-8.so.0()(64bit) for package: gnome-terminal-3.28.2-3.el7.x86_64
--> Processing Dependency: libgconf-2.so.4()(64bit) for package: gnome-terminal-3.28.2-3.el7.x86_64
---> Package gnome-terminal-nautilus.x86_64 0:3.28.2-3.el7 will be installed
---> Package gnome-themes-standard.x86_64 0:3.28-2.el7 will be installed
--> Processing Dependency: adwaita-gtk2-theme = 3.28-2.el7 for package: gnome-themes-standard-3.28-2.el7.x86_64
--> Processing Dependency: google-noto-emoji-color-fonts for package: gnome-themes-standard-3.28-2.el7.x86_64
--> Processing Dependency: abattis-cantarell-fonts for package: gnome-themes-standard-3.28-2.el7.x86_64
---> Package gnome-tweak-tool.noarch 0:3.28.1-7.el7 will be installed
--> Processing Dependency: gnome-shell-extension-user-theme for package: gnome-tweak-tool-3.28.1-7.el7.noarch
---> Package gnome-user-docs.noarch 0:3.28.2-1.el7 will be installed
---> Package gnome-weather.noarch 0:3.26.0-1.el7 will be installed
---> Package gucharmap.x86_64 0:10.0.4-1.el7 will be installed
--> Processing Dependency: gucharmap-libs(x86-64) = 10.0.4-1.el7 for package: gucharmap-10.0.4-1.el7.x86_64
--> Processing Dependency: libgucharmap_2_90.so.7()(64bit) for package: gucharmap-10.0.4-1.el7.x86_64
---> Package gvfs-afc.x86_64 0:1.36.2-7.el7_9 will be installed
--> Processing Dependency: gvfs-client(x86-64) = 1.36.2-7.el7_9 for package: gvfs-afc-1.36.2-7.el7_9.x86_64
--> Processing Dependency: usbmuxd for package: gvfs-afc-1.36.2-7.el7_9.x86_64
--> Processing Dependency: libplist.so.3()(64bit) for package: gvfs-afc-1.36.2-7.el7_9.x86_64
--> Processing Dependency: libimobiledevice.so.6()(64bit) for package: gvfs-afc-1.36.2-7.el7_9.x86_64
--> Processing Dependency: libgvfscommon.so()(64bit) for package: gvfs-afc-1.36.2-7.el7_9.x86_64
---> Package gvfs-afp.x86_64 0:1.36.2-7.el7_9 will be installed
---> Package gvfs-archive.x86_64 0:1.36.2-7.el7_9 will be installed
---> Package gvfs-fuse.x86_64 0:1.36.2-7.el7_9 will be installed
--> Processing Dependency: fuse >= 2.8.0 for package: gvfs-fuse-1.36.2-7.el7_9.x86_64
---> Package gvfs-goa.x86_64 0:1.36.2-7.el7_9 will be installed
--> Processing Dependency: libgdata(x86-64) >= 0.17.9 for package: gvfs-goa-1.36.2-7.el7_9.x86_64
--> Processing Dependency: libgdata.so.22()(64bit) for package: gvfs-goa-1.36.2-7.el7_9.x86_64
---> Package gvfs-gphoto2.x86_64 0:1.36.2-7.el7_9 will be installed
--> Processing Dependency: libgphoto2_port.so.12(LIBGPHOTO2_5_0)(64bit) for package: gvfs-gphoto2-1.36.2-7.el7_9.x86_64
--> Processing Dependency: libgphoto2_port.so.12()(64bit) for package: gvfs-gphoto2-1.36.2-7.el7_9.x86_64
--> Processing Dependency: libgphoto2.so.6()(64bit) for package: gvfs-gphoto2-1.36.2-7.el7_9.x86_64
---> Package gvfs-mtp.x86_64 0:1.36.2-7.el7_9 will be installed
--> Processing Dependency: libmtp.so.9()(64bit) for package: gvfs-mtp-1.36.2-7.el7_9.x86_64
---> Package gvfs-smb.x86_64 0:1.36.2-7.el7_9 will be installed
---> Package initial-setup-gui.x86_64 0:0.3.9.45-1.el7.centos will be installed
--> Processing Dependency: initial-setup = 0.3.9.45-1.el7.centos for package: initial-setup-gui-0.3.9.45-1.el7.centos.x86_64
--> Processing Dependency: anaconda-gui >= 21.48.22.102 for package: initial-setup-gui-0.3.9.45-1.el7.centos.x86_64
---> Package libcanberra-gtk2.x86_64 0:0.30-9.el7 will be installed
--> Processing Dependency: libvorbisfile.so.3()(64bit) for package: libcanberra-gtk2-0.30-9.el7.x86_64
--> Processing Dependency: libvorbis.so.0()(64bit) for package: libcanberra-gtk2-0.30-9.el7.x86_64
--> Processing Dependency: libtdb.so.1()(64bit) for package: libcanberra-gtk2-0.30-9.el7.x86_64
--> Processing Dependency: libogg.so.0()(64bit) for package: libcanberra-gtk2-0.30-9.el7.x86_64
--> Processing Dependency: libltdl.so.7()(64bit) for package: libcanberra-gtk2-0.30-9.el7.x86_64
---> Package libcanberra-gtk3.x86_64 0:0.30-9.el7 will be installed
---> Package libproxy-mozjs.x86_64 0:0.4.11-11.el7 will be installed
---> Package librsvg2.x86_64 0:2.40.20-1.el7 will be installed
---> Package libsane-hpaio.x86_64 0:3.15.9-5.el7 will be installed
--> Processing Dependency: hplip-libs(x86-64) = 3.15.9-5.el7 for package: libsane-hpaio-3.15.9-5.el7.x86_64
--> Processing Dependency: sane-backends for package: libsane-hpaio-3.15.9-5.el7.x86_64
--> Processing Dependency: libhpmud.so.0()(64bit) for package: libsane-hpaio-3.15.9-5.el7.x86_64
--> Processing Dependency: libhpipp.so.0()(64bit) for package: libsane-hpaio-3.15.9-5.el7.x86_64
--> Processing Dependency: libhpip.so.0()(64bit) for package: libsane-hpaio-3.15.9-5.el7.x86_64
---> Package metacity.x86_64 0:2.34.13-7.el7 will be installed
---> Package mousetweaks.x86_64 0:3.12.0-1.el7 will be installed
---> Package nautilus.x86_64 0:3.26.3.1-7.el7 will be installed
--> Processing Dependency: brasero-nautilus for package: nautilus-3.26.3.1-7.el7.x86_64
---> Package nautilus-sendto.x86_64 1:3.8.6-1.el7 will be installed
---> Package nm-connection-editor.x86_64 0:1.8.6-2.el7 will be installed
--> Processing Dependency: /usr/bin/gtk-update-icon-cache for package: nm-connection-editor-1.8.6-2.el7.x86_64
---> Package orca.x86_64 0:3.6.3-4.el7 will be installed
--> Processing Dependency: python-brlapi >= 0.5.1 for package: orca-3.6.3-4.el7.x86_64
--> Processing Dependency: speech-dispatcher-python for package: orca-3.6.3-4.el7.x86_64
--> Processing Dependency: speech-dispatcher for package: orca-3.6.3-4.el7.x86_64
--> Processing Dependency: pyatspi for package: orca-3.6.3-4.el7.x86_64
--> Processing Dependency: libwnck3 for package: orca-3.6.3-4.el7.x86_64
--> Processing Dependency: liblouis-python for package: orca-3.6.3-4.el7.x86_64
---> Package qgnomeplatform.x86_64 0:0.3-5.el7 will be installed
--> Processing Dependency: qt5-qtbase(x86-64) = 5.9.7 for package: qgnomeplatform-0.3-5.el7.x86_64
--> Processing Dependency: libQt5Widgets.so.5(Qt_5)(64bit) for package: qgnomeplatform-0.3-5.el7.x86_64
--> Processing Dependency: libQt5Gui.so.5(Qt_5_PRIVATE_API)(64bit) for package: qgnomeplatform-0.3-5.el7.x86_64
--> Processing Dependency: libQt5Gui.so.5(Qt_5)(64bit) for package: qgnomeplatform-0.3-5.el7.x86_64
--> Processing Dependency: libQt5Core.so.5(Qt_5.9)(64bit) for package: qgnomeplatform-0.3-5.el7.x86_64
--> Processing Dependency: libQt5Core.so.5(Qt_5)(64bit) for package: qgnomeplatform-0.3-5.el7.x86_64
--> Processing Dependency: highcontrast-qt5(x86-64) for package: qgnomeplatform-0.3-5.el7.x86_64
--> Processing Dependency: adwaita-qt5(x86-64) for package: qgnomeplatform-0.3-5.el7.x86_64
--> Processing Dependency: libQt5Widgets.so.5()(64bit) for package: qgnomeplatform-0.3-5.el7.x86_64
--> Processing Dependency: libQt5Gui.so.5()(64bit) for package: qgnomeplatform-0.3-5.el7.x86_64
--> Processing Dependency: libQt5DBus.so.5()(64bit) for package: qgnomeplatform-0.3-5.el7.x86_64
--> Processing Dependency: libQt5Core.so.5()(64bit) for package: qgnomeplatform-0.3-5.el7.x86_64
---> Package sane-backends-drivers-scanners.x86_64 0:1.0.24-12.el7 will be installed
--> Processing Dependency: sane-backends-libs(x86-64) = 1.0.24-12.el7 for package: sane-backends-drivers-scanners-1.0.24-12.el7.x86_64
--> Processing Dependency: libv4l1.so.0()(64bit) for package: sane-backends-drivers-scanners-1.0.24-12.el7.x86_64
--> Processing Dependency: libieee1284.so.3()(64bit) for package: sane-backends-drivers-scanners-1.0.24-12.el7.x86_64
---> Package seahorse.x86_64 0:3.20.0-1.el7 will be installed
--> Processing Dependency: pinentry-gui for package: seahorse-3.20.0-1.el7.x86_64
--> Processing Dependency: libavahi-glib.so.1()(64bit) for package: seahorse-3.20.0-1.el7.x86_64
---> Package setroubleshoot.x86_64 0:3.2.30-8.el7 will be installed
--> Processing Dependency: setroubleshoot-server = 3.2.30-8.el7 for package: setroubleshoot-3.2.30-8.el7.x86_64
--> Processing Dependency: pygtk2-libglade >= 2.9.2 for package: setroubleshoot-3.2.30-8.el7.x86_64
--> Processing Dependency: xdg-utils for package: setroubleshoot-3.2.30-8.el7.x86_64
--> Processing Dependency: libreport-gtk for package: setroubleshoot-3.2.30-8.el7.x86_64
---> Package sushi.x86_64 0:3.28.3-1.el7 will be installed
--> Processing Dependency: libmusicbrainz5.so.0()(64bit) for package: sushi-3.28.3-1.el7.x86_64
---> Package totem.x86_64 1:3.26.2-1.el7 will be installed
--> Processing Dependency: libtotem-plparser.so.18(LIBTOTEM_PL_PARSER_MINI_1.0)(64bit) for package: 1:totem-3.26.2-1.el7.x86_64
--> Processing Dependency: gstreamer1-plugins-ugly-free(x86-64) for package: 1:totem-3.26.2-1.el7.x86_64
--> Processing Dependency: grilo-plugins(x86-64) for package: 1:totem-3.26.2-1.el7.x86_64
--> Processing Dependency: libtotem-plparser.so.18()(64bit) for package: 1:totem-3.26.2-1.el7.x86_64
---> Package totem-nautilus.x86_64 1:3.26.2-1.el7 will be installed
---> Package vinagre.x86_64 0:3.22.0-14.el7 will be installed
--> Processing Dependency: libgvnc-1.0.so.0()(64bit) for package: vinagre-3.22.0-14.el7.x86_64
--> Processing Dependency: libfreerdp2.so.2()(64bit) for package: vinagre-3.22.0-14.el7.x86_64
--> Processing Dependency: libavahi-ui-gtk3.so.0()(64bit) for package: vinagre-3.22.0-14.el7.x86_64
--> Processing Dependency: libavahi-gobject.so.0()(64bit) for package: vinagre-3.22.0-14.el7.x86_64
---> Package vino.x86_64 0:3.22.0-7.el7 will be installed
---> Package xdg-desktop-portal-gtk.x86_64 0:1.0.2-1.el7 will be installed
--> Processing Dependency: xdg-desktop-portal >= 1.0.2 for package: xdg-desktop-portal-gtk-1.0.2-1.el7.x86_64
---> Package xdg-user-dirs-gtk.x86_64 0:0.10-4.el7 will be installed
--> Processing Dependency: xdg-user-dirs for package: xdg-user-dirs-gtk-0.10-4.el7.x86_64
---> Package yelp.x86_64 2:3.28.1-1.el7 will be installed
--> Processing Dependency: yelp-libs(x86-64) = 2:3.28.1-1.el7 for package: 2:yelp-3.28.1-1.el7.x86_64
--> Processing Dependency: yelp-xsl for package: 2:yelp-3.28.1-1.el7.x86_64
--> Processing Dependency: libyelp.so.0()(64bit) for package: 2:yelp-3.28.1-1.el7.x86_64
--> Processing Dependency: libxslt.so.1()(64bit) for package: 2:yelp-3.28.1-1.el7.x86_64
--> Processing Dependency: libexslt.so.0()(64bit) for package: 2:yelp-3.28.1-1.el7.x86_64
--> Running transaction check
---> Package GConf2.x86_64 0:3.2.6-8.el7 will be installed
---> Package ModemManager-glib.x86_64 0:1.6.10-4.el7 will be installed
---> Package NetworkManager-glib.x86_64 1:1.18.8-2.el7_9 will be installed
---> Package NetworkManager-libreswan.x86_64 0:1.2.4-2.el7 will be installed
--> Processing Dependency: /usr/sbin/ipsec for package: NetworkManager-libreswan-1.2.4-2.el7.x86_64
---> Package NetworkManager-wifi.x86_64 1:1.18.8-2.el7_9 will be installed
---> Package PackageKit.x86_64 0:1.1.10-2.el7.centos will be installed
--> Processing Dependency: PackageKit-backend for package: PackageKit-1.1.10-2.el7.centos.x86_64
---> Package PackageKit-glib.x86_64 0:1.1.10-2.el7.centos will be installed
---> Package abattis-cantarell-fonts.noarch 0:0.0.25-1.el7 will be installed
--> Processing Dependency: fontpackages-filesystem for package: abattis-cantarell-fonts-0.0.25-1.el7.noarch
---> Package abrt.x86_64 0:2.1.11-60.el7.centos will be installed
--> Processing Dependency: abrt-python = 2.1.11-60.el7.centos for package: abrt-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: abrt-libs = 2.1.11-60.el7.centos for package: abrt-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: sos >= 3.6 for package: abrt-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: satyr >= 0.13-10 for package: abrt-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: libreport-plugin-ureport >= 2.1.11-46 for package: abrt-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: libreport >= 2.1.11-46 for package: abrt-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: python-augeas for package: abrt-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: libreport-plugin-rhtsupport for package: abrt-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: libsatyr.so.3()(64bit) for package: abrt-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: libreport.so.0()(64bit) for package: abrt-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: libabrt.so.0()(64bit) for package: abrt-2.1.11-60.el7.centos.x86_64
---> Package abrt-addon-ccpp.x86_64 0:2.1.11-60.el7.centos will be installed
--> Processing Dependency: abrt-retrace-client for package: abrt-addon-ccpp-2.1.11-60.el7.centos.x86_64
---> Package abrt-addon-kerneloops.x86_64 0:2.1.11-60.el7.centos will be installed
---> Package abrt-addon-pstoreoops.x86_64 0:2.1.11-60.el7.centos will be installed
---> Package abrt-addon-python.x86_64 0:2.1.11-60.el7.centos will be installed
--> Processing Dependency: systemd-python for package: abrt-addon-python-2.1.11-60.el7.centos.x86_64
---> Package abrt-addon-vmcore.x86_64 0:2.1.11-60.el7.centos will be installed
---> Package abrt-addon-xorg.x86_64 0:2.1.11-60.el7.centos will be installed
---> Package abrt-gui.x86_64 0:2.1.11-60.el7.centos will be installed
--> Processing Dependency: abrt-gui-libs = 2.1.11-60.el7.centos for package: abrt-gui-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: abrt-dbus = 2.1.11-60.el7.centos for package: abrt-gui-2.1.11-60.el7.centos.x86_64
--> Processing Dependency: libabrt_gui.so.0()(64bit) for package: abrt-gui-2.1.11-60.el7.centos.x86_64
---> Package accountsservice.x86_64 0:0.6.50-7.el7 will be installed
---> Package accountsservice-libs.x86_64 0:0.6.50-7.el7 will be installed
---> Package adwaita-gtk2-theme.x86_64 0:3.28-2.el7 will be installed
---> Package adwaita-icon-theme.noarch 0:3.28.0-1.el7 will be installed
--> Processing Dependency: adwaita-cursor-theme = 3.28.0-1.el7 for package: adwaita-icon-theme-3.28.0-1.el7.noarch
---> Package adwaita-qt5.x86_64 0:1.0-1.el7 will be installed
---> Package anaconda-gui.x86_64 0:21.48.22.159-1.el7.centos will be installed
--> Processing Dependency: anaconda-widgets = 21.48.22.159-1.el7.centos for package: anaconda-gui-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: anaconda-core = 21.48.22.159-1.el7.centos for package: anaconda-gui-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: python-meh-gui >= 0.23-1 for package: anaconda-gui-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: libxklavier >= 5.4 for package: anaconda-gui-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: libtimezonemap >= 0.4.1-2 for package: anaconda-gui-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: keybinder3 for package: anaconda-gui-21.48.22.159-1.el7.centos.x86_64
---> Package appstream-data.noarch 0:7-20180614.el7 will be installed
---> Package atk.x86_64 0:2.28.1-2.el7 will be installed
---> Package atkmm.x86_64 0:2.24.2-1.el7 will be installed
---> Package avahi-glib.x86_64 0:0.6.31-20.el7 will be installed
---> Package avahi-gobject.x86_64 0:0.6.31-20.el7 will be installed
---> Package avahi-libs.x86_64 0:0.6.31-20.el7 will be installed
---> Package avahi-ui-gtk3.x86_64 0:0.6.31-20.el7 will be installed
---> Package bluez.x86_64 0:5.44-7.el7 will be installed
---> Package bolt.x86_64 0:0.7-1.el7 will be installed
---> Package brasero-nautilus.x86_64 0:3.12.2-5.el7_9.1 will be installed
--> Processing Dependency: brasero = 3.12.2-5.el7_9.1 for package: brasero-nautilus-3.12.2-5.el7_9.1.x86_64
--> Processing Dependency: libbrasero-utils3.so.1()(64bit) for package: brasero-nautilus-3.12.2-5.el7_9.1.x86_64
--> Processing Dependency: libbrasero-media3.so.1()(64bit) for package: brasero-nautilus-3.12.2-5.el7_9.1.x86_64
--> Processing Dependency: libbrasero-burn3.so.1()(64bit) for package: brasero-nautilus-3.12.2-5.el7_9.1.x86_64
---> Package cairo.x86_64 0:1.15.12-4.el7 will be installed
---> Package cairo-gobject.x86_64 0:1.15.12-4.el7 will be installed
---> Package cairomm.x86_64 0:1.12.0-1.el7 will be installed
---> Package cheese-libs.x86_64 2:3.28.0-1.el7 will be installed
---> Package clutter.x86_64 0:1.26.2-2.el7 will be installed
--> Processing Dependency: libinput(x86-64) >= 0.19.0 for package: clutter-1.26.2-2.el7.x86_64
--> Processing Dependency: libinput.so.10(LIBINPUT_0.21.0)(64bit) for package: clutter-1.26.2-2.el7.x86_64
--> Processing Dependency: libinput.so.10(LIBINPUT_0.20.0)(64bit) for package: clutter-1.26.2-2.el7.x86_64
--> Processing Dependency: libinput.so.10(LIBINPUT_0.12.0)(64bit) for package: clutter-1.26.2-2.el7.x86_64
--> Processing Dependency: libinput.so.10()(64bit) for package: clutter-1.26.2-2.el7.x86_64
---> Package clutter-gst2.x86_64 0:2.0.18-1.el7 will be installed
---> Package clutter-gst3.x86_64 0:3.0.26-1.el7 will be installed
---> Package clutter-gtk.x86_64 0:1.8.4-1.el7 will be installed
---> Package cogl.x86_64 0:1.22.2-2.el7 will be installed
---> Package colord.x86_64 0:1.3.4-2.el7 will be installed
--> Processing Dependency: libgusb.so.2(LIBGUSB_0.2.2)(64bit) for package: colord-1.3.4-2.el7.x86_64
--> Processing Dependency: libgusb.so.2(LIBGUSB_0.1.0)(64bit) for package: colord-1.3.4-2.el7.x86_64
--> Processing Dependency: color-filesystem for package: colord-1.3.4-2.el7.x86_64
--> Processing Dependency: libgusb.so.2()(64bit) for package: colord-1.3.4-2.el7.x86_64
---> Package colord-gtk.x86_64 0:0.1.25-4.el7 will be installed
--> Processing Dependency: libcolordprivate.so.1()(64bit) for package: colord-gtk-0.1.25-4.el7.x86_64
--> Processing Dependency: libcolord.so.1()(64bit) for package: colord-gtk-0.1.25-4.el7.x86_64
---> Package colord-libs.x86_64 0:1.3.4-2.el7 will be installed
---> Package compat-exiv2-026.x86_64 0:0.26-2.el7 will be installed
---> Package compat-gnome-desktop314.x86_64 0:3.14.2-1.el7 will be installed
---> Package control-center-filesystem.x86_64 1:3.28.1-8.el7_9.1 will be installed
---> Package cups-libs.x86_64 1:1.6.3-51.el7 will be installed
---> Package cups-pk-helper.x86_64 0:0.2.6-2.el7 will be installed
---> Package dbus-x11.x86_64 1:1.10.24-15.el7 will be installed
---> Package desktop-file-utils.x86_64 0:0.23-2.el7 will be installed
--> Processing Dependency: emacs-filesystem for package: desktop-file-utils-0.23-2.el7.x86_64
---> Package elfutils.x86_64 0:0.176-5.el7 will be installed
---> Package enchant.x86_64 1:1.6.0-8.el7 will be installed
--> Processing Dependency: libhunspell-1.3.so.0()(64bit) for package: 1:enchant-1.6.0-8.el7.x86_64
---> Package evince-libs.x86_64 0:3.28.2-10.el7 will be installed
--> Processing Dependency: poppler-glib >= 0.26.5-36 for package: evince-libs-3.28.2-10.el7.x86_64
--> Processing Dependency: libspectre.so.1()(64bit) for package: evince-libs-3.28.2-10.el7.x86_64
--> Processing Dependency: libpoppler-glib.so.18()(64bit) for package: evince-libs-3.28.2-10.el7.x86_64
--> Processing Dependency: libgxps.so.2()(64bit) for package: evince-libs-3.28.2-10.el7.x86_64
---> Package evolution-data-server.x86_64 0:3.28.5-5.el7_9.1 will be installed
--> Processing Dependency: evolution-data-server-langpacks = 3.28.5-5.el7_9.1 for package: evolution-data-server-3.28.5-5.el7_9.1.x86_64
--> Processing Dependency: libicuuc.so.50()(64bit) for package: evolution-data-server-3.28.5-5.el7_9.1.x86_64
--> Processing Dependency: libicui18n.so.50()(64bit) for package: evolution-data-server-3.28.5-5.el7_9.1.x86_64
--> Processing Dependency: libicudata.so.50()(64bit) for package: evolution-data-server-3.28.5-5.el7_9.1.x86_64
---> Package exempi.x86_64 0:2.2.0-9.el7 will be installed
---> Package farstream02.x86_64 0:0.2.3-3.el7 will be installed
--> Processing Dependency: libnice.so.10()(64bit) for package: farstream02-0.2.3-3.el7.x86_64
--> Processing Dependency: libgupnp-igd-1.0.so.4()(64bit) for package: farstream02-0.2.3-3.el7.x86_64
--> Processing Dependency: libgupnp-1.0.so.4()(64bit) for package: farstream02-0.2.3-3.el7.x86_64
---> Package flatpak.x86_64 0:1.0.9-12.el7_9 will be installed
---> Package flatpak-libs.x86_64 0:1.0.9-12.el7_9 will be installed
---> Package folks.x86_64 1:0.11.4-1.el7 will be installed
---> Package fontconfig.x86_64 0:2.13.0-4.3.el7 will be installed
--> Processing Dependency: dejavu-sans-fonts for package: fontconfig-2.13.0-4.3.el7.x86_64
---> Package fprintd.x86_64 0:0.8.1-2.el7 will be installed
--> Processing Dependency: libfprint.so.0()(64bit) for package: fprintd-0.8.1-2.el7.x86_64
---> Package freerdp-libs.x86_64 0:2.1.1-5.el7_9 will be installed
--> Processing Dependency: libwinpr(x86-64) = 2.1.1-5.el7_9 for package: freerdp-libs-2.1.1-5.el7_9.x86_64
--> Processing Dependency: libwinpr2.so.2()(64bit) for package: freerdp-libs-2.1.1-5.el7_9.x86_64
--> Processing Dependency: libgsm.so.1()(64bit) for package: freerdp-libs-2.1.1-5.el7_9.x86_64
---> Package fuse.x86_64 0:2.9.2-11.el7 will be installed
---> Package fwupd.x86_64 0:1.0.8-5.el7 will be installed
--> Processing Dependency: libfwup.so.1(libfwup.so.1)(64bit) for package: fwupd-1.0.8-5.el7.x86_64
--> Processing Dependency: libfwup.so.1(LIBFWUP_1.12)(64bit) for package: fwupd-1.0.8-5.el7.x86_64
--> Processing Dependency: libsmbios_c.so.2()(64bit) for package: fwupd-1.0.8-5.el7.x86_64
--> Processing Dependency: libfwup.so.1()(64bit) for package: fwupd-1.0.8-5.el7.x86_64
---> Package gcr.x86_64 0:3.28.0-1.el7 will be installed
---> Package gdb.x86_64 0:7.6.1-120.el7 will be installed
---> Package gdk-pixbuf2.x86_64 0:2.36.12-3.el7 will be installed
--> Processing Dependency: libjasper.so.1()(64bit) for package: gdk-pixbuf2-2.36.12-3.el7.x86_64
---> Package genisoimage.x86_64 0:1.1.11-25.el7 will be installed
--> Processing Dependency: libusal = 1.1.11-25.el7 for package: genisoimage-1.1.11-25.el7.x86_64
--> Processing Dependency: libusal.so.0()(64bit) for package: genisoimage-1.1.11-25.el7.x86_64
--> Processing Dependency: librols.so.0()(64bit) for package: genisoimage-1.1.11-25.el7.x86_64
---> Package geoclue2.x86_64 0:2.4.8-1.el7 will be installed
---> Package geoclue2-libs.x86_64 0:2.4.8-1.el7 will be installed
---> Package geocode-glib.x86_64 0:3.26.0-3.el7 will be installed
---> Package gjs.x86_64 0:1.52.5-1.el7_6 will be installed
--> Processing Dependency: libmozjs-52.so.0(js)(64bit) for package: gjs-1.52.5-1.el7_6.x86_64
--> Processing Dependency: libmozjs-52.so.0()(64bit) for package: gjs-1.52.5-1.el7_6.x86_64
---> Package glibmm24.x86_64 0:2.56.0-1.el7 will be installed
---> Package glx-utils.x86_64 0:8.3.0-10.el7 will be installed
---> Package gnome-abrt.x86_64 0:0.3.4-9.el7 will be installed
--> Processing Dependency: python-inotify for package: gnome-abrt-0.3.4-9.el7.x86_64
--> Processing Dependency: pygobject3 for package: gnome-abrt-0.3.4-9.el7.x86_64
---> Package gnome-bluetooth-libs.x86_64 1:3.28.2-1.el7 will be installed
---> Package gnome-desktop3.x86_64 0:3.28.2-2.el7 will be installed
---> Package gnome-keyring-pam.x86_64 0:3.28.2-1.el7 will be installed
--> Processing Dependency: gnome-keyring(x86-64) = 3.28.2-1.el7 for package: gnome-keyring-pam-3.28.2-1.el7.x86_64
---> Package gnome-menus.x86_64 0:3.13.3-3.el7 will be installed
--> Processing Dependency: redhat-menus for package: gnome-menus-3.13.3-3.el7.x86_64
---> Package gnome-online-accounts.x86_64 0:3.28.2-1.el7 will be installed
---> Package gnome-packagekit-common.x86_64 0:3.28.0-1.el7 will be installed
---> Package gnome-packagekit-installer.x86_64 0:3.28.0-1.el7 will be installed
---> Package gnome-shell-extension-alternate-tab.noarch 0:3.28.1-17.el7_9 will be installed
--> Processing Dependency: gnome-shell-extension-common = 3.28.1-17.el7_9 for package: gnome-shell-extension-alternate-tab-3.28.1-17.el7_9.noarch
---> Package gnome-shell-extension-apps-menu.noarch 0:3.28.1-17.el7_9 will be installed
---> Package gnome-shell-extension-horizontal-workspaces.noarch 0:3.28.1-17.el7_9 will be installed
---> Package gnome-shell-extension-launch-new-instance.noarch 0:3.28.1-17.el7_9 will be installed
---> Package gnome-shell-extension-places-menu.noarch 0:3.28.1-17.el7_9 will be installed
---> Package gnome-shell-extension-top-icons.noarch 0:3.28.1-17.el7_9 will be installed
---> Package gnome-shell-extension-user-theme.noarch 0:3.28.1-17.el7_9 will be installed
---> Package gnome-shell-extension-window-list.noarch 0:3.28.1-17.el7_9 will be installed
---> Package gnome-video-effects.noarch 0:0.4.3-1.el7 will be installed
--> Processing Dependency: frei0r-plugins for package: gnome-video-effects-0.4.3-1.el7.noarch
---> Package google-noto-emoji-color-fonts.noarch 0:20180508-4.el7 will be installed
---> Package grilo.x86_64 0:0.3.6-1.el7 will be installed
--> Processing Dependency: liboauth.so.0()(64bit) for package: grilo-0.3.6-1.el7.x86_64
---> Package grilo-plugins.x86_64 0:0.3.7-1.el7 will be installed
--> Processing Dependency: dleyna-server for package: grilo-plugins-0.3.7-1.el7.x86_64
--> Processing Dependency: libmediaart-2.0.so.0()(64bit) for package: grilo-plugins-0.3.7-1.el7.x86_64
--> Processing Dependency: libgom-1.0.so.0()(64bit) for package: grilo-plugins-0.3.7-1.el7.x86_64
--> Processing Dependency: libdmapsharing-3.0.so.2()(64bit) for package: grilo-plugins-0.3.7-1.el7.x86_64
---> Package gsettings-desktop-schemas.x86_64 0:3.28.0-3.el7 will be installed
---> Package gsound.x86_64 0:1.0.2-2.el7 will be installed
---> Package gspell.x86_64 0:1.6.1-1.el7 will be installed
---> Package gstreamer1.x86_64 0:1.10.4-2.el7 will be installed
---> Package gstreamer1-plugins-bad-free.x86_64 0:1.10.4-3.el7 will be installed
--> Processing Dependency: libsndfile.so.1(libsndfile.so.1.0)(64bit) for package: gstreamer1-plugins-bad-free-1.10.4-3.el7.x86_64
--> Processing Dependency: libsrtp.so.0()(64bit) for package: gstreamer1-plugins-bad-free-1.10.4-3.el7.x86_64
--> Processing Dependency: libsndfile.so.1()(64bit) for package: gstreamer1-plugins-bad-free-1.10.4-3.el7.x86_64
--> Processing Dependency: liborc-0.4.so.0()(64bit) for package: gstreamer1-plugins-bad-free-1.10.4-3.el7.x86_64
--> Processing Dependency: libopus.so.0()(64bit) for package: gstreamer1-plugins-bad-free-1.10.4-3.el7.x86_64
--> Processing Dependency: libmpcdec.so.5()(64bit) for package: gstreamer1-plugins-bad-free-1.10.4-3.el7.x86_64
--> Processing Dependency: libdvdnav.so.4()(64bit) for package: gstreamer1-plugins-bad-free-1.10.4-3.el7.x86_64
--> Processing Dependency: libSoundTouch.so.1()(64bit) for package: gstreamer1-plugins-bad-free-1.10.4-3.el7.x86_64
---> Package gstreamer1-plugins-base.x86_64 0:1.10.4-2.el7 will be installed
--> Processing Dependency: libtheoraenc.so.1(libtheoraenc_1.0)(64bit) for package: gstreamer1-plugins-base-1.10.4-2.el7.x86_64
--> Processing Dependency: libtheoradec.so.1(libtheoradec_1.0)(64bit) for package: gstreamer1-plugins-base-1.10.4-2.el7.x86_64
--> Processing Dependency: libvisual-0.4.so.0()(64bit) for package: gstreamer1-plugins-base-1.10.4-2.el7.x86_64
--> Processing Dependency: libtheoraenc.so.1()(64bit) for package: gstreamer1-plugins-base-1.10.4-2.el7.x86_64
--> Processing Dependency: libtheoradec.so.1()(64bit) for package: gstreamer1-plugins-base-1.10.4-2.el7.x86_64
--> Processing Dependency: libcdda_paranoia.so.0()(64bit) for package: gstreamer1-plugins-base-1.10.4-2.el7.x86_64
--> Processing Dependency: libcdda_interface.so.0()(64bit) for package: gstreamer1-plugins-base-1.10.4-2.el7.x86_64
--> Processing Dependency: libXv.so.1()(64bit) for package: gstreamer1-plugins-base-1.10.4-2.el7.x86_64
---> Package gstreamer1-plugins-good.x86_64 0:1.10.4-2.el7 will be installed
--> Processing Dependency: libwavpack.so.1()(64bit) for package: gstreamer1-plugins-good-1.10.4-2.el7.x86_64
--> Processing Dependency: libvpx.so.1()(64bit) for package: gstreamer1-plugins-good-1.10.4-2.el7.x86_64
--> Processing Dependency: libtag.so.1()(64bit) for package: gstreamer1-plugins-good-1.10.4-2.el7.x86_64
--> Processing Dependency: libspeex.so.1()(64bit) for package: gstreamer1-plugins-good-1.10.4-2.el7.x86_64
--> Processing Dependency: libshout.so.3()(64bit) for package: gstreamer1-plugins-good-1.10.4-2.el7.x86_64
--> Processing Dependency: librom1394.so.0()(64bit) for package: gstreamer1-plugins-good-1.10.4-2.el7.x86_64
--> Processing Dependency: libraw1394.so.11()(64bit) for package: gstreamer1-plugins-good-1.10.4-2.el7.x86_64
--> Processing Dependency: libiec61883.so.0()(64bit) for package: gstreamer1-plugins-good-1.10.4-2.el7.x86_64
--> Processing Dependency: libdv.so.4()(64bit) for package: gstreamer1-plugins-good-1.10.4-2.el7.x86_64
--> Processing Dependency: libavc1394.so.0()(64bit) for package: gstreamer1-plugins-good-1.10.4-2.el7.x86_64
--> Processing Dependency: libFLAC.so.8()(64bit) for package: gstreamer1-plugins-good-1.10.4-2.el7.x86_64
---> Package gstreamer1-plugins-ugly-free.x86_64 0:1.10.4-3.el7 will be installed
--> Processing Dependency: libcdio.so.15(CDIO_15)(64bit) for package: gstreamer1-plugins-ugly-free-1.10.4-3.el7.x86_64
--> Processing Dependency: libmpg123.so.0()(64bit) for package: gstreamer1-plugins-ugly-free-1.10.4-3.el7.x86_64
--> Processing Dependency: libcdio.so.15()(64bit) for package: gstreamer1-plugins-ugly-free-1.10.4-3.el7.x86_64
---> Package gtk-update-icon-cache.x86_64 0:3.22.30-8.el7_9 will be installed
---> Package gtk-vnc2.x86_64 0:0.7.0-3.el7 will be installed
---> Package gtk2.x86_64 0:2.24.31-1.el7 will be installed
---> Package gtk3.x86_64 0:3.22.30-8.el7_9 will be installed
---> Package gtkmm30.x86_64 0:3.22.2-1.el7 will be installed
---> Package gtksourceview3.x86_64 0:3.24.8-2.el7 will be installed
---> Package gucharmap-libs.x86_64 0:10.0.4-1.el7 will be installed
---> Package gvfs.x86_64 0:1.36.2-7.el7_9 will be installed
--> Processing Dependency: libcdio_paranoia.so.1(CDIO_PARANOIA_1)(64bit) for package: gvfs-1.36.2-7.el7_9.x86_64
--> Processing Dependency: libcdio_cdda.so.1(CDIO_CDDA_1)(64bit) for package: gvfs-1.36.2-7.el7_9.x86_64
--> Processing Dependency: libcdio_paranoia.so.1()(64bit) for package: gvfs-1.36.2-7.el7_9.x86_64
--> Processing Dependency: libcdio_cdda.so.1()(64bit) for package: gvfs-1.36.2-7.el7_9.x86_64
--> Processing Dependency: libbluray.so.1()(64bit) for package: gvfs-1.36.2-7.el7_9.x86_64
---> Package gvfs-client.x86_64 0:1.36.2-7.el7_9 will be installed
---> Package gvnc.x86_64 0:0.7.0-3.el7 will be installed
---> Package harfbuzz.x86_64 0:1.7.5-2.el7 will be installed
--> Processing Dependency: libgraphite2.so.3()(64bit) for package: harfbuzz-1.7.5-2.el7.x86_64
---> Package hicolor-icon-theme.noarch 0:0.12-7.el7 will be installed
---> Package highcontrast-qt5.x86_64 0:0.1-2.el7 will be installed
---> Package hplip-libs.x86_64 0:3.15.9-5.el7 will be installed
--> Processing Dependency: hplip-common(x86-64) = 3.15.9-5.el7 for package: hplip-libs-3.15.9-5.el7.x86_64
--> Processing Dependency: libnetsnmp.so.31()(64bit) for package: hplip-libs-3.15.9-5.el7.x86_64
---> Package ibus.x86_64 0:1.5.17-12.el7_9 will be installed
--> Processing Dependency: ibus-setup = 1.5.17-12.el7_9 for package: ibus-1.5.17-12.el7_9.x86_64
--> Processing Dependency: ibus-gtk3(x86-64) = 1.5.17-12.el7_9 for package: ibus-1.5.17-12.el7_9.x86_64
--> Processing Dependency: ibus-gtk2(x86-64) = 1.5.17-12.el7_9 for package: ibus-1.5.17-12.el7_9.x86_64
---> Package ibus-libs.x86_64 0:1.5.17-12.el7_9 will be installed
---> Package initial-setup.x86_64 0:0.3.9.45-1.el7.centos will be installed
--> Processing Dependency: anaconda-tui >= 21.48.22.102 for package: initial-setup-0.3.9.45-1.el7.centos.x86_64
--> Processing Dependency: python-di for package: initial-setup-0.3.9.45-1.el7.centos.x86_64
---> Package iso-codes.noarch 0:3.46-2.el7 will be installed
--> Processing Dependency: xml-common for package: iso-codes-3.46-2.el7.noarch
---> Package json-glib.x86_64 0:1.4.2-2.el7 will be installed
---> Package lcms2.x86_64 0:2.6-3.el7 will be installed
---> Package libXcomposite.x86_64 0:0.4.4-4.1.el7 will be installed
---> Package libappstream-glib.x86_64 0:0.7.8-2.el7 will be installed
--> Processing Dependency: libgcab-1.0.so.0(LIBGCAB1_0.2)(64bit) for package: libappstream-glib-0.7.8-2.el7.x86_64
--> Processing Dependency: libgcab-1.0.so.0(LIBGCAB1_0.0)(64bit) for package: libappstream-glib-0.7.8-2.el7.x86_64
--> Processing Dependency: libgcab-1.0.so.0()(64bit) for package: libappstream-glib-0.7.8-2.el7.x86_64
---> Package libcanberra.x86_64 0:0.30-9.el7 will be installed
--> Processing Dependency: sound-theme-freedesktop for package: libcanberra-0.30-9.el7.x86_64
---> Package libchamplain.x86_64 0:0.12.16-2.el7 will be installed
---> Package libchamplain-gtk.x86_64 0:0.12.16-2.el7 will be installed
---> Package libdvdread.x86_64 0:5.0.3-3.el7 will be installed
---> Package libepoxy.x86_64 0:1.5.2-1.el7 will be installed
---> Package libexif.x86_64 0:0.6.22-2.el7_9 will be installed
---> Package libgdata.x86_64 0:0.17.9-1.el7 will be installed
---> Package libgee.x86_64 0:0.20.1-1.el7 will be installed
---> Package libglvnd-egl.x86_64 1:1.0.1-0.8.git5baa1e5.el7 will be installed
--> Processing Dependency: mesa-libEGL(x86-64) >= 13.0.4-1 for package: 1:libglvnd-egl-1.0.1-0.8.git5baa1e5.el7.x86_64
---> Package libglvnd-gles.x86_64 1:1.0.1-0.8.git5baa1e5.el7 will be installed
---> Package libgnomekbd.x86_64 0:3.26.0-3.el7 will be installed
---> Package libgovirt.x86_64 0:0.3.4-5.el7 will be installed
---> Package libgphoto2.x86_64 0:2.5.15-3.el7 will be installed
--> Processing Dependency: lockdev for package: libgphoto2-2.5.15-3.el7.x86_64
--> Processing Dependency: liblockdev.so.1()(64bit) for package: libgphoto2-2.5.15-3.el7.x86_64
--> Processing Dependency: libgd.so.2()(64bit) for package: libgphoto2-2.5.15-3.el7.x86_64
---> Package libgtop2.x86_64 0:2.38.0-3.el7 will be installed
---> Package libgudev1.x86_64 0:219-78.el7_9.7 will be installed
---> Package libgweather.x86_64 0:3.28.2-4.el7_9 will be installed
---> Package libical.x86_64 0:3.0.3-2.el7 will be installed
---> Package libieee1284.x86_64 0:0.2.11-15.el7 will be installed
---> Package libimobiledevice.x86_64 0:1.2.0-1.el7 will be installed
--> Processing Dependency: libusbmuxd.so.4()(64bit) for package: libimobiledevice-1.2.0-1.el7.x86_64
---> Package liblouis-python.noarch 0:2.5.2-12.el7_4 will be installed
--> Processing Dependency: liblouis = 2.5.2-12.el7_4 for package: liblouis-python-2.5.2-12.el7_4.noarch
---> Package libmtp.x86_64 0:1.1.14-1.el7 will be installed
---> Package libmusicbrainz5.x86_64 0:5.0.1-9.el7 will be installed
--> Processing Dependency: libneon.so.27()(64bit) for package: libmusicbrainz5-5.0.1-9.el7.x86_64
---> Package libnm-gtk.x86_64 0:1.8.6-2.el7 will be installed
--> Processing Dependency: mobile-broadband-provider-info >= 0.20090602 for package: libnm-gtk-1.8.6-2.el7.x86_64
---> Package libnma.x86_64 0:1.8.6-2.el7 will be installed
---> Package libnotify.x86_64 0:0.7.7-1.el7 will be installed
---> Package libogg.x86_64 2:1.3.0-7.el7 will be installed
---> Package libosinfo.x86_64 0:1.1.0-5.el7 will be installed
--> Processing Dependency: osinfo-db-tools for package: libosinfo-1.1.0-5.el7.x86_64
--> Processing Dependency: osinfo-db for package: libosinfo-1.1.0-5.el7.x86_64
---> Package libpeas.x86_64 0:1.22.0-1.el7 will be installed
---> Package libpeas-gtk.x86_64 0:1.22.0-1.el7 will be installed
---> Package libpeas-loader-python.x86_64 0:1.22.0-1.el7 will be installed
---> Package libplist.x86_64 0:1.12-3.el7 will be installed
---> Package libproxy.x86_64 0:0.4.11-11.el7 will be installed
--> Processing Dependency: libmodman.so.1()(64bit) for package: libproxy-0.4.11-11.el7.x86_64
---> Package libreport-centos.x86_64 0:2.1.11-53.el7.centos will be installed
--> Processing Dependency: libreport-web = 2.1.11-53.el7.centos for package: libreport-centos-2.1.11-53.el7.centos.x86_64
---> Package libreport-gtk.x86_64 0:2.1.11-53.el7.centos will be installed
--> Processing Dependency: libreport-plugin-reportuploader = 2.1.11-53.el7.centos for package: libreport-gtk-2.1.11-53.el7.centos.x86_64
--> Processing Dependency: fros >= 1.0 for package: libreport-gtk-2.1.11-53.el7.centos.x86_64
--> Processing Dependency: libtar.so.1()(64bit) for package: libreport-gtk-2.1.11-53.el7.centos.x86_64
--> Processing Dependency: libaugeas.so.0()(64bit) for package: libreport-gtk-2.1.11-53.el7.centos.x86_64
---> Package libreport-plugin-mantisbt.x86_64 0:2.1.11-53.el7.centos will be installed
--> Processing Dependency: libxmlrpc_util.so.3()(64bit) for package: libreport-plugin-mantisbt-2.1.11-53.el7.centos.x86_64
--> Processing Dependency: libxmlrpc_client.so.3()(64bit) for package: libreport-plugin-mantisbt-2.1.11-53.el7.centos.x86_64
--> Processing Dependency: libxmlrpc.so.3()(64bit) for package: libreport-plugin-mantisbt-2.1.11-53.el7.centos.x86_64
---> Package libreport-python.x86_64 0:2.1.11-53.el7.centos will be installed
---> Package libsecret.x86_64 0:0.18.6-1.el7 will be installed
---> Package libsigc++20.x86_64 0:2.10.0-1.el7 will be installed
---> Package libsmbclient.x86_64 0:4.10.16-24.el7_9 will be installed
--> Processing Dependency: samba-common-libs = 4.10.16-24.el7_9 for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: samba-common = 4.10.16-24.el7_9 for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: samba-common = 4.10.16-24.el7_9 for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: samba-client-libs = 4.10.16-24.el7_9 for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libwbclient = 4.10.16-24.el7_9 for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libutil-cmdline-samba4.so(SAMBA_4.10.16)(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libtevent.so.0(TEVENT_0.9.9)(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libtevent.so.0(TEVENT_0.9.12)(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libtevent-util.so.0(TEVENT_UTIL_0.0.1)(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libtalloc.so.2(TALLOC_2.0.2)(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsmbconf.so.0(SMBCONF_0)(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsecrets3-samba4.so(SAMBA_4.10.16)(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsamba3-util-samba4.so(SAMBA_4.10.16)(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsamba-util.so.0(SAMBA_UTIL_0.0.1)(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsamba-security-samba4.so(SAMBA_4.10.16)(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsamba-errors.so.1(SAMBA_ERRORS_1)(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsamba-debug-samba4.so(SAMBA_4.10.16)(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libreplace-samba4.so(SAMBA_4.10.16)(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libndr.so.0(NDR_0.0.1)(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libndr-standard.so.0(NDR_STANDARD_0.0.1)(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libmsrpc3-samba4.so(SAMBA_4.10.16)(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: liblibsmb-samba4.so(SAMBA_4.10.16)(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: liblibcli-lsa3-samba4.so(SAMBA_4.10.16)(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libgse-samba4.so(SAMBA_4.10.16)(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libdcerpc-samba-samba4.so(SAMBA_4.10.16)(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libcli-smb-common-samba4.so(SAMBA_4.10.16)(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libwinbind-client-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libwbclient.so.0()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libutil-tdb-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libutil-setid-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libutil-reg-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libutil-cmdline-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libtime-basic-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libtevent.so.0()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libtevent-util.so.0()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libtdb-wrap-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libtalloc.so.2()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libtalloc-report-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsys-rw-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsocket-blocking-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsmbd-shim-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsmbconf.so.0()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsmb-transport-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libserver-role-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libserver-id-db-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsecrets3-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsamdb.so.0()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsamdb-common-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsamba3-util-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsamba-util.so.0()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsamba-sockets-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsamba-security-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsamba-modules-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsamba-hostconfig.so.0()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsamba-errors.so.1()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsamba-debug-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsamba-credentials.so.0()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libsamba-cluster-support-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libreplace-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libnetif-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libndr.so.0()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libndr-standard.so.0()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libndr-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libndr-samba-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libndr-nbt.so.0()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libndr-krb5pac.so.0()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libmsrpc3-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libmsghdr-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libmessages-util-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libmessages-dgm-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: liblibsmb-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: liblibcli-lsa3-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libldbsamba-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libldb.so.1()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libkrb5samba-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libiov-buf-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libinterfaces-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libgse-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libgensec-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libgenrand-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libflag-mapping-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libevents-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libdcerpc-samba-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libdcerpc-binding.so.0()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libdbwrap-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libcommon-auth-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libcluster-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libclidns-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libcliauth-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libcli-smb-common-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libcli-nbt-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libcli-ldap-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libcli-ldap-common-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libcli-cldap-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libauthkrb5-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libasn1util-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libaesni-intel-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libaddns-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libMESSAGING-SEND-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
--> Processing Dependency: libCHARSET3-samba4.so()(64bit) for package: libsmbclient-4.10.16-24.el7_9.x86_64
---> Package libsoup.x86_64 0:2.62.2-2.el7 will be installed
---> Package libtdb.x86_64 0:1.3.18-1.el7 will be installed
---> Package libtool-ltdl.x86_64 0:2.4.2-22.el7_3 will be installed
---> Package libudisks2.x86_64 0:2.8.4-1.el7 will be installed
---> Package libusbx.x86_64 0:1.0.21-1.el7 will be installed
---> Package libv4l.x86_64 0:0.9.5-4.el7 will be installed
---> Package libvirt-daemon-config-network.x86_64 0:4.5.0-36.el7_9.5 will be installed
--> Processing Dependency: libvirt-daemon-driver-network = 4.5.0-36.el7_9.5 for package: libvirt-daemon-config-network-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: libvirt-daemon = 4.5.0-36.el7_9.5 for package: libvirt-daemon-config-network-4.5.0-36.el7_9.5.x86_64
---> Package libvirt-daemon-kvm.x86_64 0:4.5.0-36.el7_9.5 will be installed
--> Processing Dependency: libvirt-daemon-driver-storage = 4.5.0-36.el7_9.5 for package: libvirt-daemon-kvm-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: libvirt-daemon-driver-secret = 4.5.0-36.el7_9.5 for package: libvirt-daemon-kvm-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: libvirt-daemon-driver-qemu = 4.5.0-36.el7_9.5 for package: libvirt-daemon-kvm-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: libvirt-daemon-driver-nwfilter = 4.5.0-36.el7_9.5 for package: libvirt-daemon-kvm-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: libvirt-daemon-driver-nodedev = 4.5.0-36.el7_9.5 for package: libvirt-daemon-kvm-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: libvirt-daemon-driver-interface = 4.5.0-36.el7_9.5 for package: libvirt-daemon-kvm-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: qemu-kvm for package: libvirt-daemon-kvm-4.5.0-36.el7_9.5.x86_64
---> Package libvirt-gconfig.x86_64 0:1.0.0-1.el7 will be installed
---> Package libvirt-gobject.x86_64 0:1.0.0-1.el7 will be installed
--> Processing Dependency: libvirt.so.0(LIBVIRT_1.2.8)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_1.2.6)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_1.2.5)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.9.8)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.9.7)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.9.5)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.9.4)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.9.2)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.9.13)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.9.11)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.9.10)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.9.0)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.8.6)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.8.2)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.8.0)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.7.3)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.7.2)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.7.1)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.6.4)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.6.0)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.5.0)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.4.1)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.3.2)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.3.0)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.2.1)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.2.0)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.10.2)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.1.1)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.1.0)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0(LIBVIRT_0.0.3)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt-glib-1.0.so.0(LIBVIRT_GLIB_0.1.4)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt-glib-1.0.so.0(LIBVIRT_GLIB_0.0.7)(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt.so.0()(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
--> Processing Dependency: libvirt-glib-1.0.so.0()(64bit) for package: libvirt-gobject-1.0.0-1.el7.x86_64
---> Package libvorbis.x86_64 1:1.3.3-8.el7.1 will be installed
---> Package libwacom.x86_64 0:0.30-1.el7 will be installed
--> Processing Dependency: libwacom-data for package: libwacom-0.30-1.el7.x86_64
---> Package libwayland-client.x86_64 0:1.15.0-1.el7 will be installed
---> Package libwayland-cursor.x86_64 0:1.15.0-1.el7 will be installed
---> Package libwayland-egl.x86_64 0:1.15.0-1.el7 will be installed
---> Package libwayland-server.x86_64 0:1.15.0-1.el7 will be installed
---> Package libwnck3.x86_64 0:3.24.1-2.el7 will be installed
--> Processing Dependency: libXRes.so.1()(64bit) for package: libwnck3-3.24.1-2.el7.x86_64
---> Package libxkbcommon.x86_64 0:0.7.1-3.el7 will be installed
---> Package libxslt.x86_64 0:1.1.28-6.el7 will be installed
---> Package lzop.x86_64 0:1.03-10.el7 will be installed
---> Package mesa-libgbm.x86_64 0:18.3.4-12.el7_9 will be installed
---> Package mtools.x86_64 0:4.0.18-5.el7 will be installed
---> Package mutter.x86_64 0:3.28.3-32.el7_9 will be installed
--> Processing Dependency: libxkbcommon-x11.so.0(V_0.5.0)(64bit) for package: mutter-3.28.3-32.el7_9.x86_64
--> Processing Dependency: libxkbcommon-x11.so.0()(64bit) for package: mutter-3.28.3-32.el7_9.x86_64
---> Package nautilus-extensions.x86_64 0:3.26.3.1-7.el7 will be installed
---> Package ncompress.x86_64 0:4.2.4.4-3.1.el7_8 will be installed
---> Package pango.x86_64 0:1.42.4-4.el7_7 will be installed
--> Processing Dependency: libthai(x86-64) >= 0.1.9 for package: pango-1.42.4-4.el7_7.x86_64
--> Processing Dependency: libXft(x86-64) >= 2.0.0 for package: pango-1.42.4-4.el7_7.x86_64
--> Processing Dependency: fribidi(x86-64) >= 1.0 for package: pango-1.42.4-4.el7_7.x86_64
--> Processing Dependency: libthai.so.0(LIBTHAI_0.1)(64bit) for package: pango-1.42.4-4.el7_7.x86_64
--> Processing Dependency: libthai.so.0()(64bit) for package: pango-1.42.4-4.el7_7.x86_64
--> Processing Dependency: libfribidi.so.0()(64bit) for package: pango-1.42.4-4.el7_7.x86_64
--> Processing Dependency: libXft.so.2()(64bit) for package: pango-1.42.4-4.el7_7.x86_64
---> Package pangomm.x86_64 0:2.40.1-1.el7 will be installed
---> Package pcre2.x86_64 0:10.23-2.el7 will be installed
---> Package pinentry-gtk.x86_64 0:0.8.1-17.el7 will be installed
---> Package pulseaudio-gdm-hooks.x86_64 0:10.0-6.el7_9 will be installed
---> Package pulseaudio-libs.x86_64 0:10.0-6.el7_9 will be installed
--> Processing Dependency: libasyncns.so.0()(64bit) for package: pulseaudio-libs-10.0-6.el7_9.x86_64
---> Package pulseaudio-libs-glib2.x86_64 0:10.0-6.el7_9 will be installed
---> Package pulseaudio-module-bluetooth.x86_64 0:10.0-6.el7_9 will be installed
--> Processing Dependency: pulseaudio(x86-64) = 10.0-6.el7_9 for package: pulseaudio-module-bluetooth-10.0-6.el7_9.x86_64
--> Processing Dependency: libsbc.so.1(SBC_1.0)(64bit) for package: pulseaudio-module-bluetooth-10.0-6.el7_9.x86_64
--> Processing Dependency: libsbc.so.1()(64bit) for package: pulseaudio-module-bluetooth-10.0-6.el7_9.x86_64
--> Processing Dependency: libpulsecore-10.0.so()(64bit) for package: pulseaudio-module-bluetooth-10.0-6.el7_9.x86_64
---> Package pygtk2.x86_64 0:2.24.0-9.el7 will be installed
--> Processing Dependency: pygobject2 for package: pygtk2-2.24.0-9.el7.x86_64
--> Processing Dependency: pycairo for package: pygtk2-2.24.0-9.el7.x86_64
---> Package pygtk2-libglade.x86_64 0:2.24.0-9.el7 will be installed
--> Processing Dependency: libglade-2.0.so.0()(64bit) for package: pygtk2-libglade-2.24.0-9.el7.x86_64
---> Package python-brlapi.x86_64 0:0.6.0-16.el7 will be installed
--> Processing Dependency: brlapi(x86-64) = 0.6.0-16.el7 for package: python-brlapi-0.6.0-16.el7.x86_64
--> Processing Dependency: libbrlapi.so.0.6()(64bit) for package: python-brlapi-0.6.0-16.el7.x86_64
---> Package python-ethtool.x86_64 0:0.8-8.el7 will be installed
--> Processing Dependency: libnl.so.1()(64bit) for package: python-ethtool-0.8-8.el7.x86_64
---> Package python-meh.noarch 0:0.25.3-1.el7 will be installed
--> Processing Dependency: libreport-cli >= 2.0.18-1 for package: python-meh-0.25.3-1.el7.noarch
---> Package python2-pyatspi.noarch 0:2.26.0-3.el7 will be installed
---> Package qt5-qtbase.x86_64 0:5.9.7-5.el7_9 will be installed
--> Processing Dependency: qt5-qtbase-common = 5.9.7-5.el7_9 for package: qt5-qtbase-5.9.7-5.el7_9.x86_64
--> Processing Dependency: libpcre2-16.so.0()(64bit) for package: qt5-qtbase-5.9.7-5.el7_9.x86_64
---> Package qt5-qtbase-gui.x86_64 0:5.9.7-5.el7_9 will be installed
--> Processing Dependency: libxcb-render-util.so.0()(64bit) for package: qt5-qtbase-gui-5.9.7-5.el7_9.x86_64
--> Processing Dependency: libxcb-keysyms.so.1()(64bit) for package: qt5-qtbase-gui-5.9.7-5.el7_9.x86_64
--> Processing Dependency: libxcb-image.so.0()(64bit) for package: qt5-qtbase-gui-5.9.7-5.el7_9.x86_64
--> Processing Dependency: libxcb-icccm.so.4()(64bit) for package: qt5-qtbase-gui-5.9.7-5.el7_9.x86_64
---> Package rest.x86_64 0:0.8.1-2.el7 will be installed
---> Package sane-backends.x86_64 0:1.0.24-12.el7 will be installed
---> Package sane-backends-libs.x86_64 0:1.0.24-12.el7 will be installed
---> Package setroubleshoot-server.x86_64 0:3.2.30-8.el7 will be installed
--> Processing Dependency: setroubleshoot-plugins >= 3.0.62 for package: setroubleshoot-server-3.2.30-8.el7.x86_64
--> Processing Dependency: audit-libs-python >= 1.2.6-3 for package: setroubleshoot-server-3.2.30-8.el7.x86_64
--> Processing Dependency: policycoreutils-python for package: setroubleshoot-server-3.2.30-8.el7.x86_64
---> Package speech-dispatcher.x86_64 0:0.7.1-15.el7 will be installed
--> Processing Dependency: libao.so.4(LIBAO4_1.1.0)(64bit) for package: speech-dispatcher-0.7.1-15.el7.x86_64
--> Processing Dependency: festival-freebsoft-utils for package: speech-dispatcher-0.7.1-15.el7.x86_64
--> Processing Dependency: libflite_usenglish.so.1()(64bit) for package: speech-dispatcher-0.7.1-15.el7.x86_64
--> Processing Dependency: libflite_cmulex.so.1()(64bit) for package: speech-dispatcher-0.7.1-15.el7.x86_64
--> Processing Dependency: libflite_cmu_us_kal16.so.1()(64bit) for package: speech-dispatcher-0.7.1-15.el7.x86_64
--> Processing Dependency: libflite.so.1()(64bit) for package: speech-dispatcher-0.7.1-15.el7.x86_64
--> Processing Dependency: libespeak.so.1()(64bit) for package: speech-dispatcher-0.7.1-15.el7.x86_64
--> Processing Dependency: libdotconf.so.0()(64bit) for package: speech-dispatcher-0.7.1-15.el7.x86_64
--> Processing Dependency: libao.so.4()(64bit) for package: speech-dispatcher-0.7.1-15.el7.x86_64
---> Package speech-dispatcher-python.x86_64 0:0.7.1-15.el7 will be installed
---> Package spice-glib.x86_64 0:0.35-5.el7_9.1 will be installed
--> Processing Dependency: usbredir >= 0.6-8 for package: spice-glib-0.35-5.el7_9.1.x86_64
--> Processing Dependency: libusbredirparser.so.1()(64bit) for package: spice-glib-0.35-5.el7_9.1.x86_64
--> Processing Dependency: libusbredirhost.so.1()(64bit) for package: spice-glib-0.35-5.el7_9.1.x86_64
--> Processing Dependency: libcelt051.so.0()(64bit) for package: spice-glib-0.35-5.el7_9.1.x86_64
--> Processing Dependency: libcacard.so.0()(64bit) for package: spice-glib-0.35-5.el7_9.1.x86_64
---> Package spice-gtk3.x86_64 0:0.35-5.el7_9.1 will be installed
---> Package startup-notification.x86_64 0:0.12-8.el7 will be installed
--> Processing Dependency: libxcb-util.so.1()(64bit) for package: startup-notification-0.12-8.el7.x86_64
---> Package telepathy-farstream.x86_64 0:0.6.0-5.el7 will be installed
---> Package telepathy-filesystem.noarch 0:0.0.2-6.el7 will be installed
---> Package telepathy-gabble.x86_64 0:0.18.1-4.el7 will be installed
---> Package telepathy-glib.x86_64 0:0.24.1-1.el7 will be installed
---> Package telepathy-haze.x86_64 0:0.8.0-1.el7 will be installed
--> Processing Dependency: libpurple.so.0()(64bit) for package: telepathy-haze-0.8.0-1.el7.x86_64
---> Package telepathy-logger.x86_64 0:0.8.0-5.el7 will be installed
---> Package telepathy-mission-control.x86_64 1:5.16.3-3.el7 will be installed
---> Package telepathy-salut.x86_64 0:0.8.1-6.el7 will be installed
---> Package totem-pl-parser.x86_64 0:3.26.1-1.el7 will be installed
---> Package tracker.x86_64 0:1.10.5-8.el7 will be installed
--> Processing Dependency: libiptcdata.so.0()(64bit) for package: tracker-1.10.5-8.el7.x86_64
--> Processing Dependency: libgsf-1.so.114()(64bit) for package: tracker-1.10.5-8.el7.x86_64
---> Package udisks2.x86_64 0:2.8.4-1.el7 will be installed
--> Processing Dependency: libblockdev-swap >= 2.13 for package: udisks2-2.8.4-1.el7.x86_64
--> Processing Dependency: libblockdev-part >= 2.13 for package: udisks2-2.8.4-1.el7.x86_64
--> Processing Dependency: libblockdev-mdraid >= 2.13 for package: udisks2-2.8.4-1.el7.x86_64
--> Processing Dependency: libblockdev-loop >= 2.13 for package: udisks2-2.8.4-1.el7.x86_64
--> Processing Dependency: libblockdev-fs >= 2.13 for package: udisks2-2.8.4-1.el7.x86_64
--> Processing Dependency: libblockdev-crypto >= 2.13 for package: udisks2-2.8.4-1.el7.x86_64
--> Processing Dependency: libblockdev >= 2.13 for package: udisks2-2.8.4-1.el7.x86_64
--> Processing Dependency: libatasmart >= 0.17 for package: udisks2-2.8.4-1.el7.x86_64
--> Processing Dependency: gdisk for package: udisks2-2.8.4-1.el7.x86_64
--> Processing Dependency: libblockdev.so.2()(64bit) for package: udisks2-2.8.4-1.el7.x86_64
--> Processing Dependency: libbd_utils.so.2()(64bit) for package: udisks2-2.8.4-1.el7.x86_64
--> Processing Dependency: libatasmart.so.4()(64bit) for package: udisks2-2.8.4-1.el7.x86_64
---> Package upower.x86_64 0:0.99.7-1.el7 will be installed
---> Package usbmuxd.x86_64 0:1.1.0-1.el7 will be installed
---> Package vte291.x86_64 0:0.52.4-1.el7 will be installed
--> Processing Dependency: vte-profile for package: vte291-0.52.4-1.el7.x86_64
---> Package webkitgtk3.x86_64 0:2.4.11-2.el7 will be installed
--> Processing Dependency: libwebp.so.4()(64bit) for package: webkitgtk3-2.4.11-2.el7.x86_64
--> Processing Dependency: libharfbuzz-icu.so.0()(64bit) for package: webkitgtk3-2.4.11-2.el7.x86_64
---> Package webkitgtk4.x86_64 0:2.28.2-3.el7 will be installed
--> Processing Dependency: libhyphen.so.0()(64bit) for package: webkitgtk4-2.28.2-3.el7.x86_64
---> Package webkitgtk4-jsc.x86_64 0:2.28.2-3.el7 will be installed
---> Package xdg-desktop-portal.x86_64 0:1.0.2-1.el7 will be installed
---> Package xdg-user-dirs.x86_64 0:0.15-5.el7 will be installed
---> Package xdg-utils.noarch 0:1.1.0-0.17.20120809git.el7 will be installed
---> Package yelp-libs.x86_64 2:3.28.1-1.el7 will be installed
---> Package yelp-xsl.noarch 0:3.28.0-1.el7 will be installed
---> Package zenity.x86_64 0:3.28.1-2.el7_9 will be installed
--> Running transaction check
---> Package PackageKit-yum.x86_64 0:1.1.10-2.el7.centos will be installed
---> Package abrt-dbus.x86_64 0:2.1.11-60.el7.centos will be installed
---> Package abrt-gui-libs.x86_64 0:2.1.11-60.el7.centos will be installed
---> Package abrt-libs.x86_64 0:2.1.11-60.el7.centos will be installed
---> Package abrt-python.x86_64 0:2.1.11-60.el7.centos will be installed
---> Package abrt-retrace-client.x86_64 0:2.1.11-60.el7.centos will be installed
---> Package adwaita-cursor-theme.noarch 0:3.28.0-1.el7 will be installed
---> Package anaconda-core.x86_64 0:21.48.22.159-1.el7.centos will be installed
--> Processing Dependency: python-blivet >= 1:0.61.15.71 for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: pyparted >= 2.5-2 for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: pykickstart >= 1.99.66.20-1 for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: libreport-rhel-anaconda-bugzilla >= 2.1.11-1 for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: libreport-anaconda >= 2.0.21-1 for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: langtable-python >= 0.0.31-3 for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: langtable-data >= 0.0.31-3 for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: isomd5sum >= 1.0.10 for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: iscsi-initiator-utils >= 6.2.0.870-3 for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: fcoe-utils >= 1.0.12-3.20100323git for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: usermode for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: rsync for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: realmd for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: pytz for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: python-subprocess32 for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: python-pwquality for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: python-ntplib for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: python-nss for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: python-coverage for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: python-IPy for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: libuser-python for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: libblockdev-nvdimm for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
--> Processing Dependency: createrepo for package: anaconda-core-21.48.22.159-1.el7.centos.x86_64
---> Package anaconda-tui.x86_64 0:21.48.22.159-1.el7.centos will be installed
---> Package anaconda-widgets.x86_64 0:21.48.22.159-1.el7.centos will be installed
--> Processing Dependency: libgladeui-2.so.6()(64bit) for package: anaconda-widgets-21.48.22.159-1.el7.centos.x86_64
---> Package audit-libs-python.x86_64 0:2.8.5-4.el7 will be installed
---> Package augeas-libs.x86_64 0:1.4.0-10.el7 will be installed
---> Package brasero.x86_64 0:3.12.2-5.el7_9.1 will be installed
--> Processing Dependency: libisofs.so.6(LIBISOFS6)(64bit) for package: brasero-3.12.2-5.el7_9.1.x86_64
--> Processing Dependency: libburn.so.4(LIBBURN4)(64bit) for package: brasero-3.12.2-5.el7_9.1.x86_64
--> Processing Dependency: dvd+rw-tools for package: brasero-3.12.2-5.el7_9.1.x86_64
--> Processing Dependency: cdrecord for package: brasero-3.12.2-5.el7_9.1.x86_64
--> Processing Dependency: cdrdao for package: brasero-3.12.2-5.el7_9.1.x86_64
--> Processing Dependency: cdda2wav for package: brasero-3.12.2-5.el7_9.1.x86_64
--> Processing Dependency: libisofs.so.6()(64bit) for package: brasero-3.12.2-5.el7_9.1.x86_64
--> Processing Dependency: libburn.so.4()(64bit) for package: brasero-3.12.2-5.el7_9.1.x86_64
---> Package brasero-libs.x86_64 0:3.12.2-5.el7_9.1 will be installed
---> Package brlapi.x86_64 0:0.6.0-16.el7 will be installed
--> Processing Dependency: brltty = 4.5-16.el7 for package: brlapi-0.6.0-16.el7.x86_64
---> Package cdparanoia-libs.x86_64 0:10.2-17.el7 will be installed
---> Package celt051.x86_64 0:0.5.1.3-8.el7 will be installed
---> Package color-filesystem.noarch 0:1-13.el7 will be installed
---> Package compat-libcolord1.x86_64 0:1.0.4-1.el7 will be installed
---> Package dejavu-sans-fonts.noarch 0:2.33-6.el7 will be installed
--> Processing Dependency: dejavu-fonts-common = 2.33-6.el7 for package: dejavu-sans-fonts-2.33-6.el7.noarch
---> Package dleyna-server.x86_64 0:0.5.0-3.el7 will be installed
--> Processing Dependency: dleyna-connector-dbus(x86-64) for package: dleyna-server-0.5.0-3.el7.x86_64
--> Processing Dependency: libgupnp-dlna-2.0.so.3()(64bit) for package: dleyna-server-0.5.0-3.el7.x86_64
--> Processing Dependency: libgupnp-av-1.0.so.2()(64bit) for package: dleyna-server-0.5.0-3.el7.x86_64
--> Processing Dependency: libgssdp-1.0.so.3()(64bit) for package: dleyna-server-0.5.0-3.el7.x86_64
--> Processing Dependency: libdleyna-core-1.0.so.4()(64bit) for package: dleyna-server-0.5.0-3.el7.x86_64
---> Package dotconf.x86_64 0:1.3-8.el7 will be installed
---> Package emacs-filesystem.noarch 1:24.3-23.el7_9.1 will be installed
---> Package espeak.x86_64 0:1.47.11-4.el7 will be installed
---> Package evolution-data-server-langpacks.noarch 0:3.28.5-5.el7_9.1 will be installed
---> Package festival-freebsoft-utils.noarch 0:0.10-7.el7 will be installed
--> Processing Dependency: sox for package: festival-freebsoft-utils-0.10-7.el7.noarch
--> Processing Dependency: festival for package: festival-freebsoft-utils-0.10-7.el7.noarch
---> Package flac-libs.x86_64 0:1.3.0-5.el7_1 will be installed
---> Package flite.x86_64 0:1.3-22.el7 will be installed
---> Package fontpackages-filesystem.noarch 0:1.44-8.el7 will be installed
---> Package frei0r-plugins.x86_64 0:1.3-13.el7 will be installed
--> Processing Dependency: libgavl.so.1()(64bit) for package: frei0r-plugins-1.3-13.el7.x86_64
---> Package fribidi.x86_64 0:1.0.2-1.el7_7.1 will be installed
---> Package fros.noarch 0:1.0-5.el7 will be installed
---> Package fwupdate-libs.x86_64 0:12-6.el7.centos will be installed
--> Processing Dependency: fwupdate-efi = 12-6.el7.centos for package: fwupdate-libs-12-6.el7.centos.x86_64
---> Package gd.x86_64 0:2.0.35-27.el7_9 will be installed
--> Processing Dependency: libXpm.so.4()(64bit) for package: gd-2.0.35-27.el7_9.x86_64
---> Package gdisk.x86_64 0:0.8.10-3.el7 will be installed
---> Package gnome-keyring.x86_64 0:3.28.2-1.el7 will be installed
updates/7/x86_64/filelists_db                                                                    |  12 MB  00:00:01     
---> Package gnome-shell-extension-common.noarch 0:3.28.1-17.el7_9 will be installed
---> Package gom.x86_64 0:0.4-1.el7 will be installed
---> Package graphite2.x86_64 0:1.3.10-1.el7_3 will be installed
---> Package gsm.x86_64 0:1.0.13-11.el7 will be installed
---> Package gupnp.x86_64 0:1.0.2-6.el7_9 will be installed
---> Package gupnp-igd.x86_64 0:0.2.5-2.el7 will be installed
---> Package harfbuzz-icu.x86_64 0:1.7.5-2.el7 will be installed
---> Package hplip-common.x86_64 0:3.15.9-5.el7 will be installed
---> Package hunspell.x86_64 0:1.3.2-16.el7 will be installed
--> Processing Dependency: hunspell-en-US for package: hunspell-1.3.2-16.el7.x86_64
---> Package hyphen.x86_64 0:2.8.6-5.el7 will be installed
---> Package ibus-gtk2.x86_64 0:1.5.17-12.el7_9 will be installed
---> Package ibus-gtk3.x86_64 0:1.5.17-12.el7_9 will be installed
---> Package ibus-setup.noarch 0:1.5.17-12.el7_9 will be installed
---> Package jasper-libs.x86_64 0:1.900.1-33.el7 will be installed
---> Package keybinder3.x86_64 0:0.3.0-1.el7 will be installed
---> Package libXft.x86_64 0:2.3.2-2.el7 will be installed
---> Package libXres.x86_64 0:1.2.0-1.el7 will be installed
---> Package libXv.x86_64 0:1.0.11-1.el7 will be installed
---> Package libao.x86_64 0:1.1.0-8.el7 will be installed
---> Package libasyncns.x86_64 0:0.8-7.el7 will be installed
---> Package libatasmart.x86_64 0:0.19-6.el7 will be installed
---> Package libavc1394.x86_64 0:0.5.3-14.el7 will be installed
---> Package libblockdev.x86_64 0:2.18-5.el7 will be installed
---> Package libblockdev-crypto.x86_64 0:2.18-5.el7 will be installed
--> Processing Dependency: libvolume_key.so.1()(64bit) for package: libblockdev-crypto-2.18-5.el7.x86_64
---> Package libblockdev-fs.x86_64 0:2.18-5.el7 will be installed
--> Processing Dependency: device-mapper-multipath for package: libblockdev-fs-2.18-5.el7.x86_64
---> Package libblockdev-loop.x86_64 0:2.18-5.el7 will be installed
---> Package libblockdev-mdraid.x86_64 0:2.18-5.el7 will be installed
--> Processing Dependency: mdadm for package: libblockdev-mdraid-2.18-5.el7.x86_64
--> Processing Dependency: libbytesize.so.1()(64bit) for package: libblockdev-mdraid-2.18-5.el7.x86_64
---> Package libblockdev-part.x86_64 0:2.18-5.el7 will be installed
---> Package libblockdev-swap.x86_64 0:2.18-5.el7 will be installed
---> Package libblockdev-utils.x86_64 0:2.18-5.el7 will be installed
---> Package libbluray.x86_64 0:0.2.3-6.el7 will be installed
---> Package libcacard.x86_64 40:2.7.0-1.el7 will be installed
---> Package libcdio.x86_64 0:0.92-3.el7 will be installed
---> Package libcdio-paranoia.x86_64 0:10.2+0.90-11.el7 will be installed
---> Package libdmapsharing.x86_64 0:2.9.37-1.el7 will be installed
---> Package libdv.x86_64 0:1.0.0-17.el7 will be installed
---> Package libdvdnav.x86_64 0:5.0.3-1.el7 will be installed
---> Package libfprint.x86_64 0:0.8.2-1.el7 will be installed
---> Package libgcab1.x86_64 0:0.7-4.el7_4 will be installed
---> Package libglade2.x86_64 0:2.6.4-11.el7 will be installed
---> Package libgsf.x86_64 0:1.14.26-7.el7 will be installed
---> Package libgusb.x86_64 0:0.2.9-1.el7 will be installed
---> Package libgxps.x86_64 0:0.3.0-4.el7 will be installed
---> Package libicu.x86_64 0:50.2-4.el7_7 will be installed
---> Package libiec61883.x86_64 0:1.2.0-10.el7 will be installed
---> Package libinput.x86_64 0:1.10.7-2.el7 will be installed
--> Processing Dependency: libevdev.so.2(LIBEVDEV_1_3)(64bit) for package: libinput-1.10.7-2.el7.x86_64
--> Processing Dependency: libevdev.so.2(LIBEVDEV_1)(64bit) for package: libinput-1.10.7-2.el7.x86_64
--> Processing Dependency: libmtdev.so.1()(64bit) for package: libinput-1.10.7-2.el7.x86_64
--> Processing Dependency: libevdev.so.2()(64bit) for package: libinput-1.10.7-2.el7.x86_64
---> Package libiptcdata.x86_64 0:1.0.4-11.el7 will be installed
---> Package libldb.x86_64 0:1.5.4-2.el7 will be installed
---> Package liblouis.x86_64 0:2.5.2-12.el7_4 will be installed
---> Package libmediaart.x86_64 0:1.9.4-1.el7 will be installed
---> Package libmodman.x86_64 0:2.0.1-8.el7 will be installed
---> Package libmpcdec.x86_64 0:1.2.6-12.el7 will be installed
---> Package libnice.x86_64 0:0.1.3-4.el7 will be installed
--> Processing Dependency: libgstreamer-0.10.so.0()(64bit) for package: libnice-0.1.3-4.el7.x86_64
--> Processing Dependency: libgstbase-0.10.so.0()(64bit) for package: libnice-0.1.3-4.el7.x86_64
---> Package libnl.x86_64 0:1.1.4-3.el7 will be installed
---> Package liboauth.x86_64 0:0.9.7-4.el7 will be installed
---> Package libpurple.x86_64 0:2.10.11-9.el7 will be installed
--> Processing Dependency: cyrus-sasl-scram for package: libpurple-2.10.11-9.el7.x86_64
--> Processing Dependency: cyrus-sasl-plain for package: libpurple-2.10.11-9.el7.x86_64
--> Processing Dependency: cyrus-sasl-md5 for package: libpurple-2.10.11-9.el7.x86_64
--> Processing Dependency: libmeanwhile.so.1()(64bit) for package: libpurple-2.10.11-9.el7.x86_64
--> Processing Dependency: libgstinterfaces-0.10.so.0()(64bit) for package: libpurple-2.10.11-9.el7.x86_64
--> Processing Dependency: libfarstream-0.1.so.0()(64bit) for package: libpurple-2.10.11-9.el7.x86_64
---> Package libraw1394.x86_64 0:2.1.0-2.el7 will be installed
---> Package libreport.x86_64 0:2.1.11-53.el7.centos will be installed
--> Processing Dependency: libreport-filesystem = 2.1.11-53.el7.centos for package: libreport-2.1.11-53.el7.centos.x86_64
---> Package libreport-cli.x86_64 0:2.1.11-53.el7.centos will be installed
---> Package libreport-plugin-reportuploader.x86_64 0:2.1.11-53.el7.centos will be installed
---> Package libreport-plugin-rhtsupport.x86_64 0:2.1.11-53.el7.centos will be installed
---> Package libreport-plugin-ureport.x86_64 0:2.1.11-53.el7.centos will be installed
---> Package libreport-web.x86_64 0:2.1.11-53.el7.centos will be installed
---> Package libreswan.x86_64 0:3.25-9.1.el7_8 will be installed
--> Processing Dependency: unbound-libs >= 1.6.6 for package: libreswan-3.25-9.1.el7_8.x86_64
--> Processing Dependency: libunbound.so.2()(64bit) for package: libreswan-3.25-9.1.el7_8.x86_64
--> Processing Dependency: libldns.so.1()(64bit) for package: libreswan-3.25-9.1.el7_8.x86_64
---> Package libshout.x86_64 0:2.2.2-11.el7 will be installed
---> Package libsmbios.x86_64 0:2.3.3-8.el7 will be installed
---> Package libsndfile.x86_64 0:1.0.25-12.el7_9.1 will be installed
---> Package libspectre.x86_64 0:0.2.8-1.el7 will be installed
--> Processing Dependency: libgs.so.9()(64bit) for package: libspectre-0.2.8-1.el7.x86_64
---> Package libsrtp.x86_64 0:1.4.4-11.20101004cvs.el7 will be installed
---> Package libtalloc.x86_64 0:2.1.16-1.el7 will be installed
---> Package libtar.x86_64 0:1.2.11-29.el7 will be installed
---> Package libtevent.x86_64 0:0.9.39-1.el7 will be installed
---> Package libthai.x86_64 0:0.1.14-9.el7 will be installed
---> Package libtheora.x86_64 1:1.1.1-8.el7 will be installed
---> Package libtimezonemap.x86_64 0:0.4.4-2.el7_9 will be installed
---> Package libusal.x86_64 0:1.1.11-25.el7 will be installed
---> Package libusbmuxd.x86_64 0:1.0.10-5.el7 will be installed
---> Package libvirt-daemon.x86_64 0:4.5.0-36.el7_9.5 will be installed
--> Processing Dependency: numad for package: libvirt-daemon-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: libcgroup for package: libvirt-daemon-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: libyajl.so.2()(64bit) for package: libvirt-daemon-4.5.0-36.el7_9.5.x86_64
---> Package libvirt-daemon-driver-interface.x86_64 0:4.5.0-36.el7_9.5 will be installed
--> Processing Dependency: netcf-libs >= 0.2.2 for package: libvirt-daemon-driver-interface-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: libnetcf.so.1(NETCF_1.4.0)(64bit) for package: libvirt-daemon-driver-interface-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: libnetcf.so.1(NETCF_1.3.0)(64bit) for package: libvirt-daemon-driver-interface-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: libnetcf.so.1(NETCF_1.2.0)(64bit) for package: libvirt-daemon-driver-interface-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: libnetcf.so.1(NETCF_1.0.0)(64bit) for package: libvirt-daemon-driver-interface-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: libnetcf.so.1()(64bit) for package: libvirt-daemon-driver-interface-4.5.0-36.el7_9.5.x86_64
---> Package libvirt-daemon-driver-network.x86_64 0:4.5.0-36.el7_9.5 will be installed
--> Processing Dependency: dnsmasq >= 2.41 for package: libvirt-daemon-driver-network-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: radvd for package: libvirt-daemon-driver-network-4.5.0-36.el7_9.5.x86_64
---> Package libvirt-daemon-driver-nodedev.x86_64 0:4.5.0-36.el7_9.5 will be installed
---> Package libvirt-daemon-driver-nwfilter.x86_64 0:4.5.0-36.el7_9.5 will be installed
--> Processing Dependency: libpcap.so.1()(64bit) for package: libvirt-daemon-driver-nwfilter-4.5.0-36.el7_9.5.x86_64
---> Package libvirt-daemon-driver-qemu.x86_64 0:4.5.0-36.el7_9.5 will be installed
--> Processing Dependency: libvirt-daemon-driver-storage-core = 4.5.0-36.el7_9.5 for package: libvirt-daemon-driver-qemu-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: /usr/bin/qemu-img for package: libvirt-daemon-driver-qemu-4.5.0-36.el7_9.5.x86_64
---> Package libvirt-daemon-driver-secret.x86_64 0:4.5.0-36.el7_9.5 will be installed
---> Package libvirt-daemon-driver-storage.x86_64 0:4.5.0-36.el7_9.5 will be installed
--> Processing Dependency: libvirt-daemon-driver-storage-scsi = 4.5.0-36.el7_9.5 for package: libvirt-daemon-driver-storage-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: libvirt-daemon-driver-storage-rbd = 4.5.0-36.el7_9.5 for package: libvirt-daemon-driver-storage-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: libvirt-daemon-driver-storage-mpath = 4.5.0-36.el7_9.5 for package: libvirt-daemon-driver-storage-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: libvirt-daemon-driver-storage-logical = 4.5.0-36.el7_9.5 for package: libvirt-daemon-driver-storage-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: libvirt-daemon-driver-storage-iscsi = 4.5.0-36.el7_9.5 for package: libvirt-daemon-driver-storage-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: libvirt-daemon-driver-storage-gluster = 4.5.0-36.el7_9.5 for package: libvirt-daemon-driver-storage-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: libvirt-daemon-driver-storage-disk = 4.5.0-36.el7_9.5 for package: libvirt-daemon-driver-storage-4.5.0-36.el7_9.5.x86_64
---> Package libvirt-glib.x86_64 0:1.0.0-1.el7 will be installed
---> Package libvirt-libs.x86_64 0:4.5.0-36.el7_9.5 will be installed
--> Processing Dependency: nc for package: libvirt-libs-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: cyrus-sasl-gssapi for package: libvirt-libs-4.5.0-36.el7_9.5.x86_64
--> Processing Dependency: cyrus-sasl for package: libvirt-libs-4.5.0-36.el7_9.5.x86_64
---> Package libvisual.x86_64 0:0.4.0-16.el7 will be installed
---> Package libvpx.x86_64 0:1.3.0-8.el7 will be installed
---> Package libwacom-data.noarch 0:0.30-1.el7 will be installed
---> Package libwbclient.x86_64 0:4.10.16-24.el7_9 will be installed
---> Package libwebp.x86_64 0:0.3.0-11.el7 will be installed
---> Package libwinpr.x86_64 0:2.1.1-5.el7_9 will be installed
---> Package libxkbcommon-x11.x86_64 0:0.7.1-3.el7 will be installed
---> Package libxklavier.x86_64 0:5.4-7.el7 will be installed
---> Package lockdev.x86_64 0:1.0.4-0.13.20111007git.el7 will be installed
---> Package mesa-libEGL.x86_64 0:18.3.4-12.el7_9 will be installed
---> Package mobile-broadband-provider-info.noarch 0:1.20170310-1.el7 will be installed
---> Package mozjs52.x86_64 0:52.9.0-1.el7 will be installed
---> Package mpg123-libs.x86_64 0:1.25.6-1.el7 will be installed
---> Package neon.x86_64 0:0.30.0-4.el7 will be installed
--> Processing Dependency: libpakchois.so.0()(64bit) for package: neon-0.30.0-4.el7.x86_64
---> Package net-snmp-libs.x86_64 1:5.7.2-49.el7_9.2 will be installed
---> Package opus.x86_64 0:1.0.2-6.el7 will be installed
---> Package orc.x86_64 0:0.4.26-1.el7 will be installed
---> Package osinfo-db.noarch 0:20200529-1.el7 will be installed
---> Package osinfo-db-tools.x86_64 0:1.1.0-1.el7 will be installed
---> Package pcre2-utf16.x86_64 0:10.23-2.el7 will be installed
---> Package policycoreutils-python.x86_64 0:2.5-34.el7 will be installed
--> Processing Dependency: setools-libs >= 3.3.8-4 for package: policycoreutils-python-2.5-34.el7.x86_64
--> Processing Dependency: libsemanage-python >= 2.5-14 for package: policycoreutils-python-2.5-34.el7.x86_64
--> Processing Dependency: libqpol.so.1(VERS_1.4)(64bit) for package: policycoreutils-python-2.5-34.el7.x86_64
--> Processing Dependency: libqpol.so.1(VERS_1.2)(64bit) for package: policycoreutils-python-2.5-34.el7.x86_64
--> Processing Dependency: libapol.so.4(VERS_4.0)(64bit) for package: policycoreutils-python-2.5-34.el7.x86_64
--> Processing Dependency: checkpolicy for package: policycoreutils-python-2.5-34.el7.x86_64
--> Processing Dependency: libqpol.so.1()(64bit) for package: policycoreutils-python-2.5-34.el7.x86_64
--> Processing Dependency: libapol.so.4()(64bit) for package: policycoreutils-python-2.5-34.el7.x86_64
---> Package poppler-glib.x86_64 0:0.26.5-43.el7.1 will be installed
--> Processing Dependency: poppler(x86-64) = 0.26.5-43.el7.1 for package: poppler-glib-0.26.5-43.el7.1.x86_64
--> Processing Dependency: libpoppler.so.46()(64bit) for package: poppler-glib-0.26.5-43.el7.1.x86_64
--> Processing Dependency: libopenjpeg.so.1()(64bit) for package: poppler-glib-0.26.5-43.el7.1.x86_64
---> Package pulseaudio.x86_64 0:10.0-6.el7_9 will be installed
--> Processing Dependency: rtkit for package: pulseaudio-10.0-6.el7_9.x86_64
--> Processing Dependency: libwebrtc_audio_processing.so.1()(64bit) for package: pulseaudio-10.0-6.el7_9.x86_64
---> Package pycairo.x86_64 0:1.8.10-8.el7 will be installed
---> Package pygobject2.x86_64 0:2.28.6-11.el7 will be installed
---> Package python-augeas.noarch 0:0.5.0-2.el7 will be installed
---> Package python-di.noarch 0:0.3-2.el7 will be installed
---> Package python-gobject.x86_64 0:3.22.0-1.el7_4.1 will be installed
---> Package python-inotify.noarch 0:0.9.4-4.el7 will be installed
---> Package python-meh-gui.noarch 0:0.25.3-1.el7 will be installed
---> Package qemu-kvm.x86_64 10:1.5.3-175.el7_9.6 will be installed
--> Processing Dependency: qemu-kvm-common = 10:1.5.3-175.el7_9.6 for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: seabios-bin >= 1.7.2.2-5 for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: glusterfs-api >= 3.6.0 for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: sgabios-bin for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: seavgabios-bin for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libspice-server.so.1(SPICE_SERVER_0.8.3)(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libspice-server.so.1(SPICE_SERVER_0.8.2)(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libspice-server.so.1(SPICE_SERVER_0.8.1)(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libspice-server.so.1(SPICE_SERVER_0.6.0)(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libspice-server.so.1(SPICE_SERVER_0.12.6)(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libspice-server.so.1(SPICE_SERVER_0.12.3)(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libspice-server.so.1(SPICE_SERVER_0.11.2)(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libspice-server.so.1(SPICE_SERVER_0.10.4)(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libspice-server.so.1(SPICE_SERVER_0.10.3)(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libspice-server.so.1(SPICE_SERVER_0.10.2)(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libspice-server.so.1(SPICE_SERVER_0.10.1)(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libspice-server.so.1(SPICE_SERVER_0.10.0)(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: librdmacm.so.1(RDMACM_1.0)(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libibverbs.so.1(IBVERBS_1.1)(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libibverbs.so.1(IBVERBS_1.0)(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libgfapi.so.0(GFAPI_6.0)(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libgfapi.so.0(GFAPI_3.4.0)(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: ipxe-roms-qemu for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libtcmalloc.so.4()(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libspice-server.so.1()(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: librdmacm.so.1()(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: librbd.so.1()(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: librados.so.2()(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libiscsi.so.2()(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libibverbs.so.1()(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libgfxdr.so.0()(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libgfrpc.so.0()(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
--> Processing Dependency: libgfapi.so.0()(64bit) for package: 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64
---> Package qt5-qtbase-common.noarch 0:5.9.7-5.el7_9 will be installed
---> Package redhat-menus.noarch 0:12.0.2-8.el7 will be installed
---> Package samba-client-libs.x86_64 0:4.10.16-24.el7_9 will be installed
---> Package samba-common.noarch 0:4.10.16-24.el7_9 will be installed
---> Package samba-common-libs.x86_64 0:4.10.16-24.el7_9 will be installed
---> Package satyr.x86_64 0:0.13-15.el7 will be installed
---> Package sbc.x86_64 0:1.0-5.el7 will be installed
---> Package setroubleshoot-plugins.noarch 0:3.0.67-4.el7 will be installed
---> Package sos.noarch 0:3.9-5.el7.centos.11 will be installed
--> Processing Dependency: python2-futures for package: sos-3.9-5.el7.centos.11.noarch
--> Processing Dependency: python-six for package: sos-3.9-5.el7.centos.11.noarch
---> Package sound-theme-freedesktop.noarch 0:0.8-3.el7 will be installed
---> Package soundtouch.x86_64 0:1.4.0-9.el7 will be installed
---> Package speex.x86_64 0:1.2-0.19.rc1.el7 will be installed
---> Package systemd-python.x86_64 0:219-78.el7_9.7 will be installed
---> Package taglib.x86_64 0:1.8-8.20130218git.el7 will be installed
---> Package usbredir.x86_64 0:0.7.1-3.el7 will be installed
---> Package vte-profile.x86_64 0:0.52.4-1.el7 will be installed
---> Package wavpack.x86_64 0:4.60.1-9.el7 will be installed
---> Package xcb-util.x86_64 0:0.4.0-2.el7 will be installed
---> Package xcb-util-image.x86_64 0:0.4.0-2.el7 will be installed
---> Package xcb-util-keysyms.x86_64 0:0.4.0-1.el7 will be installed
---> Package xcb-util-renderutil.x86_64 0:0.3.9-3.el7 will be installed
---> Package xcb-util-wm.x86_64 0:0.4.1-5.el7 will be installed
---> Package xml-common.noarch 0:0.6.3-39.el7 will be installed
---> Package xmlrpc-c.x86_64 0:1.32.5-1905.svn2451.el7 will be installed
---> Package xmlrpc-c-client.x86_64 0:1.32.5-1905.svn2451.el7 will be installed
--> Running transaction check
---> Package brltty.x86_64 0:4.5-16.el7 will be installed
---> Package cdrdao.x86_64 0:1.2.3-20.el7 will be installed
---> Package checkpolicy.x86_64 0:2.5-8.el7 will be installed
---> Package createrepo.noarch 0:0.9.9-28.el7 will be installed
--> Processing Dependency: python-deltarpm for package: createrepo-0.9.9-28.el7.noarch
--> Processing Dependency: deltarpm for package: createrepo-0.9.9-28.el7.noarch
---> Package cyrus-sasl.x86_64 0:2.1.26-24.el7_9 will be installed
---> Package cyrus-sasl-gssapi.x86_64 0:2.1.26-24.el7_9 will be installed
---> Package cyrus-sasl-md5.x86_64 0:2.1.26-24.el7_9 will be installed
---> Package cyrus-sasl-plain.x86_64 0:2.1.26-24.el7_9 will be installed
---> Package cyrus-sasl-scram.x86_64 0:2.1.26-24.el7_9 will be installed
---> Package dejavu-fonts-common.noarch 0:2.33-6.el7 will be installed
---> Package device-mapper-multipath.x86_64 0:0.4.9-136.el7_9 will be installed
--> Processing Dependency: device-mapper-multipath-libs = 0.4.9-136.el7_9 for package: device-mapper-multipath-0.4.9-136.el7_9.x86_64
--> Processing Dependency: libmultipath.so.0()(64bit) for package: device-mapper-multipath-0.4.9-136.el7_9.x86_64
--> Processing Dependency: libmpathpersist.so.0()(64bit) for package: device-mapper-multipath-0.4.9-136.el7_9.x86_64
--> Processing Dependency: libmpathcmd.so.0()(64bit) for package: device-mapper-multipath-0.4.9-136.el7_9.x86_64
---> Package dleyna-connector-dbus.x86_64 0:0.2.0-2.el7 will be installed
---> Package dleyna-core.x86_64 0:0.5.0-1.el7 will be installed
---> Package dnsmasq.x86_64 0:2.76-17.el7_9.3 will be installed
---> Package dvd+rw-tools.x86_64 0:7.1-15.el7 will be installed
---> Package farstream.x86_64 0:0.1.2-8.el7 will be installed
--> Processing Dependency: gstreamer-plugins-good >= 0.10.29 for package: farstream-0.1.2-8.el7.x86_64
--> Processing Dependency: gstreamer-plugins-bad-free >= 0.10.23 for package: farstream-0.1.2-8.el7.x86_64
---> Package fcoe-utils.x86_64 0:1.0.32-2.el7_6 will be installed
--> Processing Dependency: lldpad >= 0.9.43 for package: fcoe-utils-1.0.32-2.el7_6.x86_64
---> Package festival.x86_64 0:1.96-28.el7 will be installed
--> Processing Dependency: festival-speechtools-libs = 1.2.96-28.el7 for package: festival-1.96-28.el7.x86_64
--> Processing Dependency: festival-lib = 1.96-28.el7 for package: festival-1.96-28.el7.x86_64
--> Processing Dependency: festvox-slt-arctic-hts for package: festival-1.96-28.el7.x86_64
--> Processing Dependency: libeststring.so.1.2()(64bit) for package: festival-1.96-28.el7.x86_64
--> Processing Dependency: libestools.so.1.2.96.1()(64bit) for package: festival-1.96-28.el7.x86_64
--> Processing Dependency: libestbase.so.1.2.96.1()(64bit) for package: festival-1.96-28.el7.x86_64
--> Processing Dependency: libFestival.so.1.96.0()(64bit) for package: festival-1.96-28.el7.x86_64
---> Package fwupdate-efi.x86_64 0:12-6.el7.centos will be installed
---> Package gavl.x86_64 0:1.4.0-4.el7 will be installed
--> Processing Dependency: libgdither.so.1()(64bit) for package: gavl-1.4.0-4.el7.x86_64
---> Package glade-libs.x86_64 0:3.22.1-1.el7 will be installed
---> Package glusterfs-api.x86_64 0:6.0-61.el7 will be installed
--> Processing Dependency: glusterfs-client-xlators(x86-64) = 6.0-61.el7 for package: glusterfs-api-6.0-61.el7.x86_64
--> Processing Dependency: glusterfs(x86-64) = 6.0-61.el7 for package: glusterfs-api-6.0-61.el7.x86_64
---> Package glusterfs-libs.x86_64 0:6.0-61.el7 will be installed
---> Package gperftools-libs.x86_64 0:2.6.1-1.el7 will be installed
---> Package gssdp.x86_64 0:1.0.2-1.el7 will be installed
---> Package gstreamer.x86_64 0:0.10.36-7.el7 will be installed
--> Processing Dependency: gstreamer-tools >= 0.10.36 for package: gstreamer-0.10.36-7.el7.x86_64
---> Package gstreamer-plugins-base.x86_64 0:0.10.36-10.el7 will be installed
---> Package gupnp-av.x86_64 0:0.12.10-1.el7 will be installed
---> Package gupnp-dlna.x86_64 0:0.10.5-1.el7 will be installed
---> Package hunspell-en-US.noarch 0:0.20121024-6.el7 will be installed
---> Package icedax.x86_64 0:1.1.11-25.el7 will be installed
--> Processing Dependency: vorbis-tools for package: icedax-1.1.11-25.el7.x86_64
--> Processing Dependency: cdparanoia for package: icedax-1.1.11-25.el7.x86_64
---> Package ipxe-roms-qemu.noarch 0:20180825-3.git133f4c.el7 will be installed
---> Package iscsi-initiator-utils.x86_64 0:6.2.0.874-22.el7_9 will be installed
--> Processing Dependency: iscsi-initiator-utils-iscsiuio >= 6.2.0.874-22.el7_9 for package: iscsi-initiator-utils-6.2.0.874-22.el7_9.x86_64
---> Package isomd5sum.x86_64 1:1.0.10-5.el7 will be installed
---> Package langtable-data.noarch 0:0.0.31-4.el7 will be installed
--> Processing Dependency: langtable = 0.0.31-4.el7 for package: langtable-data-0.0.31-4.el7.noarch
---> Package langtable-python.noarch 0:0.0.31-4.el7 will be installed
---> Package ldns.x86_64 0:1.6.16-10.el7 will be installed
---> Package libXpm.x86_64 0:3.5.12-2.el7_9 will be installed
---> Package libblockdev-nvdimm.x86_64 0:2.18-5.el7 will be installed
--> Processing Dependency: ndctl for package: libblockdev-nvdimm-2.18-5.el7.x86_64
--> Processing Dependency: libndctl.so.6(LIBNDCTL_3)(64bit) for package: libblockdev-nvdimm-2.18-5.el7.x86_64
--> Processing Dependency: libndctl.so.6(LIBNDCTL_1)(64bit) for package: libblockdev-nvdimm-2.18-5.el7.x86_64
--> Processing Dependency: libndctl.so.6()(64bit) for package: libblockdev-nvdimm-2.18-5.el7.x86_64
---> Package libburn.x86_64 0:1.2.8-4.el7 will be installed
---> Package libbytesize.x86_64 0:1.2-1.el7 will be installed
---> Package libcgroup.x86_64 0:0.41-21.el7 will be installed
---> Package libevdev.x86_64 0:1.5.6-1.el7 will be installed
---> Package libgs.x86_64 0:9.25-5.el7 will be installed
--> Processing Dependency: urw-base35-fonts for package: libgs-9.25-5.el7.x86_64
--> Processing Dependency: adobe-mappings-pdf for package: libgs-9.25-5.el7.x86_64
--> Processing Dependency: adobe-mappings-cmap-deprecated for package: libgs-9.25-5.el7.x86_64
--> Processing Dependency: adobe-mappings-cmap for package: libgs-9.25-5.el7.x86_64
--> Processing Dependency: libpaper.so.1()(64bit) for package: libgs-9.25-5.el7.x86_64
--> Processing Dependency: libopenjp2.so.7()(64bit) for package: libgs-9.25-5.el7.x86_64
---> Package libibverbs.x86_64 0:22.4-6.el7_9 will be installed
--> Processing Dependency: rdma-core(x86-64) = 22.4-6.el7_9 for package: libibverbs-22.4-6.el7_9.x86_64
---> Package libiscsi.x86_64 0:1.9.0-7.el7 will be installed
---> Package libisofs.x86_64 0:1.2.8-4.el7 will be installed
---> Package libpcap.x86_64 14:1.5.3-13.el7_9 will be installed
---> Package librados2.x86_64 1:10.2.5-4.el7 will be installed
--> Processing Dependency: libboost_thread-mt.so.1.53.0()(64bit) for package: 1:librados2-10.2.5-4.el7.x86_64
--> Processing Dependency: libboost_system-mt.so.1.53.0()(64bit) for package: 1:librados2-10.2.5-4.el7.x86_64
--> Processing Dependency: libboost_random-mt.so.1.53.0()(64bit) for package: 1:librados2-10.2.5-4.el7.x86_64
--> Processing Dependency: libboost_iostreams-mt.so.1.53.0()(64bit) for package: 1:librados2-10.2.5-4.el7.x86_64
---> Package librbd1.x86_64 1:10.2.5-4.el7 will be installed
---> Package librdmacm.x86_64 0:22.4-6.el7_9 will be installed
---> Package libreport-anaconda.x86_64 0:2.1.11-53.el7.centos will be installed
--> Processing Dependency: libreport-plugin-bugzilla = 2.1.11-53.el7.centos for package: libreport-anaconda-2.1.11-53.el7.centos.x86_64
---> Package libreport-filesystem.x86_64 0:2.1.11-53.el7.centos will be installed
---> Package libreport-rhel-anaconda-bugzilla.x86_64 0:2.1.11-53.el7.centos will be installed
---> Package libsemanage-python.x86_64 0:2.5-14.el7 will be installed
---> Package libuser-python.x86_64 0:0.60-9.el7 will be installed
---> Package libvirt-daemon-driver-storage-core.x86_64 0:4.5.0-36.el7_9.5 will be installed
---> Package libvirt-daemon-driver-storage-disk.x86_64 0:4.5.0-36.el7_9.5 will be installed
---> Package libvirt-daemon-driver-storage-gluster.x86_64 0:4.5.0-36.el7_9.5 will be installed
--> Processing Dependency: /usr/sbin/gluster for package: libvirt-daemon-driver-storage-gluster-4.5.0-36.el7_9.5.x86_64
---> Package libvirt-daemon-driver-storage-iscsi.x86_64 0:4.5.0-36.el7_9.5 will be installed
---> Package libvirt-daemon-driver-storage-logical.x86_64 0:4.5.0-36.el7_9.5 will be installed
---> Package libvirt-daemon-driver-storage-mpath.x86_64 0:4.5.0-36.el7_9.5 will be installed
---> Package libvirt-daemon-driver-storage-rbd.x86_64 0:4.5.0-36.el7_9.5 will be installed
---> Package libvirt-daemon-driver-storage-scsi.x86_64 0:4.5.0-36.el7_9.5 will be installed
---> Package mdadm.x86_64 0:4.1-9.el7_9 will be installed
---> Package meanwhile.x86_64 0:1.1.0-12.el7 will be installed
---> Package mtdev.x86_64 0:1.1.5-5.el7 will be installed
---> Package netcf-libs.x86_64 0:0.2.8-4.el7 will be installed
--> Processing Dependency: bridge-utils for package: netcf-libs-0.2.8-4.el7.x86_64
---> Package nmap-ncat.x86_64 2:6.40-19.el7 will be installed
---> Package numad.x86_64 0:0.5-18.20150602git.el7 will be installed
---> Package openjpeg-libs.x86_64 0:1.5.1-18.el7 will be installed
---> Package pakchois.x86_64 0:0.4-10.el7 will be installed
---> Package poppler.x86_64 0:0.26.5-43.el7.1 will be installed
--> Processing Dependency: poppler-data >= 0.4.0 for package: poppler-0.26.5-43.el7.1.x86_64
---> Package pykickstart.noarch 0:1.99.66.22-1.el7 will be installed
---> Package pyparted.x86_64 1:3.9-15.el7 will be installed
---> Package python-IPy.noarch 0:0.75-6.el7 will be installed
---> Package python-blivet.noarch 1:0.61.15.76-1.el7_9 will be installed
--> Processing Dependency: python-pyblock >= 0.45 for package: 1:python-blivet-0.61.15.76-1.el7_9.noarch
--> Processing Dependency: python-cryptsetup >= 0.1.1 for package: 1:python-blivet-0.61.15.76-1.el7_9.noarch
--> Processing Dependency: python-blockdev for package: 1:python-blivet-0.61.15.76-1.el7_9.noarch
--> Processing Dependency: cryptsetup for package: 1:python-blivet-0.61.15.76-1.el7_9.noarch
---> Package python-coverage.x86_64 0:3.6-0.5.b3.el7 will be installed
--> Processing Dependency: python-setuptools for package: python-coverage-3.6-0.5.b3.el7.x86_64
---> Package python-nss.x86_64 0:0.16.0-3.el7 will be installed
---> Package python-ntplib.noarch 0:0.3.2-1.el7 will be installed
---> Package python-pwquality.x86_64 0:1.2.3-5.el7 will be installed
---> Package python-six.noarch 0:1.9.0-2.el7 will be installed
---> Package python2-futures.noarch 0:3.1.1-5.el7 will be installed
---> Package python2-subprocess32.x86_64 0:3.2.6-14.el7 will be installed
---> Package pytz.noarch 0:2016.10-2.el7 will be installed
---> Package qemu-img.x86_64 10:1.5.3-175.el7_9.6 will be installed
---> Package qemu-kvm-common.x86_64 10:1.5.3-175.el7_9.6 will be installed
---> Package radvd.x86_64 0:2.17-3.el7 will be installed
---> Package realmd.x86_64 0:0.16.1-12.el7_9.1 will be installed
--> Processing Dependency: oddjob-mkhomedir for package: realmd-0.16.1-12.el7_9.1.x86_64
---> Package rsync.x86_64 0:3.1.2-12.el7_9 will be installed
---> Package rtkit.x86_64 0:0.11-10.el7 will be installed
---> Package seabios-bin.noarch 0:1.11.0-2.el7 will be installed
---> Package seavgabios-bin.noarch 0:1.11.0-2.el7 will be installed
---> Package setools-libs.x86_64 0:3.3.8-4.el7 will be installed
---> Package sgabios-bin.noarch 1:0.20110622svn-4.el7 will be installed
---> Package sox.x86_64 0:14.4.1-7.el7 will be installed
---> Package spice-server.x86_64 0:0.14.0-9.el7_9.1 will be installed
---> Package unbound-libs.x86_64 0:1.6.6-5.el7_8 will be installed
---> Package usermode.x86_64 0:1.111-6.el7 will be installed
---> Package volume_key-libs.x86_64 0:0.3.9-9.el7 will be installed
---> Package webrtc-audio-processing.x86_64 0:0.3-1.el7 will be installed
---> Package wodim.x86_64 0:1.1.11-25.el7 will be installed
---> Package yajl.x86_64 0:2.0.4-4.el7 will be installed
--> Running transaction check
---> Package adobe-mappings-cmap.noarch 0:20171205-3.el7 will be installed
---> Package adobe-mappings-cmap-deprecated.noarch 0:20171205-3.el7 will be installed
---> Package adobe-mappings-pdf.noarch 0:20180407-1.el7 will be installed
---> Package boost-iostreams.x86_64 0:1.53.0-28.el7 will be installed
---> Package boost-random.x86_64 0:1.53.0-28.el7 will be installed
---> Package boost-system.x86_64 0:1.53.0-28.el7 will be installed
---> Package boost-thread.x86_64 0:1.53.0-28.el7 will be installed
---> Package bridge-utils.x86_64 0:1.5-9.el7 will be installed
---> Package cdparanoia.x86_64 0:10.2-17.el7 will be installed
---> Package cryptsetup.x86_64 0:2.0.3-6.el7 will be installed
---> Package cryptsetup-python.x86_64 0:2.0.3-6.el7 will be installed
---> Package deltarpm.x86_64 0:3.6-3.el7 will be installed
---> Package device-mapper-multipath-libs.x86_64 0:0.4.9-136.el7_9 will be installed
---> Package festival-lib.x86_64 0:1.96-28.el7 will be installed
---> Package festival-speechtools-libs.x86_64 0:1.2.96-28.el7 will be installed
---> Package festvox-slt-arctic-hts.noarch 0:0.20061229-28.el7 will be installed
---> Package glusterfs.x86_64 0:6.0-61.el7 will be installed
---> Package glusterfs-cli.x86_64 0:6.0-61.el7 will be installed
---> Package glusterfs-client-xlators.x86_64 0:6.0-61.el7 will be installed
---> Package gstreamer-plugins-bad-free.x86_64 0:0.10.23-23.el7 will be installed
--> Processing Dependency: libofa.so.0()(64bit) for package: gstreamer-plugins-bad-free-0.10.23-23.el7.x86_64
---> Package gstreamer-plugins-good.x86_64 0:0.10.31-13.el7 will be installed
---> Package gstreamer-tools.x86_64 0:0.10.36-7.el7 will be installed
---> Package iscsi-initiator-utils-iscsiuio.x86_64 0:6.2.0.874-22.el7_9 will be installed
---> Package langtable.noarch 0:0.0.31-4.el7 will be installed
---> Package libgdither.x86_64 0:0.6-8.el7 will be installed
---> Package libpaper.x86_64 0:1.1.24-9.el7 will be installed
---> Package libreport-plugin-bugzilla.x86_64 0:2.1.11-53.el7.centos will be installed
---> Package lldpad.x86_64 0:1.0.1-7.git036e314.el7_9 will be installed
--> Processing Dependency: libconfig.so.9()(64bit) for package: lldpad-1.0.1-7.git036e314.el7_9.x86_64
---> Package ndctl.x86_64 0:65-6.el7_9 will be installed
--> Processing Dependency: daxctl-libs(x86-64) = 65-6.el7_9 for package: ndctl-65-6.el7_9.x86_64
--> Processing Dependency: libdaxctl.so.1(LIBDAXCTL_5)(64bit) for package: ndctl-65-6.el7_9.x86_64
--> Processing Dependency: libdaxctl.so.1(LIBDAXCTL_4)(64bit) for package: ndctl-65-6.el7_9.x86_64
--> Processing Dependency: libdaxctl.so.1(LIBDAXCTL_3)(64bit) for package: ndctl-65-6.el7_9.x86_64
--> Processing Dependency: libdaxctl.so.1(LIBDAXCTL_2)(64bit) for package: ndctl-65-6.el7_9.x86_64
--> Processing Dependency: libdaxctl.so.1()(64bit) for package: ndctl-65-6.el7_9.x86_64
---> Package ndctl-libs.x86_64 0:65-6.el7_9 will be installed
---> Package oddjob-mkhomedir.x86_64 0:0.31.5-4.el7 will be installed
--> Processing Dependency: oddjob = 0.31.5-4.el7 for package: oddjob-mkhomedir-0.31.5-4.el7.x86_64
---> Package openjpeg2.x86_64 0:2.3.1-3.el7_7 will be installed
---> Package poppler-data.noarch 0:0.4.6-3.el7 will be installed
---> Package python-deltarpm.x86_64 0:3.6-3.el7 will be installed
---> Package python-pyblock.x86_64 0:0.53-6.el7 will be installed
--> Processing Dependency: libdmraid.so.1(Base)(64bit) for package: python-pyblock-0.53-6.el7.x86_64
--> Processing Dependency: libdmraid.so.1()(64bit) for package: python-pyblock-0.53-6.el7.x86_64
---> Package python-setuptools.noarch 0:0.9.8-7.el7 will be installed
--> Processing Dependency: python-backports-ssl_match_hostname for package: python-setuptools-0.9.8-7.el7.noarch
---> Package python2-blockdev.x86_64 0:2.18-5.el7 will be installed
---> Package rdma-core.x86_64 0:22.4-6.el7_9 will be installed
---> Package urw-base35-fonts.noarch 0:20170801-10.el7 will be installed
--> Processing Dependency: urw-base35-fonts-common = 20170801-10.el7 for package: urw-base35-fonts-20170801-10.el7.noarch
--> Processing Dependency: urw-base35-z003-fonts for package: urw-base35-fonts-20170801-10.el7.noarch
--> Processing Dependency: urw-base35-standard-symbols-ps-fonts for package: urw-base35-fonts-20170801-10.el7.noarch
--> Processing Dependency: urw-base35-p052-fonts for package: urw-base35-fonts-20170801-10.el7.noarch
--> Processing Dependency: urw-base35-nimbus-sans-fonts for package: urw-base35-fonts-20170801-10.el7.noarch
--> Processing Dependency: urw-base35-nimbus-roman-fonts for package: urw-base35-fonts-20170801-10.el7.noarch
--> Processing Dependency: urw-base35-nimbus-mono-ps-fonts for package: urw-base35-fonts-20170801-10.el7.noarch
--> Processing Dependency: urw-base35-gothic-fonts for package: urw-base35-fonts-20170801-10.el7.noarch
--> Processing Dependency: urw-base35-d050000l-fonts for package: urw-base35-fonts-20170801-10.el7.noarch
--> Processing Dependency: urw-base35-c059-fonts for package: urw-base35-fonts-20170801-10.el7.noarch
--> Processing Dependency: urw-base35-bookman-fonts for package: urw-base35-fonts-20170801-10.el7.noarch
---> Package vorbis-tools.x86_64 1:1.4.0-13.el7 will be installed
--> Running transaction check
---> Package daxctl-libs.x86_64 0:65-6.el7_9 will be installed
---> Package dmraid.x86_64 0:1.0.0.rc16-28.el7 will be installed
--> Processing Dependency: dmraid-events for package: dmraid-1.0.0.rc16-28.el7.x86_64
---> Package libconfig.x86_64 0:1.4.9-5.el7 will be installed
---> Package libofa.x86_64 0:0.9.3-24.el7 will be installed
--> Processing Dependency: libfftw3.so.3()(64bit) for package: libofa-0.9.3-24.el7.x86_64
---> Package oddjob.x86_64 0:0.31.5-4.el7 will be installed
---> Package python-backports-ssl_match_hostname.noarch 0:3.5.0.1-1.el7 will be installed
--> Processing Dependency: python-ipaddress for package: python-backports-ssl_match_hostname-3.5.0.1-1.el7.noarch
--> Processing Dependency: python-backports for package: python-backports-ssl_match_hostname-3.5.0.1-1.el7.noarch
---> Package urw-base35-bookman-fonts.noarch 0:20170801-10.el7 will be installed
--> Processing Dependency: xorg-x11-font-utils for package: urw-base35-bookman-fonts-20170801-10.el7.noarch
--> Processing Dependency: xorg-x11-font-utils for package: urw-base35-bookman-fonts-20170801-10.el7.noarch
---> Package urw-base35-c059-fonts.noarch 0:20170801-10.el7 will be installed
---> Package urw-base35-d050000l-fonts.noarch 0:20170801-10.el7 will be installed
---> Package urw-base35-fonts-common.noarch 0:20170801-10.el7 will be installed
---> Package urw-base35-gothic-fonts.noarch 0:20170801-10.el7 will be installed
---> Package urw-base35-nimbus-mono-ps-fonts.noarch 0:20170801-10.el7 will be installed
---> Package urw-base35-nimbus-roman-fonts.noarch 0:20170801-10.el7 will be installed
---> Package urw-base35-nimbus-sans-fonts.noarch 0:20170801-10.el7 will be installed
---> Package urw-base35-p052-fonts.noarch 0:20170801-10.el7 will be installed
---> Package urw-base35-standard-symbols-ps-fonts.noarch 0:20170801-10.el7 will be installed
---> Package urw-base35-z003-fonts.noarch 0:20170801-10.el7 will be installed
--> Running transaction check
---> Package dmraid-events.x86_64 0:1.0.0.rc16-28.el7 will be installed
--> Processing Dependency: sgpio for package: dmraid-events-1.0.0.rc16-28.el7.x86_64
---> Package fftw-libs-double.x86_64 0:3.3.3-8.el7 will be installed
---> Package python-backports.x86_64 0:1.0-8.el7 will be installed
---> Package python-ipaddress.noarch 0:1.0.16-2.el7 will be installed
---> Package xorg-x11-font-utils.x86_64 1:7.5-21.el7 will be installed
--> Running transaction check
---> Package sgpio.x86_64 0:1.2.0.10-13.el7 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

========================================================================================================================
 Package                                           Arch         Version                             Repository     Size
========================================================================================================================
Installing for group install "GNOME":
 NetworkManager-libreswan-gnome                    x86_64       1.2.4-2.el7                         base           36 k
 PackageKit-command-not-found                      x86_64       1.1.10-2.el7.centos                 base           21 k
 PackageKit-gtk3-module                            x86_64       1.1.10-2.el7.centos                 base           12 k
 abrt-desktop                                      x86_64       2.1.11-60.el7.centos                base           88 k
 at-spi2-atk                                       x86_64       2.26.2-1.el7                        base           81 k
 at-spi2-core                                      x86_64       2.28.0-1.el7                        base          158 k
 avahi                                             x86_64       0.6.31-20.el7                       base          264 k
 baobab                                            x86_64       3.28.0-2.el7                        base          393 k
 cheese                                            x86_64       2:3.28.0-1.el7                      base          162 k
 compat-cheese314                                  x86_64       3.14.2-1.el7                        base           54 k
 control-center                                    x86_64       1:3.28.1-8.el7_9.1                  updates       4.8 M
 dconf                                             x86_64       0.28.0-4.el7                        base          106 k
 empathy                                           x86_64       3.12.13-1.el7                       base          4.0 M
 eog                                               x86_64       3.28.3-1.el7                        base          4.7 M
 evince                                            x86_64       3.28.2-10.el7                       base          2.3 M
 evince-nautilus                                   x86_64       3.28.2-10.el7                       base           42 k
 file-roller                                       x86_64       3.28.1-2.el7                        base          1.3 M
 file-roller-nautilus                              x86_64       3.28.1-2.el7                        base           29 k
 firewall-config                                   noarch       0.6.3-13.el7_9                      updates       137 k
 firstboot                                         x86_64       19.12-1.el7                         base          111 k
 fprintd-pam                                       x86_64       0.8.1-2.el7                         base           16 k
 gdm                                               x86_64       1:3.28.2-26.el7                     updates       526 k
 gedit                                             x86_64       2:3.28.1-3.el7                      base          2.5 M
 glib-networking                                   x86_64       2.56.1-1.el7                        base          145 k
 gnome-bluetooth                                   x86_64       1:3.28.2-1.el7                      base           51 k
 gnome-boxes                                       x86_64       3.28.5-4.el7                        base          1.1 M
 gnome-calculator                                  x86_64       3.28.2-1.el7                        base          1.1 M
 gnome-classic-session                             noarch       3.28.1-17.el7_9                     updates        42 k
 gnome-clocks                                      x86_64       3.28.0-1.el7                        base          413 k
 gnome-color-manager                               x86_64       3.28.0-1.el7                        base          1.6 M
 gnome-contacts                                    x86_64       3.28.2-1.el7                        base          454 k
 gnome-dictionary                                  x86_64       3.26.1-2.el7                        base          642 k
 gnome-disk-utility                                x86_64       3.28.3-1.el7                        base          1.1 M
 gnome-font-viewer                                 x86_64       3.28.0-1.el7                        base          152 k
 gnome-getting-started-docs                        noarch       3.28.2-1.el7                        base           10 M
 gnome-icon-theme                                  noarch       3.12.0-1.el7                        base          9.7 M
 gnome-icon-theme-extras                           noarch       3.12.0-1.el7                        base          847 k
 gnome-icon-theme-symbolic                         noarch       3.12.0-2.el7                        base          201 k
 gnome-initial-setup                               x86_64       3.28.0-2.el7_9.1                    updates       760 k
 gnome-packagekit                                  x86_64       3.28.0-1.el7                        base          7.5 k
 gnome-packagekit-updater                          x86_64       3.28.0-1.el7                        base           74 k
 gnome-screenshot                                  x86_64       3.26.0-1.el7                        base          196 k
 gnome-session                                     x86_64       3.28.1-8.el7                        base          400 k
 gnome-session-xsession                            x86_64       3.28.1-8.el7                        base          6.6 k
 gnome-settings-daemon                             x86_64       3.28.1-11.el7_9                     updates       1.0 M
 gnome-shell                                       x86_64       3.28.3-34.el7_9                     updates       2.1 M
 gnome-software                                    x86_64       3.28.2-3.el7                        base          3.7 M
 gnome-system-log                                  x86_64       1:3.9.90-3.el7                      base          982 k
 gnome-system-monitor                              x86_64       3.28.2-1.el7                        base          748 k
 gnome-terminal                                    x86_64       3.28.2-3.el7                        base          1.3 M
 gnome-terminal-nautilus                           x86_64       3.28.2-3.el7                        base           36 k
 gnome-themes-standard                             x86_64       3.28-2.el7                          base          2.8 M
 gnome-tweak-tool                                  noarch       3.28.1-7.el7                        base          330 k
 gnome-user-docs                                   noarch       3.28.2-1.el7                        base           16 M
 gnome-weather                                     noarch       3.26.0-1.el7                        base          5.0 M
 gucharmap                                         x86_64       10.0.4-1.el7                        base          1.2 M
 gvfs-afc                                          x86_64       1.36.2-7.el7_9                      updates        74 k
 gvfs-afp                                          x86_64       1.36.2-7.el7_9                      updates        88 k
 gvfs-archive                                      x86_64       1.36.2-7.el7_9                      updates        42 k
 gvfs-fuse                                         x86_64       1.36.2-7.el7_9                      updates        46 k
 gvfs-goa                                          x86_64       1.36.2-7.el7_9                      updates        78 k
 gvfs-gphoto2                                      x86_64       1.36.2-7.el7_9                      updates        78 k
 gvfs-mtp                                          x86_64       1.36.2-7.el7_9                      updates        78 k
 gvfs-smb                                          x86_64       1.36.2-7.el7_9                      updates        60 k
 initial-setup-gui                                 x86_64       0.3.9.45-1.el7.centos               base           28 k
 libcanberra-gtk2                                  x86_64       0.30-9.el7                          base           25 k
 libcanberra-gtk3                                  x86_64       0.30-9.el7                          base           31 k
 libproxy-mozjs                                    x86_64       0.4.11-11.el7                       base           17 k
 librsvg2                                          x86_64       2.40.20-1.el7                       base          132 k
 libsane-hpaio                                     x86_64       3.15.9-5.el7                        base          104 k
 metacity                                          x86_64       2.34.13-7.el7                       base          1.1 M
 mousetweaks                                       x86_64       3.12.0-1.el7                        base          125 k
 nautilus                                          x86_64       3.26.3.1-7.el7                      base          2.9 M
 nautilus-sendto                                   x86_64       1:3.8.6-1.el7                       base           89 k
 nm-connection-editor                              x86_64       1.8.6-2.el7                         base          919 k
 orca                                              x86_64       3.6.3-4.el7                         base          3.9 M
 qgnomeplatform                                    x86_64       0.3-5.el7                           base           59 k
 sane-backends-drivers-scanners                    x86_64       1.0.24-12.el7                       base          2.3 M
 seahorse                                          x86_64       3.20.0-1.el7                        base          1.2 M
 setroubleshoot                                    x86_64       3.2.30-8.el7                        base          130 k
 sushi                                             x86_64       3.28.3-1.el7                        base           99 k
 totem                                             x86_64       1:3.26.2-1.el7                      base          2.2 M
 totem-nautilus                                    x86_64       1:3.26.2-1.el7                      base           38 k
 vinagre                                           x86_64       3.22.0-14.el7                       base          1.4 M
 vino                                              x86_64       3.22.0-7.el7                        base          453 k
 xdg-desktop-portal-gtk                            x86_64       1.0.2-1.el7                         base          157 k
 xdg-user-dirs-gtk                                 x86_64       0.10-4.el7                          base           66 k
 yelp                                              x86_64       2:3.28.1-1.el7                      base          777 k
Installing for dependencies:
 GConf2                                            x86_64       3.2.6-8.el7                         base          1.0 M
 ModemManager-glib                                 x86_64       1.6.10-4.el7                        base          232 k
 NetworkManager-glib                               x86_64       1:1.18.8-2.el7_9                    updates       1.5 M
 NetworkManager-libreswan                          x86_64       1.2.4-2.el7                         base          112 k
 NetworkManager-wifi                               x86_64       1:1.18.8-2.el7_9                    updates       202 k
 PackageKit                                        x86_64       1.1.10-2.el7.centos                 base          587 k
 PackageKit-glib                                   x86_64       1.1.10-2.el7.centos                 base          128 k
 PackageKit-yum                                    x86_64       1.1.10-2.el7.centos                 base           75 k
 abattis-cantarell-fonts                           noarch       0.0.25-1.el7                        base          149 k
 abrt                                              x86_64       2.1.11-60.el7.centos                base          538 k
 abrt-addon-ccpp                                   x86_64       2.1.11-60.el7.centos                base          195 k
 abrt-addon-kerneloops                             x86_64       2.1.11-60.el7.centos                base          107 k
 abrt-addon-pstoreoops                             x86_64       2.1.11-60.el7.centos                base           97 k
 abrt-addon-python                                 x86_64       2.1.11-60.el7.centos                base          103 k
 abrt-addon-vmcore                                 x86_64       2.1.11-60.el7.centos                base          107 k
 abrt-addon-xorg                                   x86_64       2.1.11-60.el7.centos                base           98 k
 abrt-dbus                                         x86_64       2.1.11-60.el7.centos                base          122 k
 abrt-gui                                          x86_64       2.1.11-60.el7.centos                base          191 k
 abrt-gui-libs                                     x86_64       2.1.11-60.el7.centos                base           96 k
 abrt-libs                                         x86_64       2.1.11-60.el7.centos                base          110 k
 abrt-python                                       x86_64       2.1.11-60.el7.centos                base          110 k
 abrt-retrace-client                               x86_64       2.1.11-60.el7.centos                base          123 k
 accountsservice                                   x86_64       0.6.50-7.el7                        base           99 k
 accountsservice-libs                              x86_64       0.6.50-7.el7                        base           81 k
 adobe-mappings-cmap                               noarch       20171205-3.el7                      base          2.1 M
 adobe-mappings-cmap-deprecated                    noarch       20171205-3.el7                      base          114 k
 adobe-mappings-pdf                                noarch       20180407-1.el7                      base          703 k
 adwaita-cursor-theme                              noarch       3.28.0-1.el7                        base          641 k
 adwaita-gtk2-theme                                x86_64       3.28-2.el7                          base          134 k
 adwaita-icon-theme                                noarch       3.28.0-1.el7                        base           11 M
 adwaita-qt5                                       x86_64       1.0-1.el7                           base          188 k
 anaconda-core                                     x86_64       21.48.22.159-1.el7.centos           base          1.6 M
 anaconda-gui                                      x86_64       21.48.22.159-1.el7.centos           base          512 k
 anaconda-tui                                      x86_64       21.48.22.159-1.el7.centos           base          292 k
 anaconda-widgets                                  x86_64       21.48.22.159-1.el7.centos           base          220 k
 appstream-data                                    noarch       7-20180614.el7                      base          7.2 M
 atk                                               x86_64       2.28.1-2.el7                        base          263 k
 atkmm                                             x86_64       2.24.2-1.el7                        base           79 k
 audit-libs-python                                 x86_64       2.8.5-4.el7                         base           76 k
 augeas-libs                                       x86_64       1.4.0-10.el7                        base          357 k
 avahi-glib                                        x86_64       0.6.31-20.el7                       base           25 k
 avahi-gobject                                     x86_64       0.6.31-20.el7                       base           35 k
 avahi-libs                                        x86_64       0.6.31-20.el7                       base           62 k
 avahi-ui-gtk3                                     x86_64       0.6.31-20.el7                       base           37 k
 bluez                                             x86_64       5.44-7.el7                          base          1.2 M
 bolt                                              x86_64       0.7-1.el7                           base          149 k
 boost-iostreams                                   x86_64       1.53.0-28.el7                       base           61 k
 boost-random                                      x86_64       1.53.0-28.el7                       base           39 k
 boost-system                                      x86_64       1.53.0-28.el7                       base           40 k
 boost-thread                                      x86_64       1.53.0-28.el7                       base           58 k
 brasero                                           x86_64       3.12.2-5.el7_9.1                    updates       2.6 M
 brasero-libs                                      x86_64       3.12.2-5.el7_9.1                    updates       333 k
 brasero-nautilus                                  x86_64       3.12.2-5.el7_9.1                    updates        30 k
 bridge-utils                                      x86_64       1.5-9.el7                           base           32 k
 brlapi                                            x86_64       0.6.0-16.el7                        base          114 k
 brltty                                            x86_64       4.5-16.el7                          base          933 k
 cairo                                             x86_64       1.15.12-4.el7                       base          741 k
 cairo-gobject                                     x86_64       1.15.12-4.el7                       base           26 k
 cairomm                                           x86_64       1.12.0-1.el7                        base           59 k
 cdparanoia                                        x86_64       10.2-17.el7                         base           55 k
 cdparanoia-libs                                   x86_64       10.2-17.el7                         base           56 k
 cdrdao                                            x86_64       1.2.3-20.el7                        base          320 k
 celt051                                           x86_64       0.5.1.3-8.el7                       base           53 k
 checkpolicy                                       x86_64       2.5-8.el7                           base          295 k
 cheese-libs                                       x86_64       2:3.28.0-1.el7                      base          814 k
 clutter                                           x86_64       1.26.2-2.el7                        base          1.1 M
 clutter-gst2                                      x86_64       2.0.18-1.el7                        base           61 k
 clutter-gst3                                      x86_64       3.0.26-1.el7                        base           75 k
 clutter-gtk                                       x86_64       1.8.4-1.el7                         base           44 k
 cogl                                              x86_64       1.22.2-2.el7                        base          462 k
 color-filesystem                                  noarch       1-13.el7                            base          5.3 k
 colord                                            x86_64       1.3.4-2.el7                         base          478 k
 colord-gtk                                        x86_64       0.1.25-4.el7                        base           21 k
 colord-libs                                       x86_64       1.3.4-2.el7                         base          186 k
 compat-exiv2-026                                  x86_64       0.26-2.el7                          base          828 k
 compat-gnome-desktop314                           x86_64       3.14.2-1.el7                        base          108 k
 compat-libcolord1                                 x86_64       1.0.4-1.el7                         base           96 k
 control-center-filesystem                         x86_64       1:3.28.1-8.el7_9.1                  updates        25 k
 createrepo                                        noarch       0.9.9-28.el7                        base           94 k
 cryptsetup                                        x86_64       2.0.3-6.el7                         base          154 k
 cryptsetup-python                                 x86_64       2.0.3-6.el7                         base           36 k
 cups-libs                                         x86_64       1:1.6.3-51.el7                      base          359 k
 cups-pk-helper                                    x86_64       0.2.6-2.el7                         base           81 k
 cyrus-sasl                                        x86_64       2.1.26-24.el7_9                     updates        88 k
 cyrus-sasl-gssapi                                 x86_64       2.1.26-24.el7_9                     updates        41 k
 cyrus-sasl-md5                                    x86_64       2.1.26-24.el7_9                     updates        57 k
 cyrus-sasl-plain                                  x86_64       2.1.26-24.el7_9                     updates        39 k
 cyrus-sasl-scram                                  x86_64       2.1.26-24.el7_9                     updates        43 k
 daxctl-libs                                       x86_64       65-6.el7_9                          updates        27 k
 dbus-x11                                          x86_64       1:1.10.24-15.el7                    base           48 k
 dejavu-fonts-common                               noarch       2.33-6.el7                          base           64 k
 dejavu-sans-fonts                                 noarch       2.33-6.el7                          base          1.4 M
 deltarpm                                          x86_64       3.6-3.el7                           base           82 k
 desktop-file-utils                                x86_64       0.23-2.el7                          base           67 k
 device-mapper-multipath                           x86_64       0.4.9-136.el7_9                     updates       148 k
 device-mapper-multipath-libs                      x86_64       0.4.9-136.el7_9                     updates       268 k
 dleyna-connector-dbus                             x86_64       0.2.0-2.el7                         base           20 k
 dleyna-core                                       x86_64       0.5.0-1.el7                         base           26 k
 dleyna-server                                     x86_64       0.5.0-3.el7                         base           72 k
 dmraid                                            x86_64       1.0.0.rc16-28.el7                   base          151 k
 dmraid-events                                     x86_64       1.0.0.rc16-28.el7                   base           21 k
 dnsmasq                                           x86_64       2.76-17.el7_9.3                     updates       281 k
 dotconf                                           x86_64       1.3-8.el7                           base           27 k
 dvd+rw-tools                                      x86_64       7.1-15.el7                          base          132 k
 elfutils                                          x86_64       0.176-5.el7                         base          308 k
 emacs-filesystem                                  noarch       1:24.3-23.el7_9.1                   updates        58 k
 enchant                                           x86_64       1:1.6.0-8.el7                       base           55 k
 espeak                                            x86_64       1.47.11-4.el7                       base          1.1 M
 evince-libs                                       x86_64       3.28.2-10.el7                       base          391 k
 evolution-data-server                             x86_64       3.28.5-5.el7_9.1                    updates       2.1 M
 evolution-data-server-langpacks                   noarch       3.28.5-5.el7_9.1                    updates       1.4 M
 exempi                                            x86_64       2.2.0-9.el7                         base          414 k
 farstream                                         x86_64       0.1.2-8.el7                         base          230 k
 farstream02                                       x86_64       0.2.3-3.el7                         base          227 k
 fcoe-utils                                        x86_64       1.0.32-2.el7_6                      base          120 k
 festival                                          x86_64       1.96-28.el7                         base          1.3 M
 festival-freebsoft-utils                          noarch       0.10-7.el7                          base           36 k
 festival-lib                                      x86_64       1.96-28.el7                         base          458 k
 festival-speechtools-libs                         x86_64       1.2.96-28.el7                       base          1.0 M
 festvox-slt-arctic-hts                            noarch       0.20061229-28.el7                   base          1.0 M
 fftw-libs-double                                  x86_64       3.3.3-8.el7                         base          759 k
 flac-libs                                         x86_64       1.3.0-5.el7_1                       base          169 k
 flatpak                                           x86_64       1.0.9-12.el7_9                      updates       958 k
 flatpak-libs                                      x86_64       1.0.9-12.el7_9                      updates       597 k
 flite                                             x86_64       1.3-22.el7                          base          6.1 M
 folks                                             x86_64       1:0.11.4-1.el7                      base          613 k
 fontconfig                                        x86_64       2.13.0-4.3.el7                      base          254 k
 fontpackages-filesystem                           noarch       1.44-8.el7                          base          9.9 k
 fprintd                                           x86_64       0.8.1-2.el7                         base           89 k
 freerdp-libs                                      x86_64       2.1.1-5.el7_9                       updates       855 k
 frei0r-plugins                                    x86_64       1.3-13.el7                          base          458 k
 fribidi                                           x86_64       1.0.2-1.el7_7.1                     base           79 k
 fros                                              noarch       1.0-5.el7                           base           22 k
 fuse                                              x86_64       2.9.2-11.el7                        base           86 k
 fwupd                                             x86_64       1.0.8-5.el7                         base          585 k
 fwupdate-efi                                      x86_64       12-6.el7.centos                     base           58 k
 fwupdate-libs                                     x86_64       12-6.el7.centos                     base           27 k
 gavl                                              x86_64       1.4.0-4.el7                         base          2.6 M
 gcr                                               x86_64       3.28.0-1.el7                        base          677 k
 gd                                                x86_64       2.0.35-27.el7_9                     updates       146 k
 gdb                                               x86_64       7.6.1-120.el7                       base          2.4 M
 gdisk                                             x86_64       0.8.10-3.el7                        base          190 k
 gdk-pixbuf2                                       x86_64       2.36.12-3.el7                       base          570 k
 genisoimage                                       x86_64       1.1.11-25.el7                       base          299 k
 geoclue2                                          x86_64       2.4.8-1.el7                         base          106 k
 geoclue2-libs                                     x86_64       2.4.8-1.el7                         base           43 k
 geocode-glib                                      x86_64       3.26.0-3.el7                        base           64 k
 gjs                                               x86_64       1.52.5-1.el7_6                      base          329 k
 glade-libs                                        x86_64       3.22.1-1.el7                        base          685 k
 glibmm24                                          x86_64       2.56.0-1.el7                        base          534 k
 glusterfs                                         x86_64       6.0-61.el7                          updates       586 k
 glusterfs-api                                     x86_64       6.0-61.el7                          updates        89 k
 glusterfs-cli                                     x86_64       6.0-61.el7                          updates       179 k
 glusterfs-client-xlators                          x86_64       6.0-61.el7                          updates       786 k
 glusterfs-libs                                    x86_64       6.0-61.el7                          updates       389 k
 glx-utils                                         x86_64       8.3.0-10.el7                        base           34 k
 gnome-abrt                                        x86_64       0.3.4-9.el7                         base          216 k
 gnome-bluetooth-libs                              x86_64       1:3.28.2-1.el7                      base          308 k
 gnome-desktop3                                    x86_64       3.28.2-2.el7                        base          594 k
 gnome-keyring                                     x86_64       3.28.2-1.el7                        base          908 k
 gnome-keyring-pam                                 x86_64       3.28.2-1.el7                        base           39 k
 gnome-menus                                       x86_64       3.13.3-3.el7                        base          180 k
 gnome-online-accounts                             x86_64       3.28.2-1.el7                        base          1.0 M
 gnome-packagekit-common                           x86_64       3.28.0-1.el7                        base          1.1 M
 gnome-packagekit-installer                        x86_64       3.28.0-1.el7                        base           78 k
 gnome-shell-extension-alternate-tab               noarch       3.28.1-17.el7_9                     updates        21 k
 gnome-shell-extension-apps-menu                   noarch       3.28.1-17.el7_9                     updates        26 k
 gnome-shell-extension-common                      noarch       3.28.1-17.el7_9                     updates       149 k
 gnome-shell-extension-horizontal-workspaces       noarch       3.28.1-17.el7_9                     updates        20 k
 gnome-shell-extension-launch-new-instance         noarch       3.28.1-17.el7_9                     updates        20 k
 gnome-shell-extension-places-menu                 noarch       3.28.1-17.el7_9                     updates        25 k
 gnome-shell-extension-top-icons                   noarch       3.28.1-17.el7_9                     updates        21 k
 gnome-shell-extension-user-theme                  noarch       3.28.1-17.el7_9                     updates        21 k
 gnome-shell-extension-window-list                 noarch       3.28.1-17.el7_9                     updates        34 k
 gnome-video-effects                               noarch       0.4.3-1.el7                         base           74 k
 gom                                               x86_64       0.4-1.el7                           base           59 k
 google-noto-emoji-color-fonts                     noarch       20180508-4.el7                      base          6.4 M
 gperftools-libs                                   x86_64       2.6.1-1.el7                         base          272 k
 graphite2                                         x86_64       1.3.10-1.el7_3                      base          115 k
 grilo                                             x86_64       0.3.6-1.el7                         base          210 k
 grilo-plugins                                     x86_64       0.3.7-1.el7                         base          964 k
 gsettings-desktop-schemas                         x86_64       3.28.0-3.el7                        base          606 k
 gsm                                               x86_64       1.0.13-11.el7                       base           30 k
 gsound                                            x86_64       1.0.2-2.el7                         base           29 k
 gspell                                            x86_64       1.6.1-1.el7                         base           91 k
 gssdp                                             x86_64       1.0.2-1.el7                         base           49 k
 gstreamer                                         x86_64       0.10.36-7.el7                       base          958 k
 gstreamer-plugins-bad-free                        x86_64       0.10.23-23.el7                      base          1.4 M
 gstreamer-plugins-base                            x86_64       0.10.36-10.el7                      base          1.2 M
 gstreamer-plugins-good                            x86_64       0.10.31-13.el7                      base          1.5 M
 gstreamer-tools                                   x86_64       0.10.36-7.el7                       base           27 k
 gstreamer1                                        x86_64       1.10.4-2.el7                        base          1.2 M
 gstreamer1-plugins-bad-free                       x86_64       1.10.4-3.el7                        base          1.7 M
 gstreamer1-plugins-base                           x86_64       1.10.4-2.el7                        base          1.4 M
 gstreamer1-plugins-good                           x86_64       1.10.4-2.el7                        base          2.0 M
 gstreamer1-plugins-ugly-free                      x86_64       1.10.4-3.el7                        base           80 k
 gtk-update-icon-cache                             x86_64       3.22.30-8.el7_9                     updates        27 k
 gtk-vnc2                                          x86_64       0.7.0-3.el7                         base           41 k
 gtk2                                              x86_64       2.24.31-1.el7                       base          3.4 M
 gtk3                                              x86_64       3.22.30-8.el7_9                     updates       4.4 M
 gtkmm30                                           x86_64       3.22.2-1.el7                        base          925 k
 gtksourceview3                                    x86_64       3.24.8-2.el7                        base          585 k
 gucharmap-libs                                    x86_64       10.0.4-1.el7                        base          1.1 M
 gupnp                                             x86_64       1.0.2-6.el7_9                       updates        94 k
 gupnp-av                                          x86_64       0.12.10-1.el7                       base           88 k
 gupnp-dlna                                        x86_64       0.10.5-1.el7                        base           84 k
 gupnp-igd                                         x86_64       0.2.5-2.el7                         base           29 k
 gvfs                                              x86_64       1.36.2-7.el7_9                      updates       354 k
 gvfs-client                                       x86_64       1.36.2-7.el7_9                      updates       799 k
 gvnc                                              x86_64       0.7.0-3.el7                         base           94 k
 harfbuzz                                          x86_64       1.7.5-2.el7                         base          267 k
 harfbuzz-icu                                      x86_64       1.7.5-2.el7                         base           12 k
 hicolor-icon-theme                                noarch       0.12-7.el7                          base           42 k
 highcontrast-qt5                                  x86_64       0.1-2.el7                           base          179 k
 hplip-common                                      x86_64       3.15.9-5.el7                        base           89 k
 hplip-libs                                        x86_64       3.15.9-5.el7                        base          176 k
 hunspell                                          x86_64       1.3.2-16.el7                        base          223 k
 hunspell-en-US                                    noarch       0.20121024-6.el7                    base          190 k
 hyphen                                            x86_64       2.8.6-5.el7                         base           26 k
 ibus                                              x86_64       1.5.17-12.el7_9                     updates       4.8 M
 ibus-gtk2                                         x86_64       1.5.17-12.el7_9                     updates        45 k
 ibus-gtk3                                         x86_64       1.5.17-12.el7_9                     updates        46 k
 ibus-libs                                         x86_64       1.5.17-12.el7_9                     updates       228 k
 ibus-setup                                        noarch       1.5.17-12.el7_9                     updates        80 k
 icedax                                            x86_64       1.1.11-25.el7                       base          138 k
 initial-setup                                     x86_64       0.3.9.45-1.el7.centos               base           90 k
 ipxe-roms-qemu                                    noarch       20180825-3.git133f4c.el7            base          802 k
 iscsi-initiator-utils                             x86_64       6.2.0.874-22.el7_9                  updates       423 k
 iscsi-initiator-utils-iscsiuio                    x86_64       6.2.0.874-22.el7_9                  updates        94 k
 iso-codes                                         noarch       3.46-2.el7                          base          2.7 M
 isomd5sum                                         x86_64       1:1.0.10-5.el7                      base           27 k
 jasper-libs                                       x86_64       1.900.1-33.el7                      base          150 k
 json-glib                                         x86_64       1.4.2-2.el7                         base          134 k
 keybinder3                                        x86_64       0.3.0-1.el7                         base           14 k
 langtable                                         noarch       0.0.31-4.el7                        base           32 k
 langtable-data                                    noarch       0.0.31-4.el7                        base          620 k
 langtable-python                                  noarch       0.0.31-4.el7                        base           28 k
 lcms2                                             x86_64       2.6-3.el7                           base          150 k
 ldns                                              x86_64       1.6.16-10.el7                       base          476 k
 libXcomposite                                     x86_64       0.4.4-4.1.el7                       base           22 k
 libXft                                            x86_64       2.3.2-2.el7                         base           58 k
 libXpm                                            x86_64       3.5.12-2.el7_9                      updates        56 k
 libXres                                           x86_64       1.2.0-1.el7                         base           15 k
 libXv                                             x86_64       1.0.11-1.el7                        base           18 k
 libao                                             x86_64       1.1.0-8.el7                         base           72 k
 libappstream-glib                                 x86_64       0.7.8-2.el7                         base          286 k
 libasyncns                                        x86_64       0.8-7.el7                           base           26 k
 libatasmart                                       x86_64       0.19-6.el7                          base           43 k
 libavc1394                                        x86_64       0.5.3-14.el7                        base           50 k
 libblockdev                                       x86_64       2.18-5.el7                          base          119 k
 libblockdev-crypto                                x86_64       2.18-5.el7                          base           60 k
 libblockdev-fs                                    x86_64       2.18-5.el7                          base           66 k
 libblockdev-loop                                  x86_64       2.18-5.el7                          base           51 k
 libblockdev-mdraid                                x86_64       2.18-5.el7                          base           57 k
 libblockdev-nvdimm                                x86_64       2.18-5.el7                          base           53 k
 libblockdev-part                                  x86_64       2.18-5.el7                          base           60 k
 libblockdev-swap                                  x86_64       2.18-5.el7                          base           52 k
 libblockdev-utils                                 x86_64       2.18-5.el7                          base           58 k
 libbluray                                         x86_64       0.2.3-6.el7                         base          135 k
 libburn                                           x86_64       1.2.8-4.el7                         base          149 k
 libbytesize                                       x86_64       1.2-1.el7                           base           52 k
 libcacard                                         x86_64       40:2.7.0-1.el7                      base           35 k
 libcanberra                                       x86_64       0.30-9.el7                          base           82 k
 libcdio                                           x86_64       0.92-3.el7                          base          236 k
 libcdio-paranoia                                  x86_64       10.2+0.90-11.el7                    base           70 k
 libcgroup                                         x86_64       0.41-21.el7                         base           66 k
 libchamplain                                      x86_64       0.12.16-2.el7                       base          135 k
 libchamplain-gtk                                  x86_64       0.12.16-2.el7                       base           23 k
 libconfig                                         x86_64       1.4.9-5.el7                         base           59 k
 libdmapsharing                                    x86_64       2.9.37-1.el7                        base          110 k
 libdv                                             x86_64       1.0.0-17.el7                        base           78 k
 libdvdnav                                         x86_64       5.0.3-1.el7                         base           48 k
 libdvdread                                        x86_64       5.0.3-3.el7                         base           66 k
 libepoxy                                          x86_64       1.5.2-1.el7                         base          211 k
 libevdev                                          x86_64       1.5.6-1.el7                         base           34 k
 libexif                                           x86_64       0.6.22-2.el7_9                      updates       423 k
 libfprint                                         x86_64       0.8.2-1.el7                         base          200 k
 libgcab1                                          x86_64       0.7-4.el7_4                         base           66 k
 libgdata                                          x86_64       0.17.9-1.el7                        base          439 k
 libgdither                                        x86_64       0.6-8.el7                           base           20 k
 libgee                                            x86_64       0.20.1-1.el7                        base          272 k
 libglade2                                         x86_64       2.6.4-11.el7                        base           64 k
 libglvnd-egl                                      x86_64       1:1.0.1-0.8.git5baa1e5.el7          base           44 k
 libglvnd-gles                                     x86_64       1:1.0.1-0.8.git5baa1e5.el7          base           34 k
 libgnomekbd                                       x86_64       3.26.0-3.el7                        base          161 k
 libgovirt                                         x86_64       0.3.4-5.el7                         base           75 k
 libgphoto2                                        x86_64       2.5.15-3.el7                        base          1.4 M
 libgs                                             x86_64       9.25-5.el7                          base          4.6 M
 libgsf                                            x86_64       1.14.26-7.el7                       base          166 k
 libgtop2                                          x86_64       2.38.0-3.el7                        base          134 k
 libgudev1                                         x86_64       219-78.el7_9.7                      updates       110 k
 libgusb                                           x86_64       0.2.9-1.el7                         base           40 k
 libgweather                                       x86_64       3.28.2-4.el7_9                      updates       3.1 M
 libgxps                                           x86_64       0.3.0-4.el7                         base           70 k
 libibverbs                                        x86_64       22.4-6.el7_9                        updates       269 k
 libical                                           x86_64       3.0.3-2.el7                         base          265 k
 libicu                                            x86_64       50.2-4.el7_7                        base          6.9 M
 libiec61883                                       x86_64       1.2.0-10.el7                        base           37 k
 libieee1284                                       x86_64       0.2.11-15.el7                       base           39 k
 libimobiledevice                                  x86_64       1.2.0-1.el7                         base           70 k
 libinput                                          x86_64       1.10.7-2.el7                        base          147 k
 libiptcdata                                       x86_64       1.0.4-11.el7                        base           56 k
 libiscsi                                          x86_64       1.9.0-7.el7                         base           60 k
 libisofs                                          x86_64       1.2.8-4.el7                         base          172 k
 libldb                                            x86_64       1.5.4-2.el7                         updates       149 k
 liblouis                                          x86_64       2.5.2-12.el7_4                      base          1.2 M
 liblouis-python                                   noarch       2.5.2-12.el7_4                      base           12 k
 libmediaart                                       x86_64       1.9.4-1.el7                         base           38 k
 libmodman                                         x86_64       2.0.1-8.el7                         base           28 k
 libmpcdec                                         x86_64       1.2.6-12.el7                        base           28 k
 libmtp                                            x86_64       1.1.14-1.el7                        base          174 k
 libmusicbrainz5                                   x86_64       5.0.1-9.el7                         base          148 k
 libnice                                           x86_64       0.1.3-4.el7                         base          128 k
 libnl                                             x86_64       1.1.4-3.el7                         base          128 k
 libnm-gtk                                         x86_64       1.8.6-2.el7                         base           91 k
 libnma                                            x86_64       1.8.6-2.el7                         base           98 k
 libnotify                                         x86_64       0.7.7-1.el7                         base           39 k
 liboauth                                          x86_64       0.9.7-4.el7                         base           22 k
 libofa                                            x86_64       0.9.3-24.el7                        base           61 k
 libogg                                            x86_64       2:1.3.0-7.el7                       base           24 k
 libosinfo                                         x86_64       1.1.0-5.el7                         base          230 k
 libpaper                                          x86_64       1.1.24-9.el7                        base           37 k
 libpcap                                           x86_64       14:1.5.3-13.el7_9                   updates       139 k
 libpeas                                           x86_64       1.22.0-1.el7                        base          113 k
 libpeas-gtk                                       x86_64       1.22.0-1.el7                        base           29 k
 libpeas-loader-python                             x86_64       1.22.0-1.el7                        base           20 k
 libplist                                          x86_64       1.12-3.el7                          base           58 k
 libproxy                                          x86_64       0.4.11-11.el7                       base           64 k
 libpurple                                         x86_64       2.10.11-9.el7                       base          5.4 M
 librados2                                         x86_64       1:10.2.5-4.el7                      base          1.8 M
 libraw1394                                        x86_64       2.1.0-2.el7                         base           63 k
 librbd1                                           x86_64       1:10.2.5-4.el7                      base          2.4 M
 librdmacm                                         x86_64       22.4-6.el7_9                        updates        64 k
 libreport                                         x86_64       2.1.11-53.el7.centos                base          459 k
 libreport-anaconda                                x86_64       2.1.11-53.el7.centos                base           51 k
 libreport-centos                                  x86_64       2.1.11-53.el7.centos                base           51 k
 libreport-cli                                     x86_64       2.1.11-53.el7.centos                base           53 k
 libreport-filesystem                              x86_64       2.1.11-53.el7.centos                base           41 k
 libreport-gtk                                     x86_64       2.1.11-53.el7.centos                base          101 k
 libreport-plugin-bugzilla                         x86_64       2.1.11-53.el7.centos                base           89 k
 libreport-plugin-mantisbt                         x86_64       2.1.11-53.el7.centos                base           73 k
 libreport-plugin-reportuploader                   x86_64       2.1.11-53.el7.centos                base           65 k
 libreport-plugin-rhtsupport                       x86_64       2.1.11-53.el7.centos                base           79 k
 libreport-plugin-ureport                          x86_64       2.1.11-53.el7.centos                base           59 k
 libreport-python                                  x86_64       2.1.11-53.el7.centos                base           71 k
 libreport-rhel-anaconda-bugzilla                  x86_64       2.1.11-53.el7.centos                base           43 k
 libreport-web                                     x86_64       2.1.11-53.el7.centos                base           58 k
 libreswan                                         x86_64       3.25-9.1.el7_8                      updates       1.4 M
 libsecret                                         x86_64       0.18.6-1.el7                        base          153 k
 libsemanage-python                                x86_64       2.5-14.el7                          base          113 k
 libshout                                          x86_64       2.2.2-11.el7                        base           43 k
 libsigc++20                                       x86_64       2.10.0-1.el7                        base           37 k
 libsmbclient                                      x86_64       4.10.16-24.el7_9                    updates       146 k
 libsmbios                                         x86_64       2.3.3-8.el7                         base           72 k
 libsndfile                                        x86_64       1.0.25-12.el7_9.1                   updates       150 k
 libsoup                                           x86_64       2.62.2-2.el7                        base          411 k
 libspectre                                        x86_64       0.2.8-1.el7                         base           41 k
 libsrtp                                           x86_64       1.4.4-11.20101004cvs.el7            base          275 k
 libtalloc                                         x86_64       2.1.16-1.el7                        base           33 k
 libtar                                            x86_64       1.2.11-29.el7                       base           33 k
 libtdb                                            x86_64       1.3.18-1.el7                        base           49 k
 libtevent                                         x86_64       0.9.39-1.el7                        base           41 k
 libthai                                           x86_64       0.1.14-9.el7                        base          187 k
 libtheora                                         x86_64       1:1.1.1-8.el7                       base          136 k
 libtimezonemap                                    x86_64       0.4.4-2.el7_9                       updates       2.1 M
 libtool-ltdl                                      x86_64       2.4.2-22.el7_3                      base           49 k
 libudisks2                                        x86_64       2.8.4-1.el7                         base          129 k
 libusal                                           x86_64       1.1.11-25.el7                       base          136 k
 libusbmuxd                                        x86_64       1.0.10-5.el7                        base           29 k
 libusbx                                           x86_64       1.0.21-1.el7                        base           61 k
 libuser-python                                    x86_64       0.60-9.el7                          base           52 k
 libv4l                                            x86_64       0.9.5-4.el7                         base          194 k
 libvirt-daemon                                    x86_64       4.5.0-36.el7_9.5                    updates       845 k
 libvirt-daemon-config-network                     x86_64       4.5.0-36.el7_9.5                    updates       205 k
 libvirt-daemon-driver-interface                   x86_64       4.5.0-36.el7_9.5                    updates       243 k
 libvirt-daemon-driver-network                     x86_64       4.5.0-36.el7_9.5                    updates       417 k
 libvirt-daemon-driver-nodedev                     x86_64       4.5.0-36.el7_9.5                    updates       242 k
 libvirt-daemon-driver-nwfilter                    x86_64       4.5.0-36.el7_9.5                    updates       266 k
 libvirt-daemon-driver-qemu                        x86_64       4.5.0-36.el7_9.5                    updates       752 k
 libvirt-daemon-driver-secret                      x86_64       4.5.0-36.el7_9.5                    updates       232 k
 libvirt-daemon-driver-storage                     x86_64       4.5.0-36.el7_9.5                    updates       203 k
 libvirt-daemon-driver-storage-core                x86_64       4.5.0-36.el7_9.5                    updates       444 k
 libvirt-daemon-driver-storage-disk                x86_64       4.5.0-36.el7_9.5                    updates       234 k
 libvirt-daemon-driver-storage-gluster             x86_64       4.5.0-36.el7_9.5                    updates       242 k
 libvirt-daemon-driver-storage-iscsi               x86_64       4.5.0-36.el7_9.5                    updates       231 k
 libvirt-daemon-driver-storage-logical             x86_64       4.5.0-36.el7_9.5                    updates       235 k
 libvirt-daemon-driver-storage-mpath               x86_64       4.5.0-36.el7_9.5                    updates       230 k
 libvirt-daemon-driver-storage-rbd                 x86_64       4.5.0-36.el7_9.5                    updates       237 k
 libvirt-daemon-driver-storage-scsi                x86_64       4.5.0-36.el7_9.5                    updates       231 k
 libvirt-daemon-kvm                                x86_64       4.5.0-36.el7_9.5                    updates       203 k
 libvirt-gconfig                                   x86_64       1.0.0-1.el7                         base           90 k
 libvirt-glib                                      x86_64       1.0.0-1.el7                         base           89 k
 libvirt-gobject                                   x86_64       1.0.0-1.el7                         base           64 k
 libvirt-libs                                      x86_64       4.5.0-36.el7_9.5                    updates       4.2 M
 libvisual                                         x86_64       0.4.0-16.el7                        base          138 k
 libvorbis                                         x86_64       1:1.3.3-8.el7.1                     base          204 k
 libvpx                                            x86_64       1.3.0-8.el7                         base          498 k
 libwacom                                          x86_64       0.30-1.el7                          base           32 k
 libwacom-data                                     noarch       0.30-1.el7                          base           70 k
 libwayland-client                                 x86_64       1.15.0-1.el7                        base           33 k
 libwayland-cursor                                 x86_64       1.15.0-1.el7                        base           20 k
 libwayland-egl                                    x86_64       1.15.0-1.el7                        base           13 k
 libwayland-server                                 x86_64       1.15.0-1.el7                        base           39 k
 libwbclient                                       x86_64       4.10.16-24.el7_9                    updates       117 k
 libwebp                                           x86_64       0.3.0-11.el7                        updates       170 k
 libwinpr                                          x86_64       2.1.1-5.el7_9                       updates       346 k
 libwnck3                                          x86_64       3.24.1-2.el7                        base          376 k
 libxkbcommon                                      x86_64       0.7.1-3.el7                         base          108 k
 libxkbcommon-x11                                  x86_64       0.7.1-3.el7                         base           19 k
 libxklavier                                       x86_64       5.4-7.el7                           base           64 k
 libxslt                                           x86_64       1.1.28-6.el7                        base          242 k
 lldpad                                            x86_64       1.0.1-7.git036e314.el7_9            updates       283 k
 lockdev                                           x86_64       1.0.4-0.13.20111007git.el7          base           31 k
 lzop                                              x86_64       1.03-10.el7                         base           54 k
 mdadm                                             x86_64       4.1-9.el7_9                         updates       439 k
 meanwhile                                         x86_64       1.1.0-12.el7                        base           96 k
 mesa-libEGL                                       x86_64       18.3.4-12.el7_9                     updates       110 k
 mesa-libgbm                                       x86_64       18.3.4-12.el7_9                     updates        39 k
 mobile-broadband-provider-info                    noarch       1.20170310-1.el7                    base           51 k
 mozjs52                                           x86_64       52.9.0-1.el7                        base          6.6 M
 mpg123-libs                                       x86_64       1.25.6-1.el7                        base          197 k
 mtdev                                             x86_64       1.1.5-5.el7                         base           18 k
 mtools                                            x86_64       4.0.18-5.el7                        base          203 k
 mutter                                            x86_64       3.28.3-32.el7_9                     updates       2.3 M
 nautilus-extensions                               x86_64       3.26.3.1-7.el7                      base           76 k
 ncompress                                         x86_64       4.2.4.4-3.1.el7_8                   base           27 k
 ndctl                                             x86_64       65-6.el7_9                          updates       161 k
 ndctl-libs                                        x86_64       65-6.el7_9                          updates        65 k
 neon                                              x86_64       0.30.0-4.el7                        base          166 k
 net-snmp-libs                                     x86_64       1:5.7.2-49.el7_9.2                  updates       752 k
 netcf-libs                                        x86_64       0.2.8-4.el7                         base           70 k
 nmap-ncat                                         x86_64       2:6.40-19.el7                       base          206 k
 numad                                             x86_64       0.5-18.20150602git.el7              base           35 k
 oddjob                                            x86_64       0.31.5-4.el7                        base           69 k
 oddjob-mkhomedir                                  x86_64       0.31.5-4.el7                        base           38 k
 openjpeg-libs                                     x86_64       1.5.1-18.el7                        base           86 k
 openjpeg2                                         x86_64       2.3.1-3.el7_7                       base          153 k
 opus                                              x86_64       1.0.2-6.el7                         base          630 k
 orc                                               x86_64       0.4.26-1.el7                        base          166 k
 osinfo-db                                         noarch       20200529-1.el7                      base          223 k
 osinfo-db-tools                                   x86_64       1.1.0-1.el7                         base           79 k
 pakchois                                          x86_64       0.4-10.el7                          base           14 k
 pango                                             x86_64       1.42.4-4.el7_7                      base          280 k
 pangomm                                           x86_64       2.40.1-1.el7                        base           58 k
 pcre2                                             x86_64       10.23-2.el7                         base          201 k
 pcre2-utf16                                       x86_64       10.23-2.el7                         base          189 k
 pinentry-gtk                                      x86_64       0.8.1-17.el7                        base           51 k
 policycoreutils-python                            x86_64       2.5-34.el7                          base          457 k
 poppler                                           x86_64       0.26.5-43.el7.1                     updates       787 k
 poppler-data                                      noarch       0.4.6-3.el7                         base          2.2 M
 poppler-glib                                      x86_64       0.26.5-43.el7.1                     updates       142 k
 pulseaudio                                        x86_64       10.0-6.el7_9                        updates       923 k
 pulseaudio-gdm-hooks                              x86_64       10.0-6.el7_9                        updates        20 k
 pulseaudio-libs                                   x86_64       10.0-6.el7_9                        updates       651 k
 pulseaudio-libs-glib2                             x86_64       10.0-6.el7_9                        updates        27 k
 pulseaudio-module-bluetooth                       x86_64       10.0-6.el7_9                        updates        75 k
 pycairo                                           x86_64       1.8.10-8.el7                        base          157 k
 pygobject2                                        x86_64       2.28.6-11.el7                       base          226 k
 pygtk2                                            x86_64       2.24.0-9.el7                        base          914 k
 pygtk2-libglade                                   x86_64       2.24.0-9.el7                        base           25 k
 pykickstart                                       noarch       1.99.66.22-1.el7                    base          367 k
 pyparted                                          x86_64       1:3.9-15.el7                        base          195 k
 python-IPy                                        noarch       0.75-6.el7                          base           32 k
 python-augeas                                     noarch       0.5.0-2.el7                         base           25 k
 python-backports                                  x86_64       1.0-8.el7                           base          5.8 k
 python-backports-ssl_match_hostname               noarch       3.5.0.1-1.el7                       base           13 k
 python-blivet                                     noarch       1:0.61.15.76-1.el7_9                updates       835 k
 python-brlapi                                     x86_64       0.6.0-16.el7                        base           59 k
 python-coverage                                   x86_64       3.6-0.5.b3.el7                      base          153 k
 python-deltarpm                                   x86_64       3.6-3.el7                           base           31 k
 python-di                                         noarch       0.3-2.el7                           base           19 k
 python-ethtool                                    x86_64       0.8-8.el7                           base           34 k
 python-gobject                                    x86_64       3.22.0-1.el7_4.1                    base           16 k
 python-inotify                                    noarch       0.9.4-4.el7                         base           49 k
 python-ipaddress                                  noarch       1.0.16-2.el7                        base           34 k
 python-meh                                        noarch       0.25.3-1.el7                        base           90 k
 python-meh-gui                                    noarch       0.25.3-1.el7                        base           16 k
 python-nss                                        x86_64       0.16.0-3.el7                        base          266 k
 python-ntplib                                     noarch       0.3.2-1.el7                         base           15 k
 python-pwquality                                  x86_64       1.2.3-5.el7                         base           12 k
 python-pyblock                                    x86_64       0.53-6.el7                          base           72 k
 python-setuptools                                 noarch       0.9.8-7.el7                         base          397 k
 python-six                                        noarch       1.9.0-2.el7                         base           29 k
 python2-blockdev                                  x86_64       2.18-5.el7                          base           61 k
 python2-futures                                   noarch       3.1.1-5.el7                         base           29 k
 python2-pyatspi                                   noarch       2.26.0-3.el7                        base           87 k
 python2-subprocess32                              x86_64       3.2.6-14.el7                        base           47 k
 pytz                                              noarch       2016.10-2.el7                       base           46 k
 qemu-img                                          x86_64       10:1.5.3-175.el7_9.6                updates       705 k
 qemu-kvm                                          x86_64       10:1.5.3-175.el7_9.6                updates       1.9 M
 qemu-kvm-common                                   x86_64       10:1.5.3-175.el7_9.6                updates       441 k
 qt5-qtbase                                        x86_64       5.9.7-5.el7_9                       updates       3.1 M
 qt5-qtbase-common                                 noarch       5.9.7-5.el7_9                       updates        26 k
 qt5-qtbase-gui                                    x86_64       5.9.7-5.el7_9                       updates       5.4 M
 radvd                                             x86_64       2.17-3.el7                          base           94 k
 rdma-core                                         x86_64       22.4-6.el7_9                        updates        51 k
 realmd                                            x86_64       0.16.1-12.el7_9.1                   updates       210 k
 redhat-menus                                      noarch       12.0.2-8.el7                        base          146 k
 rest                                              x86_64       0.8.1-2.el7                         base           63 k
 rsync                                             x86_64       3.1.2-12.el7_9                      updates       408 k
 rtkit                                             x86_64       0.11-10.el7                         base           51 k
 samba-client-libs                                 x86_64       4.10.16-24.el7_9                    updates       5.0 M
 samba-common                                      noarch       4.10.16-24.el7_9                    updates       219 k
 samba-common-libs                                 x86_64       4.10.16-24.el7_9                    updates       183 k
 sane-backends                                     x86_64       1.0.24-12.el7                       base          670 k
 sane-backends-libs                                x86_64       1.0.24-12.el7                       base           96 k
 satyr                                             x86_64       0.13-15.el7                         base          558 k
 sbc                                               x86_64       1.0-5.el7                           base           53 k
 seabios-bin                                       noarch       1.11.0-2.el7                        base          112 k
 seavgabios-bin                                    noarch       1.11.0-2.el7                        base           38 k
 setools-libs                                      x86_64       3.3.8-4.el7                         base          620 k
 setroubleshoot-plugins                            noarch       3.0.67-4.el7                        base          358 k
 setroubleshoot-server                             x86_64       3.2.30-8.el7                        base          390 k
 sgabios-bin                                       noarch       1:0.20110622svn-4.el7               base          7.1 k
 sgpio                                             x86_64       1.2.0.10-13.el7                     base           13 k
 sos                                               noarch       3.9-5.el7.centos.11                 updates       549 k
 sound-theme-freedesktop                           noarch       0.8-3.el7                           base          377 k
 soundtouch                                        x86_64       1.4.0-9.el7                         base           53 k
 sox                                               x86_64       14.4.1-7.el7                        base          398 k
 speech-dispatcher                                 x86_64       0.7.1-15.el7                        base          363 k
 speech-dispatcher-python                          x86_64       0.7.1-15.el7                        base           52 k
 speex                                             x86_64       1.2-0.19.rc1.el7                    base           98 k
 spice-glib                                        x86_64       0.35-5.el7_9.1                      updates       357 k
 spice-gtk3                                        x86_64       0.35-5.el7_9.1                      updates        87 k
 spice-server                                      x86_64       0.14.0-9.el7_9.1                    updates       405 k
 startup-notification                              x86_64       0.12-8.el7                          base           39 k
 systemd-python                                    x86_64       219-78.el7_9.7                      updates       146 k
 taglib                                            x86_64       1.8-8.20130218git.el7               base          310 k
 telepathy-farstream                               x86_64       0.6.0-5.el7                         base           76 k
 telepathy-filesystem                              noarch       0.0.2-6.el7                         base          4.7 k
 telepathy-gabble                                  x86_64       0.18.1-4.el7                        base          630 k
 telepathy-glib                                    x86_64       0.24.1-1.el7                        base          719 k
 telepathy-haze                                    x86_64       0.8.0-1.el7                         base           89 k
 telepathy-logger                                  x86_64       0.8.0-5.el7                         base           98 k
 telepathy-mission-control                         x86_64       1:5.16.3-3.el7                      base          202 k
 telepathy-salut                                   x86_64       0.8.1-6.el7                         base          390 k
 totem-pl-parser                                   x86_64       3.26.1-1.el7                        base          177 k
 tracker                                           x86_64       1.10.5-8.el7                        base          1.4 M
 udisks2                                           x86_64       2.8.4-1.el7                         base          441 k
 unbound-libs                                      x86_64       1.6.6-5.el7_8                       base          406 k
 upower                                            x86_64       0.99.7-1.el7                        base          162 k
 urw-base35-bookman-fonts                          noarch       20170801-10.el7                     base          852 k
 urw-base35-c059-fonts                             noarch       20170801-10.el7                     base          879 k
 urw-base35-d050000l-fonts                         noarch       20170801-10.el7                     base           75 k
 urw-base35-fonts                                  noarch       20170801-10.el7                     base          7.6 k
 urw-base35-fonts-common                           noarch       20170801-10.el7                     base           19 k
 urw-base35-gothic-fonts                           noarch       20170801-10.el7                     base          650 k
 urw-base35-nimbus-mono-ps-fonts                   noarch       20170801-10.el7                     base          796 k
 urw-base35-nimbus-roman-fonts                     noarch       20170801-10.el7                     base          860 k
 urw-base35-nimbus-sans-fonts                      noarch       20170801-10.el7                     base          1.3 M
 urw-base35-p052-fonts                             noarch       20170801-10.el7                     base          978 k
 urw-base35-standard-symbols-ps-fonts              noarch       20170801-10.el7                     base           40 k
 urw-base35-z003-fonts                             noarch       20170801-10.el7                     base          275 k
 usbmuxd                                           x86_64       1.1.0-1.el7                         base           56 k
 usbredir                                          x86_64       0.7.1-3.el7                         base           47 k
 usermode                                          x86_64       1.111-6.el7                         base          193 k
 volume_key-libs                                   x86_64       0.3.9-9.el7                         base          141 k
 vorbis-tools                                      x86_64       1:1.4.0-13.el7                      base          214 k
 vte-profile                                       x86_64       0.52.4-1.el7                        base          7.1 k
 vte291                                            x86_64       0.52.4-1.el7                        base          250 k
 wavpack                                           x86_64       4.60.1-9.el7                        base          131 k
 webkitgtk3                                        x86_64       2.4.11-2.el7                        base           11 M
 webkitgtk4                                        x86_64       2.28.2-3.el7                        updates        28 M
 webkitgtk4-jsc                                    x86_64       2.28.2-3.el7                        updates       5.7 M
 webrtc-audio-processing                           x86_64       0.3-1.el7                           base          286 k
 wodim                                             x86_64       1.1.11-25.el7                       base          320 k
 xcb-util                                          x86_64       0.4.0-2.el7                         base           16 k
 xcb-util-image                                    x86_64       0.4.0-2.el7                         base           15 k
 xcb-util-keysyms                                  x86_64       0.4.0-1.el7                         base           10 k
 xcb-util-renderutil                               x86_64       0.3.9-3.el7                         base           12 k
 xcb-util-wm                                       x86_64       0.4.1-5.el7                         base           25 k
 xdg-desktop-portal                                x86_64       1.0.2-1.el7                         base          248 k
 xdg-user-dirs                                     x86_64       0.15-5.el7                          base           59 k
 xdg-utils                                         noarch       1.1.0-0.17.20120809git.el7          base           70 k
 xml-common                                        noarch       0.6.3-39.el7                        base           26 k
 xmlrpc-c                                          x86_64       1.32.5-1905.svn2451.el7             base          130 k
 xmlrpc-c-client                                   x86_64       1.32.5-1905.svn2451.el7             base           32 k
 xorg-x11-font-utils                               x86_64       1:7.5-21.el7                        base          104 k
 yajl                                              x86_64       2.0.4-4.el7                         base           39 k
 yelp-libs                                         x86_64       2:3.28.1-1.el7                      base          101 k
 yelp-xsl                                          noarch       3.28.0-1.el7                        base          204 k
 zenity                                            x86_64       3.28.1-2.el7_9                      updates       4.0 M

Transaction Summary
========================================================================================================================
Install  88 Packages (+582 Dependent packages)

Total download size: 397 M
Installed size: 1.3 G
Downloading packages:
(1/670): NetworkManager-libreswan-gnome-1.2.4-2.el7.x86_64.rpm                                   |  36 kB  00:00:00     
(2/670): ModemManager-glib-1.6.10-4.el7.x86_64.rpm                                               | 232 kB  00:00:00     
(3/670): NetworkManager-libreswan-1.2.4-2.el7.x86_64.rpm                                         | 112 kB  00:00:00     
(4/670): PackageKit-command-not-found-1.1.10-2.el7.centos.x86_64.rpm                             |  21 kB  00:00:00     
(5/670): PackageKit-1.1.10-2.el7.centos.x86_64.rpm                                               | 587 kB  00:00:00     
(6/670): PackageKit-gtk3-module-1.1.10-2.el7.centos.x86_64.rpm                                   |  12 kB  00:00:00     
(7/670): PackageKit-glib-1.1.10-2.el7.centos.x86_64.rpm                                          | 128 kB  00:00:00     
(8/670): PackageKit-yum-1.1.10-2.el7.centos.x86_64.rpm                                           |  75 kB  00:00:00     
(9/670): abattis-cantarell-fonts-0.0.25-1.el7.noarch.rpm                                         | 149 kB  00:00:00     
(10/670): GConf2-3.2.6-8.el7.x86_64.rpm                                                          | 1.0 MB  00:00:00     
(11/670): abrt-2.1.11-60.el7.centos.x86_64.rpm                                                   | 538 kB  00:00:00     
(12/670): abrt-addon-ccpp-2.1.11-60.el7.centos.x86_64.rpm                                        | 195 kB  00:00:00     
(13/670): abrt-addon-kerneloops-2.1.11-60.el7.centos.x86_64.rpm                                  | 107 kB  00:00:00     
(14/670): NetworkManager-wifi-1.18.8-2.el7_9.x86_64.rpm                                          | 202 kB  00:00:00     
(15/670): abrt-addon-pstoreoops-2.1.11-60.el7.centos.x86_64.rpm                                  |  97 kB  00:00:00     
(16/670): abrt-addon-python-2.1.11-60.el7.centos.x86_64.rpm                                      | 103 kB  00:00:00     
(17/670): abrt-addon-vmcore-2.1.11-60.el7.centos.x86_64.rpm                                      | 107 kB  00:00:00     
(18/670): abrt-dbus-2.1.11-60.el7.centos.x86_64.rpm                                              | 122 kB  00:00:00     
(19/670): abrt-desktop-2.1.11-60.el7.centos.x86_64.rpm                                           |  88 kB  00:00:00     
(20/670): abrt-gui-libs-2.1.11-60.el7.centos.x86_64.rpm                                          |  96 kB  00:00:00     
(21/670): abrt-gui-2.1.11-60.el7.centos.x86_64.rpm                                               | 191 kB  00:00:00     
(22/670): abrt-addon-xorg-2.1.11-60.el7.centos.x86_64.rpm                                        |  98 kB  00:00:00     
(23/670): abrt-libs-2.1.11-60.el7.centos.x86_64.rpm                                              | 110 kB  00:00:00     
(24/670): abrt-python-2.1.11-60.el7.centos.x86_64.rpm                                            | 110 kB  00:00:00     
(25/670): accountsservice-0.6.50-7.el7.x86_64.rpm                                                |  99 kB  00:00:00     
(26/670): accountsservice-libs-0.6.50-7.el7.x86_64.rpm                                           |  81 kB  00:00:00     
(27/670): abrt-retrace-client-2.1.11-60.el7.centos.x86_64.rpm                                    | 123 kB  00:00:00     
(28/670): adobe-mappings-cmap-deprecated-20171205-3.el7.noarch.rpm                               | 114 kB  00:00:00     
(29/670): adwaita-gtk2-theme-3.28-2.el7.x86_64.rpm                                               | 134 kB  00:00:00     
(30/670): adwaita-cursor-theme-3.28.0-1.el7.noarch.rpm                                           | 641 kB  00:00:00     
(31/670): adobe-mappings-pdf-20180407-1.el7.noarch.rpm                                           | 703 kB  00:00:00     
(32/670): adwaita-qt5-1.0-1.el7.x86_64.rpm                                                       | 188 kB  00:00:00     
(33/670): NetworkManager-glib-1.18.8-2.el7_9.x86_64.rpm                                          | 1.5 MB  00:00:01     
(34/670): anaconda-gui-21.48.22.159-1.el7.centos.x86_64.rpm                                      | 512 kB  00:00:00     
(35/670): anaconda-tui-21.48.22.159-1.el7.centos.x86_64.rpm                                      | 292 kB  00:00:00     
(36/670): anaconda-core-21.48.22.159-1.el7.centos.x86_64.rpm                                     | 1.6 MB  00:00:00     
(37/670): adobe-mappings-cmap-20171205-3.el7.noarch.rpm                                          | 2.1 MB  00:00:01     
(38/670): anaconda-widgets-21.48.22.159-1.el7.centos.x86_64.rpm                                  | 220 kB  00:00:00     
(39/670): at-spi2-core-2.28.0-1.el7.x86_64.rpm                                                   | 158 kB  00:00:00     
(40/670): atk-2.28.1-2.el7.x86_64.rpm                                                            | 263 kB  00:00:00     
(41/670): atkmm-2.24.2-1.el7.x86_64.rpm                                                          |  79 kB  00:00:00     
(42/670): audit-libs-python-2.8.5-4.el7.x86_64.rpm                                               |  76 kB  00:00:00     
(43/670): at-spi2-atk-2.26.2-1.el7.x86_64.rpm                                                    |  81 kB  00:00:00     
(44/670): augeas-libs-1.4.0-10.el7.x86_64.rpm                                                    | 357 kB  00:00:00     
(45/670): avahi-0.6.31-20.el7.x86_64.rpm                                                         | 264 kB  00:00:00     
(46/670): avahi-glib-0.6.31-20.el7.x86_64.rpm                                                    |  25 kB  00:00:00     
(47/670): avahi-gobject-0.6.31-20.el7.x86_64.rpm                                                 |  35 kB  00:00:00     
(48/670): avahi-libs-0.6.31-20.el7.x86_64.rpm                                                    |  62 kB  00:00:00     
(49/670): avahi-ui-gtk3-0.6.31-20.el7.x86_64.rpm                                                 |  37 kB  00:00:00     
(50/670): baobab-3.28.0-2.el7.x86_64.rpm                                                         | 393 kB  00:00:00     
(51/670): bluez-5.44-7.el7.x86_64.rpm                                                            | 1.2 MB  00:00:00     
(52/670): bolt-0.7-1.el7.x86_64.rpm                                                              | 149 kB  00:00:00     
(53/670): boost-iostreams-1.53.0-28.el7.x86_64.rpm                                               |  61 kB  00:00:00     
(54/670): boost-random-1.53.0-28.el7.x86_64.rpm                                                  |  39 kB  00:00:00     
(55/670): boost-thread-1.53.0-28.el7.x86_64.rpm                                                  |  58 kB  00:00:00     
(56/670): boost-system-1.53.0-28.el7.x86_64.rpm                                                  |  40 kB  00:00:00     
(57/670): brasero-3.12.2-5.el7_9.1.x86_64.rpm                                                    | 2.6 MB  00:00:00     
(58/670): bridge-utils-1.5-9.el7.x86_64.rpm                                                      |  32 kB  00:00:00     
(59/670): brasero-nautilus-3.12.2-5.el7_9.1.x86_64.rpm                                           |  30 kB  00:00:00     
(60/670): appstream-data-7-20180614.el7.noarch.rpm                                               | 7.2 MB  00:00:02     
(61/670): brlapi-0.6.0-16.el7.x86_64.rpm                                                         | 114 kB  00:00:00     
(62/670): cairo-gobject-1.15.12-4.el7.x86_64.rpm                                                 |  26 kB  00:00:00     
(63/670): cairomm-1.12.0-1.el7.x86_64.rpm                                                        |  59 kB  00:00:00     
(64/670): cdparanoia-10.2-17.el7.x86_64.rpm                                                      |  55 kB  00:00:00     
(65/670): cdparanoia-libs-10.2-17.el7.x86_64.rpm                                                 |  56 kB  00:00:00     
(66/670): cdrdao-1.2.3-20.el7.x86_64.rpm                                                         | 320 kB  00:00:00     
(67/670): cairo-1.15.12-4.el7.x86_64.rpm                                                         | 741 kB  00:00:00     
(68/670): celt051-0.5.1.3-8.el7.x86_64.rpm                                                       |  53 kB  00:00:00     
(69/670): cheese-3.28.0-1.el7.x86_64.rpm                                                         | 162 kB  00:00:00     
(70/670): checkpolicy-2.5-8.el7.x86_64.rpm                                                       | 295 kB  00:00:00     
(71/670): adwaita-icon-theme-3.28.0-1.el7.noarch.rpm                                             |  11 MB  00:00:03     
(72/670): clutter-gst2-2.0.18-1.el7.x86_64.rpm                                                   |  61 kB  00:00:00     
(73/670): clutter-gst3-3.0.26-1.el7.x86_64.rpm                                                   |  75 kB  00:00:00     
(74/670): cheese-libs-3.28.0-1.el7.x86_64.rpm                                                    | 814 kB  00:00:00     
(75/670): brasero-libs-3.12.2-5.el7_9.1.x86_64.rpm                                               | 333 kB  00:00:01     
(76/670): clutter-gtk-1.8.4-1.el7.x86_64.rpm                                                     |  44 kB  00:00:00     
(77/670): color-filesystem-1-13.el7.noarch.rpm                                                   | 5.3 kB  00:00:00     
(78/670): clutter-1.26.2-2.el7.x86_64.rpm                                                        | 1.1 MB  00:00:00     
(79/670): cogl-1.22.2-2.el7.x86_64.rpm                                                           | 462 kB  00:00:00     
(80/670): colord-gtk-0.1.25-4.el7.x86_64.rpm                                                     |  21 kB  00:00:00     
(81/670): colord-1.3.4-2.el7.x86_64.rpm                                                          | 478 kB  00:00:00     
(82/670): compat-cheese314-3.14.2-1.el7.x86_64.rpm                                               |  54 kB  00:00:00     
(83/670): colord-libs-1.3.4-2.el7.x86_64.rpm                                                     | 186 kB  00:00:00     
(84/670): compat-gnome-desktop314-3.14.2-1.el7.x86_64.rpm                                        | 108 kB  00:00:00     
(85/670): compat-libcolord1-1.0.4-1.el7.x86_64.rpm                                               |  96 kB  00:00:00     
(86/670): brltty-4.5-16.el7.x86_64.rpm                                                           | 933 kB  00:00:00     
(87/670): createrepo-0.9.9-28.el7.noarch.rpm                                                     |  94 kB  00:00:00     
(88/670): cryptsetup-python-2.0.3-6.el7.x86_64.rpm                                               |  36 kB  00:00:00     
(89/670): cryptsetup-2.0.3-6.el7.x86_64.rpm                                                      | 154 kB  00:00:00     
(90/670): compat-exiv2-026-0.26-2.el7.x86_64.rpm                                                 | 828 kB  00:00:00     
(91/670): control-center-filesystem-3.28.1-8.el7_9.1.x86_64.rpm                                  |  25 kB  00:00:00     
(92/670): cups-libs-1.6.3-51.el7.x86_64.rpm                                                      | 359 kB  00:00:00     
(93/670): cups-pk-helper-0.2.6-2.el7.x86_64.rpm                                                  |  81 kB  00:00:00     
(94/670): cyrus-sasl-2.1.26-24.el7_9.x86_64.rpm                                                  |  88 kB  00:00:00     
(95/670): cyrus-sasl-gssapi-2.1.26-24.el7_9.x86_64.rpm                                           |  41 kB  00:00:00     
(96/670): cyrus-sasl-md5-2.1.26-24.el7_9.x86_64.rpm                                              |  57 kB  00:00:00     
(97/670): cyrus-sasl-plain-2.1.26-24.el7_9.x86_64.rpm                                            |  39 kB  00:00:00     
(98/670): cyrus-sasl-scram-2.1.26-24.el7_9.x86_64.rpm                                            |  43 kB  00:00:00     
(99/670): dbus-x11-1.10.24-15.el7.x86_64.rpm                                                     |  48 kB  00:00:00     
(100/670): daxctl-libs-65-6.el7_9.x86_64.rpm                                                     |  27 kB  00:00:00     
(101/670): dconf-0.28.0-4.el7.x86_64.rpm                                                         | 106 kB  00:00:00     
(102/670): dejavu-fonts-common-2.33-6.el7.noarch.rpm                                             |  64 kB  00:00:00     
(103/670): desktop-file-utils-0.23-2.el7.x86_64.rpm                                              |  67 kB  00:00:00     
(104/670): device-mapper-multipath-0.4.9-136.el7_9.x86_64.rpm                                    | 148 kB  00:00:00     
(105/670): deltarpm-3.6-3.el7.x86_64.rpm                                                         |  82 kB  00:00:00     
(106/670): dleyna-connector-dbus-0.2.0-2.el7.x86_64.rpm                                          |  20 kB  00:00:00     
(107/670): dleyna-server-0.5.0-3.el7.x86_64.rpm                                                  |  72 kB  00:00:00     
(108/670): dleyna-core-0.5.0-1.el7.x86_64.rpm                                                    |  26 kB  00:00:00     
(109/670): dmraid-1.0.0.rc16-28.el7.x86_64.rpm                                                   | 151 kB  00:00:00     
(110/670): device-mapper-multipath-libs-0.4.9-136.el7_9.x86_64.rpm                               | 268 kB  00:00:00     
(111/670): dmraid-events-1.0.0.rc16-28.el7.x86_64.rpm                                            |  21 kB  00:00:00     
(112/670): dotconf-1.3-8.el7.x86_64.rpm                                                          |  27 kB  00:00:00     
(113/670): dejavu-sans-fonts-2.33-6.el7.noarch.rpm                                               | 1.4 MB  00:00:00     
(114/670): elfutils-0.176-5.el7.x86_64.rpm                                                       | 308 kB  00:00:00     
(115/670): dnsmasq-2.76-17.el7_9.3.x86_64.rpm                                                    | 281 kB  00:00:00     
(116/670): dvd+rw-tools-7.1-15.el7.x86_64.rpm                                                    | 132 kB  00:00:00     
(117/670): emacs-filesystem-24.3-23.el7_9.1.noarch.rpm                                           |  58 kB  00:00:00     
(118/670): enchant-1.6.0-8.el7.x86_64.rpm                                                        |  55 kB  00:00:00     
(119/670): espeak-1.47.11-4.el7.x86_64.rpm                                                       | 1.1 MB  00:00:00     
(120/670): evince-libs-3.28.2-10.el7.x86_64.rpm                                                  | 391 kB  00:00:00     
(121/670): evince-nautilus-3.28.2-10.el7.x86_64.rpm                                              |  42 kB  00:00:00     
(122/670): evince-3.28.2-10.el7.x86_64.rpm                                                       | 2.3 MB  00:00:01     
(123/670): control-center-3.28.1-8.el7_9.1.x86_64.rpm                                            | 4.8 MB  00:00:02     
(124/670): exempi-2.2.0-9.el7.x86_64.rpm                                                         | 414 kB  00:00:00     
(125/670): farstream-0.1.2-8.el7.x86_64.rpm                                                      | 230 kB  00:00:00     
(126/670): farstream02-0.2.3-3.el7.x86_64.rpm                                                    | 227 kB  00:00:00     
(127/670): fcoe-utils-1.0.32-2.el7_6.x86_64.rpm                                                  | 120 kB  00:00:00     
(128/670): empathy-3.12.13-1.el7.x86_64.rpm                                                      | 4.0 MB  00:00:01     
(129/670): festival-freebsoft-utils-0.10-7.el7.noarch.rpm                                        |  36 kB  00:00:00     
(130/670): evolution-data-server-langpacks-3.28.5-5.el7_9.1.noarch.rpm                           | 1.4 MB  00:00:00     
(131/670): festival-lib-1.96-28.el7.x86_64.rpm                                                   | 458 kB  00:00:00     
(132/670): festival-1.96-28.el7.x86_64.rpm                                                       | 1.3 MB  00:00:00     
(133/670): festival-speechtools-libs-1.2.96-28.el7.x86_64.rpm                                    | 1.0 MB  00:00:00     
(134/670): festvox-slt-arctic-hts-0.20061229-28.el7.noarch.rpm                                   | 1.0 MB  00:00:00     
(135/670): file-roller-nautilus-3.28.1-2.el7.x86_64.rpm                                          |  29 kB  00:00:00     
(136/670): firewall-config-0.6.3-13.el7_9.noarch.rpm                                             | 137 kB  00:00:00     
(137/670): fftw-libs-double-3.3.3-8.el7.x86_64.rpm                                               | 759 kB  00:00:00     
(138/670): firstboot-19.12-1.el7.x86_64.rpm                                                      | 111 kB  00:00:00     
(139/670): flac-libs-1.3.0-5.el7_1.x86_64.rpm                                                    | 169 kB  00:00:00     
(140/670): eog-3.28.3-1.el7.x86_64.rpm                                                           | 4.7 MB  00:00:02     
(141/670): file-roller-3.28.1-2.el7.x86_64.rpm                                                   | 1.3 MB  00:00:00     
(142/670): evolution-data-server-3.28.5-5.el7_9.1.x86_64.rpm                                     | 2.1 MB  00:00:01     
(143/670): flatpak-1.0.9-12.el7_9.x86_64.rpm                                                     | 958 kB  00:00:00     
(144/670): folks-0.11.4-1.el7.x86_64.rpm                                                         | 613 kB  00:00:00     
(145/670): fontpackages-filesystem-1.44-8.el7.noarch.rpm                                         | 9.9 kB  00:00:00     
(146/670): fprintd-pam-0.8.1-2.el7.x86_64.rpm                                                    |  16 kB  00:00:00     
(147/670): fprintd-0.8.1-2.el7.x86_64.rpm                                                        |  89 kB  00:00:00     
(148/670): fontconfig-2.13.0-4.3.el7.x86_64.rpm                                                  | 254 kB  00:00:00     
(149/670): flatpak-libs-1.0.9-12.el7_9.x86_64.rpm                                                | 597 kB  00:00:00     
(150/670): fribidi-1.0.2-1.el7_7.1.x86_64.rpm                                                    |  79 kB  00:00:00     
(151/670): fuse-2.9.2-11.el7.x86_64.rpm                                                          |  86 kB  00:00:00     
(152/670): frei0r-plugins-1.3-13.el7.x86_64.rpm                                                  | 458 kB  00:00:00     
(153/670): fwupdate-efi-12-6.el7.centos.x86_64.rpm                                               |  58 kB  00:00:00     
(154/670): freerdp-libs-2.1.1-5.el7_9.x86_64.rpm                                                 | 855 kB  00:00:00     
(155/670): fwupdate-libs-12-6.el7.centos.x86_64.rpm                                              |  27 kB  00:00:00     
(156/670): fros-1.0-5.el7.noarch.rpm                                                             |  22 kB  00:00:00     
(157/670): gd-2.0.35-27.el7_9.x86_64.rpm                                                         | 146 kB  00:00:00     
(158/670): fwupd-1.0.8-5.el7.x86_64.rpm                                                          | 585 kB  00:00:00     
(159/670): gdisk-0.8.10-3.el7.x86_64.rpm                                                         | 190 kB  00:00:00     
(160/670): gcr-3.28.0-1.el7.x86_64.rpm                                                           | 677 kB  00:00:00     
(161/670): gdm-3.28.2-26.el7.x86_64.rpm                                                          | 526 kB  00:00:00     
(162/670): gdk-pixbuf2-2.36.12-3.el7.x86_64.rpm                                                  | 570 kB  00:00:00     
(163/670): genisoimage-1.1.11-25.el7.x86_64.rpm                                                  | 299 kB  00:00:00     
(164/670): geoclue2-2.4.8-1.el7.x86_64.rpm                                                       | 106 kB  00:00:00     
(165/670): gedit-3.28.1-3.el7.x86_64.rpm                                                         | 2.5 MB  00:00:00     
(166/670): gavl-1.4.0-4.el7.x86_64.rpm                                                           | 2.6 MB  00:00:01     
(167/670): gdb-7.6.1-120.el7.x86_64.rpm                                                          | 2.4 MB  00:00:01     
(168/670): geocode-glib-3.26.0-3.el7.x86_64.rpm                                                  |  64 kB  00:00:00     
(169/670): glib-networking-2.56.1-1.el7.x86_64.rpm                                               | 145 kB  00:00:00     
(170/670): glade-libs-3.22.1-1.el7.x86_64.rpm                                                    | 685 kB  00:00:00     
(171/670): geoclue2-libs-2.4.8-1.el7.x86_64.rpm                                                  |  43 kB  00:00:00     
(172/670): gjs-1.52.5-1.el7_6.x86_64.rpm                                                         | 329 kB  00:00:00     
(173/670): glibmm24-2.56.0-1.el7.x86_64.rpm                                                      | 534 kB  00:00:00     
(174/670): glusterfs-6.0-61.el7.x86_64.rpm                                                       | 586 kB  00:00:00     
(175/670): glusterfs-cli-6.0-61.el7.x86_64.rpm                                                   | 179 kB  00:00:00     
(176/670): glusterfs-api-6.0-61.el7.x86_64.rpm                                                   |  89 kB  00:00:00     
(177/670): glx-utils-8.3.0-10.el7.x86_64.rpm                                                     |  34 kB  00:00:00     
(178/670): gnome-bluetooth-3.28.2-1.el7.x86_64.rpm                                               |  51 kB  00:00:00     
(179/670): gnome-abrt-0.3.4-9.el7.x86_64.rpm                                                     | 216 kB  00:00:00     
(180/670): glusterfs-libs-6.0-61.el7.x86_64.rpm                                                  | 389 kB  00:00:00     
(181/670): glusterfs-client-xlators-6.0-61.el7.x86_64.rpm                                        | 786 kB  00:00:00     
(182/670): flite-1.3-22.el7.x86_64.rpm                                                           | 6.1 MB  00:00:02     
(183/670): gnome-bluetooth-libs-3.28.2-1.el7.x86_64.rpm                                          | 308 kB  00:00:00     
(184/670): gnome-classic-session-3.28.1-17.el7_9.noarch.rpm                                      |  42 kB  00:00:00     
(185/670): gnome-clocks-3.28.0-1.el7.x86_64.rpm                                                  | 413 kB  00:00:00     
(186/670): gnome-contacts-3.28.2-1.el7.x86_64.rpm                                                | 454 kB  00:00:00     
(187/670): gnome-desktop3-3.28.2-2.el7.x86_64.rpm                                                | 594 kB  00:00:00     
(188/670): gnome-calculator-3.28.2-1.el7.x86_64.rpm                                              | 1.1 MB  00:00:00     
(189/670): gnome-dictionary-3.26.1-2.el7.x86_64.rpm                                              | 642 kB  00:00:00     
(190/670): gnome-font-viewer-3.28.0-1.el7.x86_64.rpm                                             | 152 kB  00:00:00     
(191/670): gnome-boxes-3.28.5-4.el7.x86_64.rpm                                                   | 1.1 MB  00:00:00     
(192/670): gnome-disk-utility-3.28.3-1.el7.x86_64.rpm                                            | 1.1 MB  00:00:00     
(193/670): gnome-color-manager-3.28.0-1.el7.x86_64.rpm                                           | 1.6 MB  00:00:00     
(194/670): gnome-icon-theme-symbolic-3.12.0-2.el7.noarch.rpm                                     | 201 kB  00:00:00     
(195/670): gnome-initial-setup-3.28.0-2.el7_9.1.x86_64.rpm                                       | 760 kB  00:00:00     
(196/670): gnome-icon-theme-extras-3.12.0-1.el7.noarch.rpm                                       | 847 kB  00:00:00     
(197/670): gnome-keyring-pam-3.28.2-1.el7.x86_64.rpm                                             |  39 kB  00:00:00     
(198/670): gnome-keyring-3.28.2-1.el7.x86_64.rpm                                                 | 908 kB  00:00:00     
(199/670): gnome-packagekit-3.28.0-1.el7.x86_64.rpm                                              | 7.5 kB  00:00:00     
(200/670): gnome-menus-3.13.3-3.el7.x86_64.rpm                                                   | 180 kB  00:00:00     
(201/670): gnome-packagekit-common-3.28.0-1.el7.x86_64.rpm                                       | 1.1 MB  00:00:00     
(202/670): gnome-online-accounts-3.28.2-1.el7.x86_64.rpm                                         | 1.0 MB  00:00:00     
(203/670): gnome-packagekit-installer-3.28.0-1.el7.x86_64.rpm                                    |  78 kB  00:00:00     
(204/670): gnome-packagekit-updater-3.28.0-1.el7.x86_64.rpm                                      |  74 kB  00:00:00     
(205/670): gnome-session-xsession-3.28.1-8.el7.x86_64.rpm                                        | 6.6 kB  00:00:00     
(206/670): gnome-screenshot-3.26.0-1.el7.x86_64.rpm                                              | 196 kB  00:00:00     
(207/670): gnome-session-3.28.1-8.el7.x86_64.rpm                                                 | 400 kB  00:00:00     
(208/670): gnome-settings-daemon-3.28.1-11.el7_9.x86_64.rpm                                      | 1.0 MB  00:00:00     
(209/670): gnome-shell-extension-alternate-tab-3.28.1-17.el7_9.noarch.rpm                        |  21 kB  00:00:00     
(210/670): gnome-shell-extension-apps-menu-3.28.1-17.el7_9.noarch.rpm                            |  26 kB  00:00:00     
(211/670): gnome-shell-extension-common-3.28.1-17.el7_9.noarch.rpm                               | 149 kB  00:00:00     
(212/670): gnome-shell-extension-horizontal-workspaces-3.28.1-17.el7_9.noarch.rpm                |  20 kB  00:00:00     
(213/670): gnome-shell-extension-launch-new-instance-3.28.1-17.el7_9.noarch.rpm                  |  20 kB  00:00:00     
(214/670): gnome-shell-extension-places-menu-3.28.1-17.el7_9.noarch.rpm                          |  25 kB  00:00:00     
(215/670): gnome-shell-extension-top-icons-3.28.1-17.el7_9.noarch.rpm                            |  21 kB  00:00:00     
(216/670): gnome-shell-extension-user-theme-3.28.1-17.el7_9.noarch.rpm                           |  21 kB  00:00:00     
(217/670): gnome-shell-extension-window-list-3.28.1-17.el7_9.noarch.rpm                          |  34 kB  00:00:00     
(218/670): gnome-system-log-3.9.90-3.el7.x86_64.rpm                                              | 982 kB  00:00:00     
(219/670): gnome-system-monitor-3.28.2-1.el7.x86_64.rpm                                          | 748 kB  00:00:00     
(220/670): gnome-icon-theme-3.12.0-1.el7.noarch.rpm                                              | 9.7 MB  00:00:03     
(221/670): gnome-getting-started-docs-3.28.2-1.el7.noarch.rpm                                    |  10 MB  00:00:03     
(222/670): gnome-terminal-nautilus-3.28.2-3.el7.x86_64.rpm                                       |  36 kB  00:00:00     
(223/670): gnome-tweak-tool-3.28.1-7.el7.noarch.rpm                                              | 330 kB  00:00:00     
(224/670): gnome-terminal-3.28.2-3.el7.x86_64.rpm                                                | 1.3 MB  00:00:00     
(225/670): gnome-software-3.28.2-3.el7.x86_64.rpm                                                | 3.7 MB  00:00:01     
(226/670): gnome-video-effects-0.4.3-1.el7.noarch.rpm                                            |  74 kB  00:00:00     
(227/670): gom-0.4-1.el7.x86_64.rpm                                                              |  59 kB  00:00:00     
(228/670): gnome-themes-standard-3.28-2.el7.x86_64.rpm                                           | 2.8 MB  00:00:01     
(229/670): gperftools-libs-2.6.1-1.el7.x86_64.rpm                                                | 272 kB  00:00:00     
(230/670): graphite2-1.3.10-1.el7_3.x86_64.rpm                                                   | 115 kB  00:00:00     
(231/670): grilo-0.3.6-1.el7.x86_64.rpm                                                          | 210 kB  00:00:00     
(232/670): grilo-plugins-0.3.7-1.el7.x86_64.rpm                                                  | 964 kB  00:00:00     
(233/670): gnome-weather-3.26.0-1.el7.noarch.rpm                                                 | 5.0 MB  00:00:02     
(234/670): gsettings-desktop-schemas-3.28.0-3.el7.x86_64.rpm                                     | 606 kB  00:00:00     
(235/670): gsm-1.0.13-11.el7.x86_64.rpm                                                          |  30 kB  00:00:00     
(236/670): gsound-1.0.2-2.el7.x86_64.rpm                                                         |  29 kB  00:00:00     
(237/670): gssdp-1.0.2-1.el7.x86_64.rpm                                                          |  49 kB  00:00:00     
(238/670): gspell-1.6.1-1.el7.x86_64.rpm                                                         |  91 kB  00:00:00     
(239/670): google-noto-emoji-color-fonts-20180508-4.el7.noarch.rpm                               | 6.4 MB  00:00:02     
(240/670): gstreamer-0.10.36-7.el7.x86_64.rpm                                                    | 958 kB  00:00:00     
(241/670): gstreamer-plugins-bad-free-0.10.23-23.el7.x86_64.rpm                                  | 1.4 MB  00:00:00     
(242/670): gstreamer-plugins-base-0.10.36-10.el7.x86_64.rpm                                      | 1.2 MB  00:00:00     
(243/670): gstreamer-tools-0.10.36-7.el7.x86_64.rpm                                              |  27 kB  00:00:00     
(244/670): gstreamer-plugins-good-0.10.31-13.el7.x86_64.rpm                                      | 1.5 MB  00:00:00     
(245/670): gstreamer1-1.10.4-2.el7.x86_64.rpm                                                    | 1.2 MB  00:00:00     
(246/670): gstreamer1-plugins-base-1.10.4-2.el7.x86_64.rpm                                       | 1.4 MB  00:00:00     
(247/670): gstreamer1-plugins-ugly-free-1.10.4-3.el7.x86_64.rpm                                  |  80 kB  00:00:00     
(248/670): gstreamer1-plugins-bad-free-1.10.4-3.el7.x86_64.rpm                                   | 1.7 MB  00:00:00     
(249/670): gtk-update-icon-cache-3.22.30-8.el7_9.x86_64.rpm                                      |  27 kB  00:00:00     
(250/670): gtk-vnc2-0.7.0-3.el7.x86_64.rpm                                                       |  41 kB  00:00:00     
(251/670): gstreamer1-plugins-good-1.10.4-2.el7.x86_64.rpm                                       | 2.0 MB  00:00:01     
(252/670): gtkmm30-3.22.2-1.el7.x86_64.rpm                                                       | 925 kB  00:00:00     
(253/670): gtksourceview3-3.24.8-2.el7.x86_64.rpm                                                | 585 kB  00:00:00     
(254/670): gtk2-2.24.31-1.el7.x86_64.rpm                                                         | 3.4 MB  00:00:01     
(255/670): gucharmap-10.0.4-1.el7.x86_64.rpm                                                     | 1.2 MB  00:00:01     
(256/670): gucharmap-libs-10.0.4-1.el7.x86_64.rpm                                                | 1.1 MB  00:00:01     
(257/670): gnome-user-docs-3.28.2-1.el7.noarch.rpm                                               |  16 MB  00:00:07     
(258/670): gtk3-3.22.30-8.el7_9.x86_64.rpm                                                       | 4.4 MB  00:00:03     
(259/670): gupnp-av-0.12.10-1.el7.x86_64.rpm                                                     |  88 kB  00:00:00     
(260/670): gupnp-igd-0.2.5-2.el7.x86_64.rpm                                                      |  29 kB  00:00:00     
(261/670): gupnp-1.0.2-6.el7_9.x86_64.rpm                                                        |  94 kB  00:00:00     
(262/670): gupnp-dlna-0.10.5-1.el7.x86_64.rpm                                                    |  84 kB  00:00:00     
(263/670): gvfs-1.36.2-7.el7_9.x86_64.rpm                                                        | 354 kB  00:00:00     
(264/670): gvfs-afc-1.36.2-7.el7_9.x86_64.rpm                                                    |  74 kB  00:00:00     
(265/670): gvfs-afp-1.36.2-7.el7_9.x86_64.rpm                                                    |  88 kB  00:00:00     
(266/670): gvfs-archive-1.36.2-7.el7_9.x86_64.rpm                                                |  42 kB  00:00:00     
(267/670): gvfs-client-1.36.2-7.el7_9.x86_64.rpm                                                 | 799 kB  00:00:00     
(268/670): gnome-shell-3.28.3-34.el7_9.x86_64.rpm                                                | 2.1 MB  00:00:10     
(269/670): gvfs-fuse-1.36.2-7.el7_9.x86_64.rpm                                                   |  46 kB  00:00:00     
(270/670): gvnc-0.7.0-3.el7.x86_64.rpm                                                           |  94 kB  00:00:00     
(271/670): gvfs-goa-1.36.2-7.el7_9.x86_64.rpm                                                    |  78 kB  00:00:00     
(272/670): harfbuzz-icu-1.7.5-2.el7.x86_64.rpm                                                   |  12 kB  00:00:00     
(273/670): harfbuzz-1.7.5-2.el7.x86_64.rpm                                                       | 267 kB  00:00:00     
(274/670): gvfs-mtp-1.36.2-7.el7_9.x86_64.rpm                                                    |  78 kB  00:00:00     
(275/670): hicolor-icon-theme-0.12-7.el7.noarch.rpm                                              |  42 kB  00:00:00     
(276/670): gvfs-smb-1.36.2-7.el7_9.x86_64.rpm                                                    |  60 kB  00:00:00     
(277/670): hplip-common-3.15.9-5.el7.x86_64.rpm                                                  |  89 kB  00:00:00     
(278/670): highcontrast-qt5-0.1-2.el7.x86_64.rpm                                                 | 179 kB  00:00:00     
(279/670): gvfs-gphoto2-1.36.2-7.el7_9.x86_64.rpm                                                |  78 kB  00:00:00     
(280/670): hyphen-2.8.6-5.el7.x86_64.rpm                                                         |  26 kB  00:00:00     
(281/670): hunspell-en-US-0.20121024-6.el7.noarch.rpm                                            | 190 kB  00:00:00     
(282/670): hplip-libs-3.15.9-5.el7.x86_64.rpm                                                    | 176 kB  00:00:00     
(283/670): ibus-gtk2-1.5.17-12.el7_9.x86_64.rpm                                                  |  45 kB  00:00:00     
(284/670): ibus-setup-1.5.17-12.el7_9.noarch.rpm                                                 |  80 kB  00:00:00     
(285/670): hunspell-1.3.2-16.el7.x86_64.rpm                                                      | 223 kB  00:00:00     
(286/670): icedax-1.1.11-25.el7.x86_64.rpm                                                       | 138 kB  00:00:00     
(287/670): ibus-gtk3-1.5.17-12.el7_9.x86_64.rpm                                                  |  46 kB  00:00:00     
(288/670): initial-setup-0.3.9.45-1.el7.centos.x86_64.rpm                                        |  90 kB  00:00:00     
(289/670): initial-setup-gui-0.3.9.45-1.el7.centos.x86_64.rpm                                    |  28 kB  00:00:00     
(290/670): iscsi-initiator-utils-iscsiuio-6.2.0.874-22.el7_9.x86_64.rpm                          |  94 kB  00:00:00     
(291/670): ibus-libs-1.5.17-12.el7_9.x86_64.rpm                                                  | 228 kB  00:00:00     
(292/670): isomd5sum-1.0.10-5.el7.x86_64.rpm                                                     |  27 kB  00:00:00     
(293/670): iscsi-initiator-utils-6.2.0.874-22.el7_9.x86_64.rpm                                   | 423 kB  00:00:00     
(294/670): jasper-libs-1.900.1-33.el7.x86_64.rpm                                                 | 150 kB  00:00:00     
(295/670): keybinder3-0.3.0-1.el7.x86_64.rpm                                                     |  14 kB  00:00:00     
(296/670): langtable-0.0.31-4.el7.noarch.rpm                                                     |  32 kB  00:00:00     
(297/670): ipxe-roms-qemu-20180825-3.git133f4c.el7.noarch.rpm                                    | 802 kB  00:00:00     
(298/670): json-glib-1.4.2-2.el7.x86_64.rpm                                                      | 134 kB  00:00:00     
(299/670): langtable-python-0.0.31-4.el7.noarch.rpm                                              |  28 kB  00:00:00     
(300/670): lcms2-2.6-3.el7.x86_64.rpm                                                            | 150 kB  00:00:00     
(301/670): libXcomposite-0.4.4-4.1.el7.x86_64.rpm                                                |  22 kB  00:00:00     
(302/670): langtable-data-0.0.31-4.el7.noarch.rpm                                                | 620 kB  00:00:00     
(303/670): libXft-2.3.2-2.el7.x86_64.rpm                                                         |  58 kB  00:00:00     
(304/670): libXres-1.2.0-1.el7.x86_64.rpm                                                        |  15 kB  00:00:00     
(305/670): libXv-1.0.11-1.el7.x86_64.rpm                                                         |  18 kB  00:00:00     
(306/670): libXpm-3.5.12-2.el7_9.x86_64.rpm                                                      |  56 kB  00:00:00     
(307/670): libao-1.1.0-8.el7.x86_64.rpm                                                          |  72 kB  00:00:00     
(308/670): ldns-1.6.16-10.el7.x86_64.rpm                                                         | 476 kB  00:00:00     
(309/670): libasyncns-0.8-7.el7.x86_64.rpm                                                       |  26 kB  00:00:00     
(310/670): libavc1394-0.5.3-14.el7.x86_64.rpm                                                    |  50 kB  00:00:00     
(311/670): libatasmart-0.19-6.el7.x86_64.rpm                                                     |  43 kB  00:00:00     
(312/670): libappstream-glib-0.7.8-2.el7.x86_64.rpm                                              | 286 kB  00:00:00     
(313/670): libblockdev-2.18-5.el7.x86_64.rpm                                                     | 119 kB  00:00:00     
(314/670): libblockdev-fs-2.18-5.el7.x86_64.rpm                                                  |  66 kB  00:00:00     
(315/670): libblockdev-loop-2.18-5.el7.x86_64.rpm                                                |  51 kB  00:00:00     
(316/670): libblockdev-crypto-2.18-5.el7.x86_64.rpm                                              |  60 kB  00:00:00     
(317/670): libblockdev-nvdimm-2.18-5.el7.x86_64.rpm                                              |  53 kB  00:00:00     
(318/670): libblockdev-mdraid-2.18-5.el7.x86_64.rpm                                              |  57 kB  00:00:00     
(319/670): libblockdev-swap-2.18-5.el7.x86_64.rpm                                                |  52 kB  00:00:00     
(320/670): libblockdev-part-2.18-5.el7.x86_64.rpm                                                |  60 kB  00:00:00     
(321/670): libblockdev-utils-2.18-5.el7.x86_64.rpm                                               |  58 kB  00:00:00     
(322/670): libbluray-0.2.3-6.el7.x86_64.rpm                                                      | 135 kB  00:00:00     
(323/670): libbytesize-1.2-1.el7.x86_64.rpm                                                      |  52 kB  00:00:00     
(324/670): libcacard-2.7.0-1.el7.x86_64.rpm                                                      |  35 kB  00:00:00     
(325/670): libburn-1.2.8-4.el7.x86_64.rpm                                                        | 149 kB  00:00:00     
(326/670): libcanberra-gtk2-0.30-9.el7.x86_64.rpm                                                |  25 kB  00:00:00     
(327/670): libcanberra-0.30-9.el7.x86_64.rpm                                                     |  82 kB  00:00:00     
(328/670): libcdio-paranoia-10.2+0.90-11.el7.x86_64.rpm                                          |  70 kB  00:00:00     
(329/670): iso-codes-3.46-2.el7.noarch.rpm                                                       | 2.7 MB  00:00:01     
(330/670): libcgroup-0.41-21.el7.x86_64.rpm                                                      |  66 kB  00:00:00     
(331/670): libcdio-0.92-3.el7.x86_64.rpm                                                         | 236 kB  00:00:00     
(332/670): libchamplain-0.12.16-2.el7.x86_64.rpm                                                 | 135 kB  00:00:00     
(333/670): libchamplain-gtk-0.12.16-2.el7.x86_64.rpm                                             |  23 kB  00:00:00     
(334/670): libconfig-1.4.9-5.el7.x86_64.rpm                                                      |  59 kB  00:00:00     
(335/670): libdmapsharing-2.9.37-1.el7.x86_64.rpm                                                | 110 kB  00:00:00     
(336/670): libdvdnav-5.0.3-1.el7.x86_64.rpm                                                      |  48 kB  00:00:00     
(337/670): libdv-1.0.0-17.el7.x86_64.rpm                                                         |  78 kB  00:00:00     
(338/670): libdvdread-5.0.3-3.el7.x86_64.rpm                                                     |  66 kB  00:00:00     
(339/670): libevdev-1.5.6-1.el7.x86_64.rpm                                                       |  34 kB  00:00:00     
(340/670): libcanberra-gtk3-0.30-9.el7.x86_64.rpm                                                |  31 kB  00:00:00     
(341/670): libepoxy-1.5.2-1.el7.x86_64.rpm                                                       | 211 kB  00:00:00     
(342/670): libfprint-0.8.2-1.el7.x86_64.rpm                                                      | 200 kB  00:00:00     
(343/670): libgdither-0.6-8.el7.x86_64.rpm                                                       |  20 kB  00:00:00     
(344/670): libgcab1-0.7-4.el7_4.x86_64.rpm                                                       |  66 kB  00:00:00     
(345/670): libgdata-0.17.9-1.el7.x86_64.rpm                                                      | 439 kB  00:00:00     
(346/670): libglade2-2.6.4-11.el7.x86_64.rpm                                                     |  64 kB  00:00:00     
(347/670): libgee-0.20.1-1.el7.x86_64.rpm                                                        | 272 kB  00:00:00     
(348/670): libglvnd-egl-1.0.1-0.8.git5baa1e5.el7.x86_64.rpm                                      |  44 kB  00:00:00     
(349/670): libexif-0.6.22-2.el7_9.x86_64.rpm                                                     | 423 kB  00:00:00     
(350/670): libglvnd-gles-1.0.1-0.8.git5baa1e5.el7.x86_64.rpm                                     |  34 kB  00:00:00     
(351/670): libgovirt-0.3.4-5.el7.x86_64.rpm                                                      |  75 kB  00:00:00     
(352/670): libgnomekbd-3.26.0-3.el7.x86_64.rpm                                                   | 161 kB  00:00:00     
(353/670): libgsf-1.14.26-7.el7.x86_64.rpm                                                       | 166 kB  00:00:00     
(354/670): libgtop2-2.38.0-3.el7.x86_64.rpm                                                      | 134 kB  00:00:00     
(355/670): ibus-1.5.17-12.el7_9.x86_64.rpm                                                       | 4.8 MB  00:00:02     
(356/670): libgusb-0.2.9-1.el7.x86_64.rpm                                                        |  40 kB  00:00:00     
(357/670): libgxps-0.3.0-4.el7.x86_64.rpm                                                        |  70 kB  00:00:00     
(358/670): libgudev1-219-78.el7_9.7.x86_64.rpm                                                   | 110 kB  00:00:00     
(359/670): libical-3.0.3-2.el7.x86_64.rpm                                                        | 265 kB  00:00:00     
(360/670): libibverbs-22.4-6.el7_9.x86_64.rpm                                                    | 269 kB  00:00:00     
(361/670): libgphoto2-2.5.15-3.el7.x86_64.rpm                                                    | 1.4 MB  00:00:00     
(362/670): libiec61883-1.2.0-10.el7.x86_64.rpm                                                   |  37 kB  00:00:00     
(363/670): libieee1284-0.2.11-15.el7.x86_64.rpm                                                  |  39 kB  00:00:00     
(364/670): libimobiledevice-1.2.0-1.el7.x86_64.rpm                                               |  70 kB  00:00:00     
(365/670): libinput-1.10.7-2.el7.x86_64.rpm                                                      | 147 kB  00:00:00     
(366/670): libiptcdata-1.0.4-11.el7.x86_64.rpm                                                   |  56 kB  00:00:00     
(367/670): libiscsi-1.9.0-7.el7.x86_64.rpm                                                       |  60 kB  00:00:00     
(368/670): libisofs-1.2.8-4.el7.x86_64.rpm                                                       | 172 kB  00:00:00     
(369/670): libldb-1.5.4-2.el7.x86_64.rpm                                                         | 149 kB  00:00:00     
(370/670): liblouis-python-2.5.2-12.el7_4.noarch.rpm                                             |  12 kB  00:00:00     
(371/670): libmediaart-1.9.4-1.el7.x86_64.rpm                                                    |  38 kB  00:00:00     
(372/670): libmodman-2.0.1-8.el7.x86_64.rpm                                                      |  28 kB  00:00:00     
(373/670): libmpcdec-1.2.6-12.el7.x86_64.rpm                                                     |  28 kB  00:00:00     
(374/670): libmtp-1.1.14-1.el7.x86_64.rpm                                                        | 174 kB  00:00:00     
(375/670): libgweather-3.28.2-4.el7_9.x86_64.rpm                                                 | 3.1 MB  00:00:01     
(376/670): libmusicbrainz5-5.0.1-9.el7.x86_64.rpm                                                | 148 kB  00:00:00     
(377/670): liblouis-2.5.2-12.el7_4.x86_64.rpm                                                    | 1.2 MB  00:00:00     
(378/670): libnl-1.1.4-3.el7.x86_64.rpm                                                          | 128 kB  00:00:00     
(379/670): libnice-0.1.3-4.el7.x86_64.rpm                                                        | 128 kB  00:00:00     
(380/670): libnotify-0.7.7-1.el7.x86_64.rpm                                                      |  39 kB  00:00:00     
(381/670): libnm-gtk-1.8.6-2.el7.x86_64.rpm                                                      |  91 kB  00:00:00     
(382/670): liboauth-0.9.7-4.el7.x86_64.rpm                                                       |  22 kB  00:00:00     
(383/670): libnma-1.8.6-2.el7.x86_64.rpm                                                         |  98 kB  00:00:00     
(384/670): libogg-1.3.0-7.el7.x86_64.rpm                                                         |  24 kB  00:00:00     
(385/670): libofa-0.9.3-24.el7.x86_64.rpm                                                        |  61 kB  00:00:00     
(386/670): libpaper-1.1.24-9.el7.x86_64.rpm                                                      |  37 kB  00:00:00     
(387/670): libosinfo-1.1.0-5.el7.x86_64.rpm                                                      | 230 kB  00:00:00     
(388/670): libpeas-1.22.0-1.el7.x86_64.rpm                                                       | 113 kB  00:00:00     
(389/670): libpcap-1.5.3-13.el7_9.x86_64.rpm                                                     | 139 kB  00:00:00     
(390/670): libpeas-loader-python-1.22.0-1.el7.x86_64.rpm                                         |  20 kB  00:00:00     
(391/670): libpeas-gtk-1.22.0-1.el7.x86_64.rpm                                                   |  29 kB  00:00:00     
(392/670): libplist-1.12-3.el7.x86_64.rpm                                                        |  58 kB  00:00:00     
(393/670): libproxy-mozjs-0.4.11-11.el7.x86_64.rpm                                               |  17 kB  00:00:00     
(394/670): libproxy-0.4.11-11.el7.x86_64.rpm                                                     |  64 kB  00:00:00     
(395/670): libraw1394-2.1.0-2.el7.x86_64.rpm                                                     |  63 kB  00:00:00     
(396/670): libgs-9.25-5.el7.x86_64.rpm                                                           | 4.6 MB  00:00:02     
(397/670): librdmacm-22.4-6.el7_9.x86_64.rpm                                                     |  64 kB  00:00:00     
(398/670): libreport-2.1.11-53.el7.centos.x86_64.rpm                                             | 459 kB  00:00:00     
(399/670): libreport-anaconda-2.1.11-53.el7.centos.x86_64.rpm                                    |  51 kB  00:00:00     
(400/670): libreport-centos-2.1.11-53.el7.centos.x86_64.rpm                                      |  51 kB  00:00:00     
(401/670): libreport-cli-2.1.11-53.el7.centos.x86_64.rpm                                         |  53 kB  00:00:00     
(402/670): libreport-filesystem-2.1.11-53.el7.centos.x86_64.rpm                                  |  41 kB  00:00:00     
(403/670): libreport-gtk-2.1.11-53.el7.centos.x86_64.rpm                                         | 101 kB  00:00:00     
(404/670): libreport-plugin-bugzilla-2.1.11-53.el7.centos.x86_64.rpm                             |  89 kB  00:00:00     
(405/670): librados2-10.2.5-4.el7.x86_64.rpm                                                     | 1.8 MB  00:00:01     
(406/670): libreport-plugin-mantisbt-2.1.11-53.el7.centos.x86_64.rpm                             |  73 kB  00:00:00     
(407/670): libreport-plugin-reportuploader-2.1.11-53.el7.centos.x86_64.rpm                       |  65 kB  00:00:00     
(408/670): libreport-plugin-rhtsupport-2.1.11-53.el7.centos.x86_64.rpm                           |  79 kB  00:00:00     
(409/670): libreport-plugin-ureport-2.1.11-53.el7.centos.x86_64.rpm                              |  59 kB  00:00:00     
(410/670): libreport-rhel-anaconda-bugzilla-2.1.11-53.el7.centos.x86_64.rpm                      |  43 kB  00:00:00     
(411/670): libreport-python-2.1.11-53.el7.centos.x86_64.rpm                                      |  71 kB  00:00:00     
(412/670): libreport-web-2.1.11-53.el7.centos.x86_64.rpm                                         |  58 kB  00:00:00     
(413/670): librbd1-10.2.5-4.el7.x86_64.rpm                                                       | 2.4 MB  00:00:01     
(414/670): librsvg2-2.40.20-1.el7.x86_64.rpm                                                     | 132 kB  00:00:00     
(415/670): libsane-hpaio-3.15.9-5.el7.x86_64.rpm                                                 | 104 kB  00:00:00     
(416/670): libsecret-0.18.6-1.el7.x86_64.rpm                                                     | 153 kB  00:00:00     
(417/670): libsemanage-python-2.5-14.el7.x86_64.rpm                                              | 113 kB  00:00:00     
(418/670): libsigc++20-2.10.0-1.el7.x86_64.rpm                                                   |  37 kB  00:00:00     
(419/670): libshout-2.2.2-11.el7.x86_64.rpm                                                      |  43 kB  00:00:00     
(420/670): libsmbios-2.3.3-8.el7.x86_64.rpm                                                      |  72 kB  00:00:00     
(421/670): libsmbclient-4.10.16-24.el7_9.x86_64.rpm                                              | 146 kB  00:00:00     
(422/670): libicu-50.2-4.el7_7.x86_64.rpm                                                        | 6.9 MB  00:00:04     
(423/670): libreswan-3.25-9.1.el7_8.x86_64.rpm                                                   | 1.4 MB  00:00:00     
(424/670): libsoup-2.62.2-2.el7.x86_64.rpm                                                       | 411 kB  00:00:00     
(425/670): libtalloc-2.1.16-1.el7.x86_64.rpm                                                     |  33 kB  00:00:00     
(426/670): libsrtp-1.4.4-11.20101004cvs.el7.x86_64.rpm                                           | 275 kB  00:00:00     
(427/670): libtar-1.2.11-29.el7.x86_64.rpm                                                       |  33 kB  00:00:00     
(428/670): libtdb-1.3.18-1.el7.x86_64.rpm                                                        |  49 kB  00:00:00     
(429/670): libspectre-0.2.8-1.el7.x86_64.rpm                                                     |  41 kB  00:00:00     
(430/670): libtevent-0.9.39-1.el7.x86_64.rpm                                                     |  41 kB  00:00:00     
(431/670): libthai-0.1.14-9.el7.x86_64.rpm                                                       | 187 kB  00:00:00     
(432/670): libtheora-1.1.1-8.el7.x86_64.rpm                                                      | 136 kB  00:00:00     
(433/670): libtool-ltdl-2.4.2-22.el7_3.x86_64.rpm                                                |  49 kB  00:00:00     
(434/670): libudisks2-2.8.4-1.el7.x86_64.rpm                                                     | 129 kB  00:00:00     
(435/670): libsndfile-1.0.25-12.el7_9.1.x86_64.rpm                                               | 150 kB  00:00:00     
(436/670): libusal-1.1.11-25.el7.x86_64.rpm                                                      | 136 kB  00:00:00     
(437/670): libusbx-1.0.21-1.el7.x86_64.rpm                                                       |  61 kB  00:00:00     
(438/670): libusbmuxd-1.0.10-5.el7.x86_64.rpm                                                    |  29 kB  00:00:00     
(439/670): libuser-python-0.60-9.el7.x86_64.rpm                                                  |  52 kB  00:00:00     
(440/670): libv4l-0.9.5-4.el7.x86_64.rpm                                                         | 194 kB  00:00:00     
(441/670): libpurple-2.10.11-9.el7.x86_64.rpm                                                    | 5.4 MB  00:00:02     
(442/670): libvirt-daemon-config-network-4.5.0-36.el7_9.5.x86_64.rpm                             | 205 kB  00:00:00     
(443/670): libvirt-daemon-4.5.0-36.el7_9.5.x86_64.rpm                                            | 845 kB  00:00:00     
(444/670): libvirt-daemon-driver-interface-4.5.0-36.el7_9.5.x86_64.rpm                           | 243 kB  00:00:00     
(445/670): libvirt-daemon-driver-nodedev-4.5.0-36.el7_9.5.x86_64.rpm                             | 242 kB  00:00:00     
(446/670): libvirt-daemon-driver-nwfilter-4.5.0-36.el7_9.5.x86_64.rpm                            | 266 kB  00:00:00     
(447/670): libvirt-daemon-driver-secret-4.5.0-36.el7_9.5.x86_64.rpm                              | 232 kB  00:00:00     
(448/670): libvirt-daemon-driver-network-4.5.0-36.el7_9.5.x86_64.rpm                             | 417 kB  00:00:00     
(449/670): libvirt-daemon-driver-storage-4.5.0-36.el7_9.5.x86_64.rpm                             | 203 kB  00:00:00     
(450/670): libvirt-daemon-driver-storage-core-4.5.0-36.el7_9.5.x86_64.rpm                        | 444 kB  00:00:00     
(451/670): libvirt-daemon-driver-storage-gluster-4.5.0-36.el7_9.5.x86_64.rpm                     | 242 kB  00:00:00     
(452/670): libvirt-daemon-driver-storage-disk-4.5.0-36.el7_9.5.x86_64.rpm                        | 234 kB  00:00:00     
(453/670): libvirt-daemon-driver-storage-iscsi-4.5.0-36.el7_9.5.x86_64.rpm                       | 231 kB  00:00:00     
(454/670): libtimezonemap-0.4.4-2.el7_9.x86_64.rpm                                               | 2.1 MB  00:00:01     
(455/670): libvirt-daemon-driver-storage-logical-4.5.0-36.el7_9.5.x86_64.rpm                     | 235 kB  00:00:00     
(456/670): libvirt-daemon-driver-qemu-4.5.0-36.el7_9.5.x86_64.rpm                                | 752 kB  00:00:00     
(457/670): libvirt-daemon-driver-storage-mpath-4.5.0-36.el7_9.5.x86_64.rpm                       | 230 kB  00:00:00     
(458/670): libvirt-gconfig-1.0.0-1.el7.x86_64.rpm                                                |  90 kB  00:00:00     
(459/670): libvirt-daemon-driver-storage-rbd-4.5.0-36.el7_9.5.x86_64.rpm                         | 237 kB  00:00:00     
(460/670): libvirt-daemon-kvm-4.5.0-36.el7_9.5.x86_64.rpm                                        | 203 kB  00:00:00     
(461/670): libvirt-gobject-1.0.0-1.el7.x86_64.rpm                                                |  64 kB  00:00:00     
(462/670): libvirt-daemon-driver-storage-scsi-4.5.0-36.el7_9.5.x86_64.rpm                        | 231 kB  00:00:00     
(463/670): libvirt-glib-1.0.0-1.el7.x86_64.rpm                                                   |  89 kB  00:00:00     
(464/670): libvorbis-1.3.3-8.el7.1.x86_64.rpm                                                    | 204 kB  00:00:00     
(465/670): libvisual-0.4.0-16.el7.x86_64.rpm                                                     | 138 kB  00:00:00     
(466/670): libwacom-0.30-1.el7.x86_64.rpm                                                        |  32 kB  00:00:00     
(467/670): libwacom-data-0.30-1.el7.noarch.rpm                                                   |  70 kB  00:00:00     
(468/670): libwayland-egl-1.15.0-1.el7.x86_64.rpm                                                |  13 kB  00:00:00     
(469/670): libwayland-cursor-1.15.0-1.el7.x86_64.rpm                                             |  20 kB  00:00:00     
(470/670): libwayland-client-1.15.0-1.el7.x86_64.rpm                                             |  33 kB  00:00:00     
(471/670): libwayland-server-1.15.0-1.el7.x86_64.rpm                                             |  39 kB  00:00:00     
(472/670): libwbclient-4.10.16-24.el7_9.x86_64.rpm                                               | 117 kB  00:00:00     
(473/670): libwebp-0.3.0-11.el7.x86_64.rpm                                                       | 170 kB  00:00:00     
(474/670): libvpx-1.3.0-8.el7.x86_64.rpm                                                         | 498 kB  00:00:00     
(475/670): libxkbcommon-x11-0.7.1-3.el7.x86_64.rpm                                               |  19 kB  00:00:00     
(476/670): libxklavier-5.4-7.el7.x86_64.rpm                                                      |  64 kB  00:00:00     
(477/670): libxkbcommon-0.7.1-3.el7.x86_64.rpm                                                   | 108 kB  00:00:00     
(478/670): libwnck3-3.24.1-2.el7.x86_64.rpm                                                      | 376 kB  00:00:00     
(479/670): libxslt-1.1.28-6.el7.x86_64.rpm                                                       | 242 kB  00:00:00     
(480/670): lockdev-1.0.4-0.13.20111007git.el7.x86_64.rpm                                         |  31 kB  00:00:00     
(481/670): lzop-1.03-10.el7.x86_64.rpm                                                           |  54 kB  00:00:00     
(482/670): lldpad-1.0.1-7.git036e314.el7_9.x86_64.rpm                                            | 283 kB  00:00:00     
(483/670): meanwhile-1.1.0-12.el7.x86_64.rpm                                                     |  96 kB  00:00:00     
(484/670): mesa-libEGL-18.3.4-12.el7_9.x86_64.rpm                                                | 110 kB  00:00:00     
(485/670): libwinpr-2.1.1-5.el7_9.x86_64.rpm                                                     | 346 kB  00:00:00     
(486/670): mdadm-4.1-9.el7_9.x86_64.rpm                                                          | 439 kB  00:00:00     
(487/670): mobile-broadband-provider-info-1.20170310-1.el7.noarch.rpm                            |  51 kB  00:00:00     
(488/670): mousetweaks-3.12.0-1.el7.x86_64.rpm                                                   | 125 kB  00:00:00     
(489/670): metacity-2.34.13-7.el7.x86_64.rpm                                                     | 1.1 MB  00:00:00     
(490/670): mtdev-1.1.5-5.el7.x86_64.rpm                                                          |  18 kB  00:00:00     
(491/670): mtools-4.0.18-5.el7.x86_64.rpm                                                        | 203 kB  00:00:00     
(492/670): mpg123-libs-1.25.6-1.el7.x86_64.rpm                                                   | 197 kB  00:00:00     
(493/670): mutter-3.28.3-32.el7_9.x86_64.rpm                                                     | 2.3 MB  00:00:00     
(494/670): nautilus-extensions-3.26.3.1-7.el7.x86_64.rpm                                         |  76 kB  00:00:00     
(495/670): nautilus-sendto-3.8.6-1.el7.x86_64.rpm                                                |  89 kB  00:00:00     
(496/670): nautilus-3.26.3.1-7.el7.x86_64.rpm                                                    | 2.9 MB  00:00:01     
(497/670): ncompress-4.2.4.4-3.1.el7_8.x86_64.rpm                                                |  27 kB  00:00:00     
(498/670): ndctl-65-6.el7_9.x86_64.rpm                                                           | 161 kB  00:00:00     
(499/670): neon-0.30.0-4.el7.x86_64.rpm                                                          | 166 kB  00:00:00     
(500/670): ndctl-libs-65-6.el7_9.x86_64.rpm                                                      |  65 kB  00:00:00     
(501/670): netcf-libs-0.2.8-4.el7.x86_64.rpm                                                     |  70 kB  00:00:00     
(502/670): net-snmp-libs-5.7.2-49.el7_9.2.x86_64.rpm                                             | 752 kB  00:00:00     
(503/670): nm-connection-editor-1.8.6-2.el7.x86_64.rpm                                           | 919 kB  00:00:00     
(504/670): numad-0.5-18.20150602git.el7.x86_64.rpm                                               |  35 kB  00:00:00     
(505/670): nmap-ncat-6.40-19.el7.x86_64.rpm                                                      | 206 kB  00:00:00     
(506/670): oddjob-0.31.5-4.el7.x86_64.rpm                                                        |  69 kB  00:00:00     
(507/670): openjpeg-libs-1.5.1-18.el7.x86_64.rpm                                                 |  86 kB  00:00:00     
(508/670): oddjob-mkhomedir-0.31.5-4.el7.x86_64.rpm                                              |  38 kB  00:00:00     
(509/670): openjpeg2-2.3.1-3.el7_7.x86_64.rpm                                                    | 153 kB  00:00:00     
(510/670): orc-0.4.26-1.el7.x86_64.rpm                                                           | 166 kB  00:00:00     
(511/670): opus-1.0.2-6.el7.x86_64.rpm                                                           | 630 kB  00:00:00     
(512/670): libvirt-libs-4.5.0-36.el7_9.5.x86_64.rpm                                              | 4.2 MB  00:00:02     
(513/670): osinfo-db-tools-1.1.0-1.el7.x86_64.rpm                                                |  79 kB  00:00:00     
(514/670): pakchois-0.4-10.el7.x86_64.rpm                                                        |  14 kB  00:00:00     
(515/670): osinfo-db-20200529-1.el7.noarch.rpm                                                   | 223 kB  00:00:00     
(516/670): pangomm-2.40.1-1.el7.x86_64.rpm                                                       |  58 kB  00:00:00     
(517/670): pango-1.42.4-4.el7_7.x86_64.rpm                                                       | 280 kB  00:00:00     
(518/670): mozjs52-52.9.0-1.el7.x86_64.rpm                                                       | 6.6 MB  00:00:02     
(519/670): pcre2-utf16-10.23-2.el7.x86_64.rpm                                                    | 189 kB  00:00:00     
(520/670): pinentry-gtk-0.8.1-17.el7.x86_64.rpm                                                  |  51 kB  00:00:00     
(521/670): pcre2-10.23-2.el7.x86_64.rpm                                                          | 201 kB  00:00:00     
(522/670): policycoreutils-python-2.5-34.el7.x86_64.rpm                                          | 457 kB  00:00:00     
(523/670): poppler-glib-0.26.5-43.el7.1.x86_64.rpm                                               | 142 kB  00:00:00     
(524/670): orca-3.6.3-4.el7.x86_64.rpm                                                           | 3.9 MB  00:00:01     
(525/670): pulseaudio-10.0-6.el7_9.x86_64.rpm                                                    | 923 kB  00:00:00     
(526/670): poppler-data-0.4.6-3.el7.noarch.rpm                                                   | 2.2 MB  00:00:00     
(527/670): pulseaudio-gdm-hooks-10.0-6.el7_9.x86_64.rpm                                          |  20 kB  00:00:00     
(528/670): pulseaudio-libs-10.0-6.el7_9.x86_64.rpm                                               | 651 kB  00:00:00     
(529/670): pycairo-1.8.10-8.el7.x86_64.rpm                                                       | 157 kB  00:00:00     
(530/670): pulseaudio-module-bluetooth-10.0-6.el7_9.x86_64.rpm                                   |  75 kB  00:00:00     
(531/670): pygobject2-2.28.6-11.el7.x86_64.rpm                                                   | 226 kB  00:00:00     
(532/670): pygtk2-libglade-2.24.0-9.el7.x86_64.rpm                                               |  25 kB  00:00:00     
(533/670): pulseaudio-libs-glib2-10.0-6.el7_9.x86_64.rpm                                         |  27 kB  00:00:00     
(534/670): pykickstart-1.99.66.22-1.el7.noarch.rpm                                               | 367 kB  00:00:00     
(535/670): poppler-0.26.5-43.el7.1.x86_64.rpm                                                    | 787 kB  00:00:00     
(536/670): pygtk2-2.24.0-9.el7.x86_64.rpm                                                        | 914 kB  00:00:00     
(537/670): python-IPy-0.75-6.el7.noarch.rpm                                                      |  32 kB  00:00:00     
(538/670): python-backports-ssl_match_hostname-3.5.0.1-1.el7.noarch.rpm                          |  13 kB  00:00:00     
(539/670): pyparted-3.9-15.el7.x86_64.rpm                                                        | 195 kB  00:00:00     
(540/670): python-backports-1.0-8.el7.x86_64.rpm                                                 | 5.8 kB  00:00:00     
(541/670): python-coverage-3.6-0.5.b3.el7.x86_64.rpm                                             | 153 kB  00:00:00     
(542/670): python-brlapi-0.6.0-16.el7.x86_64.rpm                                                 |  59 kB  00:00:00     
(543/670): python-augeas-0.5.0-2.el7.noarch.rpm                                                  |  25 kB  00:00:00     
(544/670): python-deltarpm-3.6-3.el7.x86_64.rpm                                                  |  31 kB  00:00:00     
(545/670): python-ethtool-0.8-8.el7.x86_64.rpm                                                   |  34 kB  00:00:00     
(546/670): python-inotify-0.9.4-4.el7.noarch.rpm                                                 |  49 kB  00:00:00     
(547/670): python-gobject-3.22.0-1.el7_4.1.x86_64.rpm                                            |  16 kB  00:00:00     
(548/670): python-ipaddress-1.0.16-2.el7.noarch.rpm                                              |  34 kB  00:00:00     
(549/670): python-meh-gui-0.25.3-1.el7.noarch.rpm                                                |  16 kB  00:00:00     
(550/670): python-meh-0.25.3-1.el7.noarch.rpm                                                    |  90 kB  00:00:00     
(551/670): python-di-0.3-2.el7.noarch.rpm                                                        |  19 kB  00:00:00     
(552/670): python-nss-0.16.0-3.el7.x86_64.rpm                                                    | 266 kB  00:00:00     
(553/670): python-ntplib-0.3.2-1.el7.noarch.rpm                                                  |  15 kB  00:00:00     
(554/670): python-pwquality-1.2.3-5.el7.x86_64.rpm                                               |  12 kB  00:00:00     
(555/670): python-pyblock-0.53-6.el7.x86_64.rpm                                                  |  72 kB  00:00:00     
(556/670): python2-blockdev-2.18-5.el7.x86_64.rpm                                                |  61 kB  00:00:00     
(557/670): python-six-1.9.0-2.el7.noarch.rpm                                                     |  29 kB  00:00:00     
(558/670): python2-futures-3.1.1-5.el7.noarch.rpm                                                |  29 kB  00:00:00     
(559/670): python-setuptools-0.9.8-7.el7.noarch.rpm                                              | 397 kB  00:00:00     
(560/670): python2-subprocess32-3.2.6-14.el7.x86_64.rpm                                          |  47 kB  00:00:00     
(561/670): pytz-2016.10-2.el7.noarch.rpm                                                         |  46 kB  00:00:00     
(562/670): python2-pyatspi-2.26.0-3.el7.noarch.rpm                                               |  87 kB  00:00:00     
(563/670): python-blivet-0.61.15.76-1.el7_9.noarch.rpm                                           | 835 kB  00:00:00     
(564/670): qgnomeplatform-0.3-5.el7.x86_64.rpm                                                   |  59 kB  00:00:00     
(565/670): qemu-img-1.5.3-175.el7_9.6.x86_64.rpm                                                 | 705 kB  00:00:00     
(566/670): qt5-qtbase-common-5.9.7-5.el7_9.noarch.rpm                                            |  26 kB  00:00:00     
(567/670): qemu-kvm-common-1.5.3-175.el7_9.6.x86_64.rpm                                          | 441 kB  00:00:00     
(568/670): radvd-2.17-3.el7.x86_64.rpm                                                           |  94 kB  00:00:00     
(569/670): rdma-core-22.4-6.el7_9.x86_64.rpm                                                     |  51 kB  00:00:00     
(570/670): realmd-0.16.1-12.el7_9.1.x86_64.rpm                                                   | 210 kB  00:00:00     
(571/670): redhat-menus-12.0.2-8.el7.noarch.rpm                                                  | 146 kB  00:00:00     
(572/670): rest-0.8.1-2.el7.x86_64.rpm                                                           |  63 kB  00:00:00     
(573/670): rsync-3.1.2-12.el7_9.x86_64.rpm                                                       | 408 kB  00:00:00     
(574/670): rtkit-0.11-10.el7.x86_64.rpm                                                          |  51 kB  00:00:00     
(575/670): qemu-kvm-1.5.3-175.el7_9.6.x86_64.rpm                                                 | 1.9 MB  00:00:00     
(576/670): samba-common-4.10.16-24.el7_9.noarch.rpm                                              | 219 kB  00:00:00     
(577/670): qt5-qtbase-5.9.7-5.el7_9.x86_64.rpm                                                   | 3.1 MB  00:00:01     
(578/670): sane-backends-1.0.24-12.el7.x86_64.rpm                                                | 670 kB  00:00:00     
(579/670): samba-common-libs-4.10.16-24.el7_9.x86_64.rpm                                         | 183 kB  00:00:00     
(580/670): sane-backends-libs-1.0.24-12.el7.x86_64.rpm                                           |  96 kB  00:00:00     
(581/670): mesa-libgbm-18.3.4-12.el7_9.x86_64.rpm                                                |  39 kB  00:00:05     
(582/670): sbc-1.0-5.el7.x86_64.rpm                                                              |  53 kB  00:00:00     
(583/670): seabios-bin-1.11.0-2.el7.noarch.rpm                                                   | 112 kB  00:00:00     
(584/670): satyr-0.13-15.el7.x86_64.rpm                                                          | 558 kB  00:00:00     
(585/670): seavgabios-bin-1.11.0-2.el7.noarch.rpm                                                |  38 kB  00:00:00     
(586/670): setools-libs-3.3.8-4.el7.x86_64.rpm                                                   | 620 kB  00:00:00     
(587/670): setroubleshoot-3.2.30-8.el7.x86_64.rpm                                                | 130 kB  00:00:00     
(588/670): qt5-qtbase-gui-5.9.7-5.el7_9.x86_64.rpm                                               | 5.4 MB  00:00:02     
(589/670): seahorse-3.20.0-1.el7.x86_64.rpm                                                      | 1.2 MB  00:00:00     
(590/670): sgabios-bin-0.20110622svn-4.el7.noarch.rpm                                            | 7.1 kB  00:00:00     
(591/670): sgpio-1.2.0.10-13.el7.x86_64.rpm                                                      |  13 kB  00:00:00     
(592/670): setroubleshoot-plugins-3.0.67-4.el7.noarch.rpm                                        | 358 kB  00:00:00     
(593/670): sane-backends-drivers-scanners-1.0.24-12.el7.x86_64.rpm                               | 2.3 MB  00:00:01     
(594/670): setroubleshoot-server-3.2.30-8.el7.x86_64.rpm                                         | 390 kB  00:00:00     
(595/670): samba-client-libs-4.10.16-24.el7_9.x86_64.rpm                                         | 5.0 MB  00:00:02     
(596/670): soundtouch-1.4.0-9.el7.x86_64.rpm                                                     |  53 kB  00:00:00     
(597/670): sound-theme-freedesktop-0.8-3.el7.noarch.rpm                                          | 377 kB  00:00:00     
(598/670): sos-3.9-5.el7.centos.11.noarch.rpm                                                    | 549 kB  00:00:00     
(599/670): speex-1.2-0.19.rc1.el7.x86_64.rpm                                                     |  98 kB  00:00:00     
(600/670): speech-dispatcher-python-0.7.1-15.el7.x86_64.rpm                                      |  52 kB  00:00:00     
(601/670): sox-14.4.1-7.el7.x86_64.rpm                                                           | 398 kB  00:00:00     
(602/670): spice-gtk3-0.35-5.el7_9.1.x86_64.rpm                                                  |  87 kB  00:00:00     
(603/670): startup-notification-0.12-8.el7.x86_64.rpm                                            |  39 kB  00:00:00     
(604/670): spice-glib-0.35-5.el7_9.1.x86_64.rpm                                                  | 357 kB  00:00:00     
(605/670): speech-dispatcher-0.7.1-15.el7.x86_64.rpm                                             | 363 kB  00:00:00     
(606/670): sushi-3.28.3-1.el7.x86_64.rpm                                                         |  99 kB  00:00:00     
(607/670): systemd-python-219-78.el7_9.7.x86_64.rpm                                              | 146 kB  00:00:00     
(608/670): telepathy-farstream-0.6.0-5.el7.x86_64.rpm                                            |  76 kB  00:00:00     
(609/670): taglib-1.8-8.20130218git.el7.x86_64.rpm                                               | 310 kB  00:00:00     
(610/670): telepathy-haze-0.8.0-1.el7.x86_64.rpm                                                 |  89 kB  00:00:00     
(611/670): telepathy-filesystem-0.0.2-6.el7.noarch.rpm                                           | 4.7 kB  00:00:00     
(612/670): telepathy-logger-0.8.0-5.el7.x86_64.rpm                                               |  98 kB  00:00:00     
(613/670): telepathy-mission-control-5.16.3-3.el7.x86_64.rpm                                     | 202 kB  00:00:00     
(614/670): telepathy-glib-0.24.1-1.el7.x86_64.rpm                                                | 719 kB  00:00:00     
(615/670): totem-nautilus-3.26.2-1.el7.x86_64.rpm                                                |  38 kB  00:00:00     
(616/670): totem-pl-parser-3.26.1-1.el7.x86_64.rpm                                               | 177 kB  00:00:00     
(617/670): telepathy-salut-0.8.1-6.el7.x86_64.rpm                                                | 390 kB  00:00:00     
(618/670): spice-server-0.14.0-9.el7_9.1.x86_64.rpm                                              | 405 kB  00:00:00     
(619/670): udisks2-2.8.4-1.el7.x86_64.rpm                                                        | 441 kB  00:00:00     
(620/670): upower-0.99.7-1.el7.x86_64.rpm                                                        | 162 kB  00:00:00     
(621/670): unbound-libs-1.6.6-5.el7_8.x86_64.rpm                                                 | 406 kB  00:00:00     
(622/670): tracker-1.10.5-8.el7.x86_64.rpm                                                       | 1.4 MB  00:00:00     
(623/670): urw-base35-d050000l-fonts-20170801-10.el7.noarch.rpm                                  |  75 kB  00:00:00     
(624/670): urw-base35-fonts-20170801-10.el7.noarch.rpm                                           | 7.6 kB  00:00:00     
(625/670): urw-base35-fonts-common-20170801-10.el7.noarch.rpm                                    |  19 kB  00:00:00     
(626/670): urw-base35-bookman-fonts-20170801-10.el7.noarch.rpm                                   | 852 kB  00:00:00     
(627/670): urw-base35-c059-fonts-20170801-10.el7.noarch.rpm                                      | 879 kB  00:00:00     
(628/670): telepathy-gabble-0.18.1-4.el7.x86_64.rpm                                              | 630 kB  00:00:01     
(629/670): totem-3.26.2-1.el7.x86_64.rpm                                                         | 2.2 MB  00:00:00     
(630/670): urw-base35-gothic-fonts-20170801-10.el7.noarch.rpm                                    | 650 kB  00:00:00     
(631/670): urw-base35-standard-symbols-ps-fonts-20170801-10.el7.noarch.rpm                       |  40 kB  00:00:00     
(632/670): urw-base35-nimbus-mono-ps-fonts-20170801-10.el7.noarch.rpm                            | 796 kB  00:00:00     
(633/670): urw-base35-z003-fonts-20170801-10.el7.noarch.rpm                                      | 275 kB  00:00:00     
(634/670): urw-base35-nimbus-roman-fonts-20170801-10.el7.noarch.rpm                              | 860 kB  00:00:00     
(635/670): usbmuxd-1.1.0-1.el7.x86_64.rpm                                                        |  56 kB  00:00:00     
(636/670): usbredir-0.7.1-3.el7.x86_64.rpm                                                       |  47 kB  00:00:00     
(637/670): urw-base35-p052-fonts-20170801-10.el7.noarch.rpm                                      | 978 kB  00:00:00     
(638/670): usermode-1.111-6.el7.x86_64.rpm                                                       | 193 kB  00:00:00     
(639/670): vorbis-tools-1.4.0-13.el7.x86_64.rpm                                                  | 214 kB  00:00:00     
(640/670): vino-3.22.0-7.el7.x86_64.rpm                                                          | 453 kB  00:00:00     
(641/670): volume_key-libs-0.3.9-9.el7.x86_64.rpm                                                | 141 kB  00:00:00     
(642/670): vte-profile-0.52.4-1.el7.x86_64.rpm                                                   | 7.1 kB  00:00:00     
(643/670): wavpack-4.60.1-9.el7.x86_64.rpm                                                       | 131 kB  00:00:00     
(644/670): vinagre-3.22.0-14.el7.x86_64.rpm                                                      | 1.4 MB  00:00:00     
(645/670): vte291-0.52.4-1.el7.x86_64.rpm                                                        | 250 kB  00:00:00     
(646/670): webrtc-audio-processing-0.3-1.el7.x86_64.rpm                                          | 286 kB  00:00:00     
(647/670): wodim-1.1.11-25.el7.x86_64.rpm                                                        | 320 kB  00:00:00     
(648/670): xcb-util-0.4.0-2.el7.x86_64.rpm                                                       |  16 kB  00:00:00     
(649/670): xcb-util-image-0.4.0-2.el7.x86_64.rpm                                                 |  15 kB  00:00:00     
(650/670): urw-base35-nimbus-sans-fonts-20170801-10.el7.noarch.rpm                               | 1.3 MB  00:00:01     
(651/670): xcb-util-keysyms-0.4.0-1.el7.x86_64.rpm                                               |  10 kB  00:00:00     
(652/670): xcb-util-renderutil-0.3.9-3.el7.x86_64.rpm                                            |  12 kB  00:00:00     
(653/670): xcb-util-wm-0.4.1-5.el7.x86_64.rpm                                                    |  25 kB  00:00:00     
(654/670): xdg-desktop-portal-gtk-1.0.2-1.el7.x86_64.rpm                                         | 157 kB  00:00:00     
(655/670): xdg-user-dirs-0.15-5.el7.x86_64.rpm                                                   |  59 kB  00:00:00     
(656/670): xdg-desktop-portal-1.0.2-1.el7.x86_64.rpm                                             | 248 kB  00:00:00     
(657/670): xdg-utils-1.1.0-0.17.20120809git.el7.noarch.rpm                                       |  70 kB  00:00:00     
(658/670): xml-common-0.6.3-39.el7.noarch.rpm                                                    |  26 kB  00:00:00     
(659/670): xdg-user-dirs-gtk-0.10-4.el7.x86_64.rpm                                               |  66 kB  00:00:00     
(660/670): xmlrpc-c-client-1.32.5-1905.svn2451.el7.x86_64.rpm                                    |  32 kB  00:00:00     
(661/670): xorg-x11-font-utils-7.5-21.el7.x86_64.rpm                                             | 104 kB  00:00:00     
(662/670): yajl-2.0.4-4.el7.x86_64.rpm                                                           |  39 kB  00:00:00     
(663/670): xmlrpc-c-1.32.5-1905.svn2451.el7.x86_64.rpm                                           | 130 kB  00:00:00     
(664/670): yelp-libs-3.28.1-1.el7.x86_64.rpm                                                     | 101 kB  00:00:00     
(665/670): yelp-3.28.1-1.el7.x86_64.rpm                                                          | 777 kB  00:00:00     
(666/670): yelp-xsl-3.28.0-1.el7.noarch.rpm                                                      | 204 kB  00:00:00     
(667/670): webkitgtk4-jsc-2.28.2-3.el7.x86_64.rpm                                                | 5.7 MB  00:00:02     
(668/670): webkitgtk3-2.4.11-2.el7.x86_64.rpm                                                    |  11 MB  00:00:03     
(669/670): webkitgtk4-2.28.2-3.el7.x86_64.rpm                                                    |  28 MB  00:00:06     
(670/670): zenity-3.28.1-2.el7_9.x86_64.rpm                                                      | 4.0 MB  00:00:04     
------------------------------------------------------------------------------------------------------------------------
Total                                                                                   8.3 MB/s | 397 MB  00:00:48     
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : atk-2.28.1-2.el7.x86_64                                                                            1/670 
  Installing : avahi-libs-0.6.31-20.el7.x86_64                                                                    2/670 
  Installing : json-glib-1.4.2-2.el7.x86_64                                                                       3/670 
  Installing : gstreamer1-1.10.4-2.el7.x86_64                                                                     4/670 
  Installing : libsecret-0.18.6-1.el7.x86_64                                                                      5/670 
  Installing : libgudev1-219-78.el7_9.7.x86_64                                                                    6/670 
  Installing : libusbx-1.0.21-1.el7.x86_64                                                                        7/670 
  Installing : libXcomposite-0.4.4-4.1.el7.x86_64                                                                 8/670 
  Installing : satyr-0.13-15.el7.x86_64                                                                           9/670 
  Installing : 2:libogg-1.3.0-7.el7.x86_64                                                                       10/670 
  Installing : yajl-2.0.4-4.el7.x86_64                                                                           11/670 
  Installing : libwayland-client-1.15.0-1.el7.x86_64                                                             12/670 
  Installing : libwayland-server-1.15.0-1.el7.x86_64                                                             13/670 
  Installing : gsettings-desktop-schemas-3.28.0-3.el7.x86_64                                                     14/670 
  Installing : mesa-libgbm-18.3.4-12.el7_9.x86_64                                                                15/670 
  Installing : 1:libvorbis-1.3.3-8.el7.1.x86_64                                                                  16/670 
  Installing : 1:cups-libs-1.6.3-51.el7.x86_64                                                                   17/670 
  Installing : telepathy-glib-0.24.1-1.el7.x86_64                                                                18/670 
  Installing : augeas-libs-1.4.0-10.el7.x86_64                                                                   19/670 
  Installing : libxkbcommon-0.7.1-3.el7.x86_64                                                                   20/670 
  Installing : libwayland-egl-1.15.0-1.el7.x86_64                                                                21/670 
  Installing : avahi-glib-0.6.31-20.el7.x86_64                                                                   22/670 
  Installing : lcms2-2.6-3.el7.x86_64                                                                            23/670 
  Installing : libtar-1.2.11-29.el7.x86_64                                                                       24/670 
  Installing : 1:xorg-x11-font-utils-7.5-21.el7.x86_64                                                           25/670 
  Installing : libwayland-cursor-1.15.0-1.el7.x86_64                                                             26/670 
  Installing : libblockdev-utils-2.18-5.el7.x86_64                                                               27/670 
  Installing : gvfs-client-1.36.2-7.el7_9.x86_64                                                                 28/670 
  Installing : libicu-50.2-4.el7_7.x86_64                                                                        29/670 
  Installing : PackageKit-glib-1.1.10-2.el7.centos.x86_64                                                        30/670 
  Installing : libtdb-1.3.18-1.el7.x86_64                                                                        31/670 
  Installing : xmlrpc-c-1.32.5-1905.svn2451.el7.x86_64                                                           32/670 
  Installing : telepathy-filesystem-0.0.2-6.el7.noarch                                                           33/670 
  Installing : glusterfs-libs-6.0-61.el7.x86_64                                                                  34/670 
  Installing : orc-0.4.26-1.el7.x86_64                                                                           35/670 
  Installing : xmlrpc-c-client-1.32.5-1905.svn2451.el7.x86_64                                                    36/670 
  Installing : flac-libs-1.3.0-5.el7_1.x86_64                                                                    37/670 
  Installing : dconf-0.28.0-4.el7.x86_64                                                                         38/670 
  Installing : opus-1.0.2-6.el7.x86_64                                                                           39/670 
  Installing : libsigc++20-2.10.0-1.el7.x86_64                                                                   40/670 
  Installing : libxslt-1.1.28-6.el7.x86_64                                                                       41/670 
  Installing : libtool-ltdl-2.4.2-22.el7_3.x86_64                                                                42/670 
  Installing : totem-pl-parser-3.26.1-1.el7.x86_64                                                               43/670 
  Installing : 1:NetworkManager-glib-1.18.8-2.el7_9.x86_64                                                       44/670 
  Installing : 1:dbus-x11-1.10.24-15.el7.x86_64                                                                  45/670 
  Installing : 1:libtheora-1.1.1-8.el7.x86_64                                                                    46/670 
  Installing : ibus-libs-1.5.17-12.el7_9.x86_64                                                                  47/670 
  Installing : hicolor-icon-theme-0.12-7.el7.noarch                                                              48/670 
  Installing : speex-1.2-0.19.rc1.el7.x86_64                                                                     49/670 
  Installing : libexif-0.6.22-2.el7_9.x86_64                                                                     50/670 
  Installing : libv4l-0.9.5-4.el7.x86_64                                                                         51/670 
  Installing : libdvdread-5.0.3-3.el7.x86_64                                                                     52/670 
  Installing : fontpackages-filesystem-1.44-8.el7.noarch                                                         53/670 
  Installing : urw-base35-fonts-common-20170801-10.el7.noarch                                                    54/670 
  Installing : libplist-1.12-3.el7.x86_64                                                                        55/670 
  Installing : libtalloc-2.1.16-1.el7.x86_64                                                                     56/670 
  Installing : libpeas-1.22.0-1.el7.x86_64                                                                       57/670 
  Installing : gsm-1.0.13-11.el7.x86_64                                                                          58/670 
  Installing : libsndfile-1.0.25-12.el7_9.1.x86_64                                                               59/670 
  Installing : libtevent-0.9.39-1.el7.x86_64                                                                     60/670 
  Installing : glibmm24-2.56.0-1.el7.x86_64                                                                      61/670 
  Installing : libraw1394-2.1.0-2.el7.x86_64                                                                     62/670 
  Installing : 1:control-center-filesystem-3.28.1-8.el7_9.1.x86_64                                               63/670 
  Installing : GConf2-3.2.6-8.el7.x86_64                                                                         64/670 
  Installing : pygobject2-2.28.6-11.el7.x86_64                                                                   65/670 
  Installing : libldb-1.5.4-2.el7.x86_64                                                                         66/670 
  Installing : gnome-icon-theme-3.12.0-1.el7.noarch                                                              67/670 
  Installing : libical-3.0.3-2.el7.x86_64                                                                        68/670 
  Installing : celt051-0.5.1.3-8.el7.x86_64                                                                      69/670 
  Installing : libgusb-0.2.9-1.el7.x86_64                                                                        70/670 
  Installing : colord-libs-1.3.4-2.el7.x86_64                                                                    71/670 
  Installing : usbredir-0.7.1-3.el7.x86_64                                                                       72/670 
  Installing : libepoxy-1.5.2-1.el7.x86_64                                                                       73/670 
  Installing : liboauth-0.9.7-4.el7.x86_64                                                                       74/670 
  Installing : cdparanoia-libs-10.2-17.el7.x86_64                                                                75/670 
  Installing : boost-system-1.53.0-28.el7.x86_64                                                                 76/670 
  Installing : wavpack-4.60.1-9.el7.x86_64                                                                       77/670 
  Installing : libgee-0.20.1-1.el7.x86_64                                                                        78/670 
  Installing : 14:libpcap-1.5.3-13.el7_9.x86_64                                                                  79/670 
  Installing : libudisks2-2.8.4-1.el7.x86_64                                                                     80/670 
  Installing : taglib-1.8-8.20130218git.el7.x86_64                                                               81/670 
  Installing : samba-common-4.10.16-24.el7_9.noarch                                                              82/670 
  Installing : gperftools-libs-2.6.1-1.el7.x86_64                                                                83/670 
  Installing : pcre2-10.23-2.el7.x86_64                                                                          84/670 
  Installing : libusal-1.1.11-25.el7.x86_64                                                                      85/670 
  Installing : genisoimage-1.1.11-25.el7.x86_64                                                                  86/670 
  Installing : accountsservice-0.6.50-7.el7.x86_64                                                               87/670 
  Installing : accountsservice-libs-0.6.50-7.el7.x86_64                                                          88/670 
  Installing : libieee1284-0.2.11-15.el7.x86_64                                                                  89/670 
  Installing : 1:pyparted-3.9-15.el7.x86_64                                                                      90/670 
  Installing : libcdio-0.92-3.el7.x86_64                                                                         91/670 
  Installing : libcdio-paranoia-10.2+0.90-11.el7.x86_64                                                          92/670 
  Installing : samba-common-libs-4.10.16-24.el7_9.x86_64                                                         93/670 
  Installing : libwbclient-4.10.16-24.el7_9.x86_64                                                               94/670 
  Installing : samba-client-libs-4.10.16-24.el7_9.x86_64                                                         95/670 
  Installing : libsmbclient-4.10.16-24.el7_9.x86_64                                                              96/670 
  Installing : boost-thread-1.53.0-28.el7.x86_64                                                                 97/670 
  Installing : bluez-5.44-7.el7.x86_64                                                                           98/670 
  Installing : libavc1394-0.5.3-14.el7.x86_64                                                                    99/670 
  Installing : libiec61883-1.2.0-10.el7.x86_64                                                                  100/670 
  Installing : atkmm-2.24.2-1.el7.x86_64                                                                        101/670 
  Installing : libdvdnav-5.0.3-1.el7.x86_64                                                                     102/670 
  Installing : libshout-2.2.2-11.el7.x86_64                                                                     103/670 
  Installing : 1:telepathy-mission-control-5.16.3-3.el7.x86_64                                                  104/670 
  Installing : telepathy-logger-0.8.0-5.el7.x86_64                                                              105/670 
  Installing : libblockdev-2.18-5.el7.x86_64                                                                    106/670 
  Installing : avahi-gobject-0.6.31-20.el7.x86_64                                                               107/670 
  Installing : python-augeas-0.5.0-2.el7.noarch                                                                 108/670 
  Installing : mesa-libEGL-18.3.4-12.el7_9.x86_64                                                               109/670 
  Installing : 1:libglvnd-egl-1.0.1-0.8.git5baa1e5.el7.x86_64                                                   110/670 
  Installing : 1:libglvnd-gles-1.0.1-0.8.git5baa1e5.el7.x86_64                                                  111/670 
  Installing : hunspell-en-US-0.20121024-6.el7.noarch                                                           112/670 
  Installing : hunspell-1.3.2-16.el7.x86_64                                                                     113/670 
  Installing : 1:enchant-1.6.0-8.el7.x86_64                                                                     114/670 
  Installing : langtable-0.0.31-4.el7.noarch                                                                    115/670 
  Installing : langtable-data-0.0.31-4.el7.noarch                                                               116/670 
  Installing : glx-utils-8.3.0-10.el7.x86_64                                                                    117/670 
  Installing : soundtouch-1.4.0-9.el7.x86_64                                                                    118/670 
  Installing : libvisual-0.4.0-16.el7.x86_64                                                                    119/670 
  Installing : libXv-1.0.11-1.el7.x86_64                                                                        120/670 
  Installing : audit-libs-python-2.8.5-4.el7.x86_64                                                             121/670 
  Installing : mobile-broadband-provider-info-1.20170310-1.el7.noarch                                           122/670 
  Installing : boost-iostreams-1.53.0-28.el7.x86_64                                                             123/670 
  Installing : pykickstart-1.99.66.22-1.el7.noarch                                                              124/670 
  Installing : libmpcdec-1.2.6-12.el7.x86_64                                                                    125/670 
  Installing : python-six-1.9.0-2.el7.noarch                                                                    126/670 
  Installing : jasper-libs-1.900.1-33.el7.x86_64                                                                127/670 
  Installing : gdk-pixbuf2-2.36.12-3.el7.x86_64                                                                 128/670 
  Installing : libnotify-0.7.7-1.el7.x86_64                                                                     129/670 
  Installing : gtk-update-icon-cache-3.22.30-8.el7_9.x86_64                                                     130/670 
  Installing : gvnc-0.7.0-3.el7.x86_64                                                                          131/670 
  Installing : libmediaart-1.9.4-1.el7.x86_64                                                                   132/670 
  Installing : xcb-util-0.4.0-2.el7.x86_64                                                                      133/670 
  Installing : startup-notification-0.12-8.el7.x86_64                                                           134/670 
  Installing : libwebp-0.3.0-11.el7.x86_64                                                                      135/670 
  Installing : 1:NetworkManager-wifi-1.18.8-2.el7_9.x86_64                                                      136/670 
  Installing : daxctl-libs-65-6.el7_9.x86_64                                                                    137/670 
  Installing : ndctl-libs-65-6.el7_9.x86_64                                                                     138/670 
  Installing : libvirt-gconfig-1.0.0-1.el7.x86_64                                                               139/670 
  Installing : python-IPy-0.75-6.el7.noarch                                                                     140/670 
  Installing : systemd-python-219-78.el7_9.7.x86_64                                                             141/670 
  Installing : gdb-7.6.1-120.el7.x86_64                                                                         142/670 
  Installing : rdma-core-22.4-6.el7_9.x86_64                                                                    143/670 
  Installing : libibverbs-22.4-6.el7_9.x86_64                                                                   144/670 
  Installing : libcgroup-0.41-21.el7.x86_64                                                                     145/670 
  Installing : 40:libcacard-2.7.0-1.el7.x86_64                                                                  146/670 
  Installing : gdisk-0.8.10-3.el7.x86_64                                                                        147/670 
  Installing : exempi-2.2.0-9.el7.x86_64                                                                        148/670 
  Installing : libdv-1.0.0-17.el7.x86_64                                                                        149/670 
  Installing : libvpx-1.3.0-8.el7.x86_64                                                                        150/670 
  Installing : elfutils-0.176-5.el7.x86_64                                                                      151/670 
  Installing : xml-common-0.6.3-39.el7.noarch                                                                   152/670 
  Installing : iso-codes-3.46-2.el7.noarch                                                                      153/670 
  Installing : libxklavier-5.4-7.el7.x86_64                                                                     154/670 
  Installing : boost-random-1.53.0-28.el7.x86_64                                                                155/670 
  Installing : 1:librados2-10.2.5-4.el7.x86_64                                                                  156/670 
  Installing : 1:librbd1-10.2.5-4.el7.x86_64                                                                    157/670 
  Installing : fuse-2.9.2-11.el7.x86_64                                                                         158/670 
  Installing : ModemManager-glib-1.6.10-4.el7.x86_64                                                            159/670 
  Installing : libiscsi-1.9.0-7.el7.x86_64                                                                      160/670 
  Installing : lzop-1.03-10.el7.x86_64                                                                          161/670 
  Installing : at-spi2-core-2.28.0-1.el7.x86_64                                                                 162/670 
  Installing : at-spi2-atk-2.26.2-1.el7.x86_64                                                                  163/670 
  Installing : libgtop2-2.38.0-3.el7.x86_64                                                                     164/670 
  Installing : libreport-filesystem-2.1.11-53.el7.centos.x86_64                                                 165/670 
  Installing : libreport-python-2.1.11-53.el7.centos.x86_64                                                     166/670 
  Installing : libreport-2.1.11-53.el7.centos.x86_64                                                            167/670 
  Installing : abrt-libs-2.1.11-60.el7.centos.x86_64                                                            168/670 
  Installing : mdadm-4.1-9.el7_9.x86_64                                                                         169/670 
  Installing : deltarpm-3.6-3.el7.x86_64                                                                        170/670 
  Installing : openjpeg-libs-1.5.1-18.el7.x86_64                                                                171/670 
  Installing : adobe-mappings-cmap-20171205-3.el7.noarch                                                        172/670 
  Installing : adobe-mappings-cmap-deprecated-20171205-3.el7.noarch                                             173/670 
  Installing : python-deltarpm-3.6-3.el7.x86_64                                                                 174/670 
  Installing : createrepo-0.9.9-28.el7.noarch                                                                   175/670 
  Installing : libreport-cli-2.1.11-53.el7.centos.x86_64                                                        176/670 
  Installing : python-meh-0.25.3-1.el7.noarch                                                                   177/670 
  Installing : 10:qemu-kvm-common-1.5.3-175.el7_9.6.x86_64                                                      178/670 
  Installing : librdmacm-22.4-6.el7_9.x86_64                                                                    179/670 
  Installing : ndctl-65-6.el7_9.x86_64                                                                          180/670 
  Installing : libblockdev-nvdimm-2.18-5.el7.x86_64                                                             181/670 
  Installing : xcb-util-image-0.4.0-2.el7.x86_64                                                                182/670 
  Installing : libgsf-1.14.26-7.el7.x86_64                                                                      183/670 
  Installing : langtable-python-0.0.31-4.el7.noarch                                                             184/670 
  Installing : python2-blockdev-2.18-5.el7.x86_64                                                               185/670 
  Installing : dvd+rw-tools-7.1-15.el7.x86_64                                                                   186/670 
  Installing : wodim-1.1.11-25.el7.x86_64                                                                       187/670 
  Installing : 2:nmap-ncat-6.40-19.el7.x86_64                                                                   188/670 
  Installing : ldns-1.6.16-10.el7.x86_64                                                                        189/670 
  Installing : cdparanoia-10.2-17.el7.x86_64                                                                    190/670 
  Installing : spice-server-0.14.0-9.el7_9.1.x86_64                                                             191/670 
  Installing : PackageKit-1.1.10-2.el7.centos.x86_64                                                            192/670 
  Installing : PackageKit-yum-1.1.10-2.el7.centos.x86_64                                                        193/670 
  Installing : libusbmuxd-1.0.10-5.el7.x86_64                                                                   194/670 
  Installing : libimobiledevice-1.2.0-1.el7.x86_64                                                              195/670 
  Installing : upower-0.99.7-1.el7.x86_64                                                                       196/670 
  Installing : usbmuxd-1.1.0-1.el7.x86_64                                                                       197/670 
  Installing : abattis-cantarell-fonts-0.0.25-1.el7.noarch                                                      198/670 
  Installing : dejavu-fonts-common-2.33-6.el7.noarch                                                            199/670 
  Installing : dejavu-sans-fonts-2.33-6.el7.noarch                                                              200/670 
  Installing : fontconfig-2.13.0-4.3.el7.x86_64                                                                 201/670 
  Installing : cairo-1.15.12-4.el7.x86_64                                                                       202/670 
  Installing : cairo-gobject-1.15.12-4.el7.x86_64                                                               203/670 
  Installing : cairomm-1.12.0-1.el7.x86_64                                                                      204/670 
  Installing : libgxps-0.3.0-4.el7.x86_64                                                                       205/670 
  Installing : pycairo-1.8.10-8.el7.x86_64                                                                      206/670 
  Installing : python-gobject-3.22.0-1.el7_4.1.x86_64                                                           207/670 
  Installing : libpeas-loader-python-1.22.0-1.el7.x86_64                                                        208/670 
  Installing : python2-pyatspi-2.26.0-3.el7.noarch                                                              209/670 
  Installing : urw-base35-d050000l-fonts-20170801-10.el7.noarch                                                 210/670 
  Installing : urw-base35-standard-symbols-ps-fonts-20170801-10.el7.noarch                                      211/670 
  Installing : urw-base35-gothic-fonts-20170801-10.el7.noarch                                                   212/670 
  Installing : urw-base35-nimbus-roman-fonts-20170801-10.el7.noarch                                             213/670 
  Installing : urw-base35-nimbus-mono-ps-fonts-20170801-10.el7.noarch                                           214/670 
  Installing : urw-base35-nimbus-sans-fonts-20170801-10.el7.noarch                                              215/670 
  Installing : urw-base35-z003-fonts-20170801-10.el7.noarch                                                     216/670 
  Installing : urw-base35-p052-fonts-20170801-10.el7.noarch                                                     217/670 
  Installing : libXft-2.3.2-2.el7.x86_64                                                                        218/670 
  Installing : urw-base35-c059-fonts-20170801-10.el7.noarch                                                     219/670 
  Installing : urw-base35-bookman-fonts-20170801-10.el7.noarch                                                  220/670 
  Installing : urw-base35-fonts-20170801-10.el7.noarch                                                          221/670 
  Installing : google-noto-emoji-color-fonts-20180508-4.el7.noarch                                              222/670 
  Installing : glusterfs-6.0-61.el7.x86_64                                                                      223/670 
  Installing : glusterfs-client-xlators-6.0-61.el7.x86_64                                                       224/670 
  Installing : glusterfs-api-6.0-61.el7.x86_64                                                                  225/670 
  Installing : 10:qemu-img-1.5.3-175.el7_9.6.x86_64                                                             226/670 
  Installing : glusterfs-cli-6.0-61.el7.x86_64                                                                  227/670 
  Installing : libwinpr-2.1.1-5.el7_9.x86_64                                                                    228/670 
  Installing : brltty-4.5-16.el7.x86_64                                                                         229/670 
  Installing : brlapi-0.6.0-16.el7.x86_64                                                                       230/670 
  Installing : python-brlapi-0.6.0-16.el7.x86_64                                                                231/670 
  Installing : libblockdev-swap-2.18-5.el7.x86_64                                                               232/670 
  Installing : libblockdev-loop-2.18-5.el7.x86_64                                                               233/670 
  Installing : compat-libcolord1-1.0.4-1.el7.x86_64                                                             234/670 
  Installing : libxkbcommon-x11-0.7.1-3.el7.x86_64                                                              235/670 
  Installing : cups-pk-helper-0.2.6-2.el7.x86_64                                                                236/670 
  Installing : libmtp-1.1.14-1.el7.x86_64                                                                       237/670 
  Installing : libfprint-0.8.2-1.el7.x86_64                                                                     238/670 
  Installing : fprintd-0.8.1-2.el7.x86_64                                                                       239/670 
  Installing : iscsi-initiator-utils-6.2.0.874-22.el7_9.x86_64                                                  240/670 
  Installing : iscsi-initiator-utils-iscsiuio-6.2.0.874-22.el7_9.x86_64                                         241/670 
  Installing : libisofs-1.2.8-4.el7.x86_64                                                                      242/670 
  Installing : checkpolicy-2.5-8.el7.x86_64                                                                     243/670 
  Installing : libevdev-1.5.6-1.el7.x86_64                                                                      244/670 
  Installing : libthai-0.1.14-9.el7.x86_64                                                                      245/670 
  Installing : oddjob-0.31.5-4.el7.x86_64                                                                       246/670 
  Installing : oddjob-mkhomedir-0.31.5-4.el7.x86_64                                                             247/670 
  Installing : realmd-0.16.1-12.el7_9.1.x86_64                                                                  248/670 
  Installing : libasyncns-0.8-7.el7.x86_64                                                                      249/670 
  Installing : pulseaudio-libs-10.0-6.el7_9.x86_64                                                              250/670 
  Installing : pulseaudio-libs-glib2-10.0-6.el7_9.x86_64                                                        251/670 
  Installing : libao-1.1.0-8.el7.x86_64                                                                         252/670 
  Installing : festival-speechtools-libs-1.2.96-28.el7.x86_64                                                   253/670 
  Installing : festival-lib-1.96-28.el7.x86_64                                                                  254/670 
  Installing : festvox-slt-arctic-hts-0.20061229-28.el7.noarch                                                  255/670 
  Installing : festival-1.96-28.el7.x86_64                                                                      256/670 
  Installing : 1:vorbis-tools-1.4.0-13.el7.x86_64                                                               257/670 
  Installing : icedax-1.1.11-25.el7.x86_64                                                                      258/670 
  Installing : cdrdao-1.2.3-20.el7.x86_64                                                                       259/670 
  Installing : sox-14.4.1-7.el7.x86_64                                                                          260/670 
  Installing : festival-freebsoft-utils-0.10-7.el7.noarch                                                       261/670 
  Installing : espeak-1.47.11-4.el7.x86_64                                                                      262/670 
  Installing : freerdp-libs-2.1.1-5.el7_9.x86_64                                                                263/670 
  Installing : python-pwquality-1.2.3-5.el7.x86_64                                                              264/670 
  Installing : libsrtp-1.4.4-11.20101004cvs.el7.x86_64                                                          265/670 
  Installing : device-mapper-multipath-libs-0.4.9-136.el7_9.x86_64                                              266/670 
  Installing : device-mapper-multipath-0.4.9-136.el7_9.x86_64                                                   267/670 
  Installing : libblockdev-part-2.18-5.el7.x86_64                                                               268/670 
  Installing : libblockdev-fs-2.18-5.el7.x86_64                                                                 269/670 
  Installing : poppler-data-0.4.6-3.el7.noarch                                                                  270/670 
  Installing : poppler-0.26.5-43.el7.1.x86_64                                                                   271/670 
  Installing : poppler-glib-0.26.5-43.el7.1.x86_64                                                              272/670 
  Installing : 1:isomd5sum-1.0.10-5.el7.x86_64                                                                  273/670 
  Installing : liblouis-2.5.2-12.el7_4.x86_64                                                                   274/670 
  Installing : liblouis-python-2.5.2-12.el7_4.noarch                                                            275/670 
  Installing : webrtc-audio-processing-0.3-1.el7.x86_64                                                         276/670 
  Installing : hyphen-2.8.6-5.el7.x86_64                                                                        277/670 
  Installing : libpaper-1.1.24-9.el7.x86_64                                                                     278/670 
  Installing : volume_key-libs-0.3.9-9.el7.x86_64                                                               279/670 
  Installing : libblockdev-crypto-2.18-5.el7.x86_64                                                             280/670 
  Installing : graphite2-1.3.10-1.el7_3.x86_64                                                                  281/670 
  Installing : harfbuzz-1.7.5-2.el7.x86_64                                                                      282/670 
  Installing : harfbuzz-icu-1.7.5-2.el7.x86_64                                                                  283/670 
  Installing : sgpio-1.2.0.10-13.el7.x86_64                                                                     284/670 
  Installing : dmraid-1.0.0.rc16-28.el7.x86_64                                                                  285/670 
  Installing : dmraid-events-1.0.0.rc16-28.el7.x86_64                                                           286/670 
  Installing : python-pyblock-0.53-6.el7.x86_64                                                                 287/670 
  Installing : dotconf-1.3-8.el7.x86_64                                                                         288/670 
  Installing : cyrus-sasl-plain-2.1.26-24.el7_9.x86_64                                                          289/670 
  Installing : osinfo-db-tools-1.1.0-1.el7.x86_64                                                               290/670 
  Installing : python-nss-0.16.0-3.el7.x86_64                                                                   291/670 
  Installing : fros-1.0-5.el7.noarch                                                                            292/670 
  Installing : cryptsetup-python-2.0.3-6.el7.x86_64                                                             293/670 
  Installing : gstreamer-tools-0.10.36-7.el7.x86_64                                                             294/670 
  Installing : gstreamer-0.10.36-7.el7.x86_64                                                                   295/670 
  Installing : compat-exiv2-026-0.26-2.el7.x86_64                                                               296/670 
  Installing : cyrus-sasl-md5-2.1.26-24.el7_9.x86_64                                                            297/670 
  Installing : sbc-1.0-5.el7.x86_64                                                                             298/670 
  Installing : ipxe-roms-qemu-20180825-3.git133f4c.el7.noarch                                                   299/670 
  Installing : numad-0.5-18.20150602git.el7.x86_64                                                              300/670 
  Installing : sound-theme-freedesktop-0.8-3.el7.noarch                                                         301/670 
  Installing : libcanberra-0.30-9.el7.x86_64                                                                    302/670 
  Installing : gsound-1.0.2-2.el7.x86_64                                                                        303/670 
  Installing : rsync-3.1.2-12.el7_9.x86_64                                                                      304/670 
  Installing : fftw-libs-double-3.3.3-8.el7.x86_64                                                              305/670 
  Installing : libofa-0.9.3-24.el7.x86_64                                                                       306/670 
  Installing : xcb-util-wm-0.4.1-5.el7.x86_64                                                                   307/670 
  Installing : libsmbios-2.3.3-8.el7.x86_64                                                                     308/670 
  Installing : python2-futures-3.1.1-5.el7.noarch                                                               309/670 
  Installing : sos-3.9-5.el7.centos.11.noarch                                                                   310/670 
  Installing : bolt-0.7-1.el7.x86_64                                                                            311/670 
  Installing : rtkit-0.11-10.el7.x86_64                                                                         312/670 
  Installing : pulseaudio-10.0-6.el7_9.x86_64                                                                   313/670 
  Installing : pulseaudio-module-bluetooth-10.0-6.el7_9.x86_64                                                  314/670 
  Installing : libatasmart-0.19-6.el7.x86_64                                                                    315/670 
  Installing : pakchois-0.4-10.el7.x86_64                                                                       316/670 
  Installing : meanwhile-1.1.0-12.el7.x86_64                                                                    317/670 
  Installing : libsemanage-python-2.5-14.el7.x86_64                                                             318/670 
  Installing : lockdev-1.0.4-0.13.20111007git.el7.x86_64                                                        319/670 
  Installing : fribidi-1.0.2-1.el7_7.1.x86_64                                                                   320/670 
  Installing : pango-1.42.4-4.el7_7.x86_64                                                                      321/670 
  Installing : gstreamer1-plugins-base-1.10.4-2.el7.x86_64                                                      322/670 
  Installing : cogl-1.22.2-2.el7.x86_64                                                                         323/670 
  Installing : gtk2-2.24.31-1.el7.x86_64                                                                        324/670 
  Installing : librsvg2-2.40.20-1.el7.x86_64                                                                    325/670 
  Installing : gstreamer1-plugins-bad-free-1.10.4-3.el7.x86_64                                                  326/670 
  Installing : gstreamer-plugins-base-0.10.36-10.el7.x86_64                                                     327/670 
  Installing : spice-glib-0.35-5.el7_9.1.x86_64                                                                 328/670 
  Installing : pygtk2-2.24.0-9.el7.x86_64                                                                       329/670 
  Installing : pinentry-gtk-0.8.1-17.el7.x86_64                                                                 330/670 
  Installing : pangomm-2.40.1-1.el7.x86_64                                                                      331/670 
  Installing : gstreamer-plugins-bad-free-0.10.23-23.el7.x86_64                                                 332/670 
  Installing : adwaita-gtk2-theme-3.28-2.el7.x86_64                                                             333/670 
  Installing : libglade2-2.6.4-11.el7.x86_64                                                                    334/670 
  Installing : pygtk2-libglade-2.24.0-9.el7.x86_64                                                              335/670 
  Installing : gupnp-dlna-0.10.5-1.el7.x86_64                                                                   336/670 
  Installing : python2-subprocess32-3.2.6-14.el7.x86_64                                                         337/670 
  Installing : appstream-data-7-20180614.el7.noarch                                                             338/670 
  Installing : color-filesystem-1-13.el7.noarch                                                                 339/670 
  Installing : colord-1.3.4-2.el7.x86_64                                                                        340/670 
  Installing : libbytesize-1.2-1.el7.x86_64                                                                     341/670 
  Installing : libblockdev-mdraid-2.18-5.el7.x86_64                                                             342/670 
  Installing : udisks2-2.8.4-1.el7.x86_64                                                                       343/670 
  Installing : libbluray-0.2.3-6.el7.x86_64                                                                     344/670 
  Installing : osinfo-db-20200529-1.el7.noarch                                                                  345/670 
  Installing : libosinfo-1.1.0-5.el7.x86_64                                                                     346/670 
  Installing : dnsmasq-2.76-17.el7_9.3.x86_64                                                                   347/670 
  Installing : yelp-xsl-3.28.0-1.el7.noarch                                                                     348/670 
  Installing : bridge-utils-1.5-9.el7.x86_64                                                                    349/670 
  Installing : netcf-libs-0.2.8-4.el7.x86_64                                                                    350/670 
  Installing : seabios-bin-1.11.0-2.el7.noarch                                                                  351/670 
  Installing : fwupdate-efi-12-6.el7.centos.x86_64                                                              352/670 
  Installing : fwupdate-libs-12-6.el7.centos.x86_64                                                             353/670 
  Installing : gupnp-av-0.12.10-1.el7.x86_64                                                                    354/670 
  Installing : adwaita-cursor-theme-3.28.0-1.el7.noarch                                                         355/670 
  Installing : adwaita-icon-theme-3.28.0-1.el7.noarch                                                           356/670 
  Installing : gnome-themes-standard-3.28-2.el7.x86_64                                                          357/670 
  Installing : xcb-util-keysyms-0.4.0-1.el7.x86_64                                                              358/670 
  Installing : gom-0.4-1.el7.x86_64                                                                             359/670 
  Installing : libgdither-0.6-8.el7.x86_64                                                                      360/670 
  Installing : gavl-1.4.0-4.el7.x86_64                                                                          361/670 
  Installing : frei0r-plugins-1.3-13.el7.x86_64                                                                 362/670 
  Installing : gnome-video-effects-0.4.3-1.el7.noarch                                                           363/670 
  Installing : python-backports-1.0-8.el7.x86_64                                                                364/670 
  Installing : libburn-1.2.8-4.el7.x86_64                                                                       365/670 
  Installing : mtdev-1.1.5-5.el7.x86_64                                                                         366/670 
  Installing : python-ntplib-0.3.2-1.el7.noarch                                                                 367/670 
  Installing : openjpeg2-2.3.1-3.el7_7.x86_64                                                                   368/670 
  Installing : python-inotify-0.9.4-4.el7.noarch                                                                369/670 
  Installing : pcre2-utf16-10.23-2.el7.x86_64                                                                   370/670 
  Installing : qt5-qtbase-common-5.9.7-5.el7_9.noarch                                                           371/670 
  Installing : qt5-qtbase-5.9.7-5.el7_9.x86_64                                                                  372/670 
  Installing : gnome-user-docs-3.28.2-1.el7.noarch                                                              373/670 
  Installing : mtools-4.0.18-5.el7.x86_64                                                                       374/670 
  Installing : mpg123-libs-1.25.6-1.el7.x86_64                                                                  375/670 
  Installing : gstreamer1-plugins-ugly-free-1.10.4-3.el7.x86_64                                                 376/670 
  Installing : unbound-libs-1.6.6-5.el7_8.x86_64                                                                377/670 
  Installing : libreswan-3.25-9.1.el7_8.x86_64                                                                  378/670 
  Installing : NetworkManager-libreswan-1.2.4-2.el7.x86_64                                                      379/670 
  Installing : cyrus-sasl-scram-2.1.26-24.el7_9.x86_64                                                          380/670 
  Installing : cyrus-sasl-gssapi-2.1.26-24.el7_9.x86_64                                                         381/670 
  Installing : python-di-0.3-2.el7.noarch                                                                       382/670 
  Installing : libmodman-2.0.1-8.el7.x86_64                                                                     383/670 
  Installing : libproxy-0.4.11-11.el7.x86_64                                                                    384/670 
  Installing : libreport-web-2.1.11-53.el7.centos.x86_64                                                        385/670 
  Installing : libreport-plugin-reportuploader-2.1.11-53.el7.centos.x86_64                                      386/670 
  Installing : libreport-plugin-rhtsupport-2.1.11-53.el7.centos.x86_64                                          387/670 
  Installing : libreport-plugin-mantisbt-2.1.11-53.el7.centos.x86_64                                            388/670 
  Installing : libreport-plugin-bugzilla-2.1.11-53.el7.centos.x86_64                                            389/670 
  Installing : libreport-rhel-anaconda-bugzilla-2.1.11-53.el7.centos.x86_64                                     390/670 
  Installing : libreport-anaconda-2.1.11-53.el7.centos.x86_64                                                   391/670 
  Installing : libreport-centos-2.1.11-53.el7.centos.x86_64                                                     392/670 
  Installing : libreport-plugin-ureport-2.1.11-53.el7.centos.x86_64                                             393/670 
  Installing : abrt-python-2.1.11-60.el7.centos.x86_64                                                          394/670 
  Installing : abrt-2.1.11-60.el7.centos.x86_64                                                                 395/670 
  Installing : abrt-dbus-2.1.11-60.el7.centos.x86_64                                                            396/670 
  Installing : abrt-addon-kerneloops-2.1.11-60.el7.centos.x86_64                                                397/670 
  Installing : abrt-addon-pstoreoops-2.1.11-60.el7.centos.x86_64                                                398/670 
  Installing : abrt-addon-vmcore-2.1.11-60.el7.centos.x86_64                                                    399/670 
  Installing : abrt-retrace-client-2.1.11-60.el7.centos.x86_64                                                  400/670 
  Installing : abrt-addon-ccpp-2.1.11-60.el7.centos.x86_64                                                      401/670 
  Installing : abrt-addon-xorg-2.1.11-60.el7.centos.x86_64                                                      402/670 
  Installing : abrt-addon-python-2.1.11-60.el7.centos.x86_64                                                    403/670 
  Installing : glib-networking-2.56.1-1.el7.x86_64                                                              404/670 
  Installing : libsoup-2.62.2-2.el7.x86_64                                                                      405/670 
  Installing : geocode-glib-3.26.0-3.el7.x86_64                                                                 406/670 
  Installing : rest-0.8.1-2.el7.x86_64                                                                          407/670 
  Installing : gtk3-3.22.30-8.el7_9.x86_64                                                                      408/670 
  Installing : gcr-3.28.0-1.el7.x86_64                                                                          409/670 
  Installing : libcanberra-gtk3-0.30-9.el7.x86_64                                                               410/670 
  Installing : nautilus-extensions-3.26.3.1-7.el7.x86_64                                                        411/670 
  Installing : libgweather-3.28.2-4.el7_9.x86_64                                                                412/670 
  Installing : libnma-1.8.6-2.el7.x86_64                                                                        413/670 
  Installing : libreport-gtk-2.1.11-53.el7.centos.x86_64                                                        414/670 
  Installing : zenity-3.28.1-2.el7_9.x86_64                                                                     415/670 
  Installing : geoclue2-2.4.8-1.el7.x86_64                                                                      416/670 
  Installing : webkitgtk4-jsc-2.28.2-3.el7.x86_64                                                               417/670 
  Installing : webkitgtk4-2.28.2-3.el7.x86_64                                                                   418/670 
  Installing : gnome-online-accounts-3.28.2-1.el7.x86_64                                                        419/670 
  Installing : geoclue2-libs-2.4.8-1.el7.x86_64                                                                 420/670 
  Installing : libgdata-0.17.9-1.el7.x86_64                                                                     421/670 
  Installing : evolution-data-server-langpacks-3.28.5-5.el7_9.1.noarch                                          422/670 
  Installing : evolution-data-server-3.28.5-5.el7_9.1.x86_64                                                    423/670 
  Installing : libgnomekbd-3.26.0-3.el7.x86_64                                                                  424/670 
  Installing : gtksourceview3-3.24.8-2.el7.x86_64                                                               425/670 
  Installing : grilo-0.3.6-1.el7.x86_64                                                                         426/670 
  Installing : libpeas-gtk-1.22.0-1.el7.x86_64                                                                  427/670 
  Installing : gssdp-1.0.2-1.el7.x86_64                                                                         428/670 
  Installing : gupnp-1.0.2-6.el7_9.x86_64                                                                       429/670 
  Installing : gupnp-igd-0.2.5-2.el7.x86_64                                                                     430/670 
  Installing : libnice-0.1.3-4.el7.x86_64                                                                       431/670 
  Installing : gstreamer1-plugins-good-1.10.4-2.el7.x86_64                                                      432/670 
  Installing : farstream02-0.2.3-3.el7.x86_64                                                                   433/670 
  Installing : dleyna-core-0.5.0-1.el7.x86_64                                                                   434/670 
  Installing : 1:folks-0.11.4-1.el7.x86_64                                                                      435/670 
  Installing : nm-connection-editor-1.8.6-2.el7.x86_64                                                          436/670 
  Installing : brasero-libs-3.12.2-5.el7_9.1.x86_64                                                             437/670 
  Installing : 1:gnome-bluetooth-libs-3.28.2-1.el7.x86_64                                                       438/670 
  Installing : gtk-vnc2-0.7.0-3.el7.x86_64                                                                      439/670 
  Installing : colord-gtk-0.1.25-4.el7.x86_64                                                                   440/670 
  Installing : spice-gtk3-0.35-5.el7_9.1.x86_64                                                                 441/670 
  Installing : gspell-1.6.1-1.el7.x86_64                                                                        442/670 
  Installing : abrt-gui-libs-2.1.11-60.el7.centos.x86_64                                                        443/670 
  Installing : gnome-packagekit-common-3.28.0-1.el7.x86_64                                                      444/670 
  Installing : gnome-packagekit-installer-3.28.0-1.el7.x86_64                                                   445/670 
  Installing : gnome-packagekit-updater-3.28.0-1.el7.x86_64                                                     446/670 
  Installing : dleyna-connector-dbus-0.2.0-2.el7.x86_64                                                         447/670 
  Installing : dleyna-server-0.5.0-3.el7.x86_64                                                                 448/670 
  Installing : telepathy-farstream-0.6.0-5.el7.x86_64                                                           449/670 
  Installing : telepathy-gabble-0.18.1-4.el7.x86_64                                                             450/670 
  Installing : glade-libs-3.22.1-1.el7.x86_64                                                                   451/670 
  Installing : anaconda-widgets-21.48.22.159-1.el7.centos.x86_64                                                452/670 
  Installing : 2:yelp-libs-3.28.1-1.el7.x86_64                                                                  453/670 
  Installing : 2:yelp-3.28.1-1.el7.x86_64                                                                       454/670 
  Installing : webkitgtk3-2.4.11-2.el7.x86_64                                                                   455/670 
  Installing : python-meh-gui-0.25.3-1.el7.noarch                                                               456/670 
  Installing : libcanberra-gtk2-0.30-9.el7.x86_64                                                               457/670 
  Installing : metacity-2.34.13-7.el7.x86_64                                                                    458/670 
  Installing : gnome-keyring-3.28.2-1.el7.x86_64                                                                459/670 
  Installing : gnome-keyring-pam-3.28.2-1.el7.x86_64                                                            460/670 
  Installing : gucharmap-libs-10.0.4-1.el7.x86_64                                                               461/670 
  Installing : avahi-ui-gtk3-0.6.31-20.el7.x86_64                                                               462/670 
  Installing : compat-gnome-desktop314-3.14.2-1.el7.x86_64                                                      463/670 
  Installing : keybinder3-0.3.0-1.el7.x86_64                                                                    464/670 
  Installing : libnm-gtk-1.8.6-2.el7.x86_64                                                                     465/670 
  Installing : vino-3.22.0-7.el7.x86_64                                                                         466/670 
  Installing : gtkmm30-3.22.2-1.el7.x86_64                                                                      467/670 
  Installing : libtimezonemap-0.4.4-2.el7_9.x86_64                                                              468/670 
  Installing : libgovirt-0.3.4-5.el7.x86_64                                                                     469/670 
  Installing : telepathy-salut-0.8.1-6.el7.x86_64                                                               470/670 
  Installing : gstreamer-plugins-good-0.10.31-13.el7.x86_64                                                     471/670 
  Installing : farstream-0.1.2-8.el7.x86_64                                                                     472/670 
  Installing : libpurple-2.10.11-9.el7.x86_64                                                                   473/670 
  Installing : telepathy-haze-0.8.0-1.el7.x86_64                                                                474/670 
  Installing : libdmapsharing-2.9.37-1.el7.x86_64                                                               475/670 
  Installing : neon-0.30.0-4.el7.x86_64                                                                         476/670 
  Installing : libmusicbrainz5-5.0.1-9.el7.x86_64                                                               477/670 
  Installing : 1:net-snmp-libs-5.7.2-49.el7_9.2.x86_64                                                          478/670 
  Installing : redhat-menus-12.0.2-8.el7.noarch                                                                 479/670 
  Installing : gnome-menus-3.13.3-3.el7.x86_64                                                                  480/670 
  Installing : vte-profile-0.52.4-1.el7.x86_64                                                                  481/670 
  Installing : vte291-0.52.4-1.el7.x86_64                                                                       482/670 
  Installing : gnome-terminal-3.28.2-3.el7.x86_64                                                               483/670 
  Installing : libwacom-data-0.30-1.el7.noarch                                                                  484/670 
  Installing : libwacom-0.30-1.el7.x86_64                                                                       485/670 
  Installing : libinput-1.10.7-2.el7.x86_64                                                                     486/670 
  Installing : clutter-1.26.2-2.el7.x86_64                                                                      487/670 
  Installing : clutter-gtk-1.8.4-1.el7.x86_64                                                                   488/670 
  Installing : clutter-gst3-3.0.26-1.el7.x86_64                                                                 489/670 
  Installing : libchamplain-0.12.16-2.el7.x86_64                                                                490/670 
  Installing : clutter-gst2-2.0.18-1.el7.x86_64                                                                 491/670 
  Installing : libchamplain-gtk-0.12.16-2.el7.x86_64                                                            492/670 
  Installing : 1:sgabios-bin-0.20110622svn-4.el7.noarch                                                         493/670 
  Installing : cyrus-sasl-2.1.26-24.el7_9.x86_64                                                                494/670 
  Installing : libvirt-libs-4.5.0-36.el7_9.5.x86_64                                                             495/670 
  Installing : libvirt-daemon-4.5.0-36.el7_9.5.x86_64                                                           496/670 
  Installing : libvirt-daemon-driver-storage-core-4.5.0-36.el7_9.5.x86_64                                       497/670 
  Installing : libvirt-daemon-driver-storage-disk-4.5.0-36.el7_9.5.x86_64                                       498/670 
  Installing : libvirt-daemon-driver-storage-gluster-4.5.0-36.el7_9.5.x86_64                                    499/670 
  Installing : libvirt-daemon-driver-storage-rbd-4.5.0-36.el7_9.5.x86_64                                        500/670 
  Installing : libvirt-daemon-driver-storage-iscsi-4.5.0-36.el7_9.5.x86_64                                      501/670 
  Installing : libvirt-daemon-driver-storage-logical-4.5.0-36.el7_9.5.x86_64                                    502/670 
  Installing : libvirt-daemon-driver-storage-mpath-4.5.0-36.el7_9.5.x86_64                                      503/670 
  Installing : libvirt-daemon-driver-storage-scsi-4.5.0-36.el7_9.5.x86_64                                       504/670 
  Installing : libvirt-daemon-driver-storage-4.5.0-36.el7_9.5.x86_64                                            505/670 
  Installing : libvirt-daemon-driver-nwfilter-4.5.0-36.el7_9.5.x86_64                                           506/670 
  Installing : libvirt-daemon-driver-interface-4.5.0-36.el7_9.5.x86_64                                          507/670 
  Installing : libvirt-daemon-driver-nodedev-4.5.0-36.el7_9.5.x86_64                                            508/670 
  Installing : libvirt-daemon-driver-secret-4.5.0-36.el7_9.5.x86_64                                             509/670 
  Installing : libvirt-glib-1.0.0-1.el7.x86_64                                                                  510/670 
  Installing : libvirt-gobject-1.0.0-1.el7.x86_64                                                               511/670 
  Installing : python-ipaddress-1.0.16-2.el7.noarch                                                             512/670 
  Installing : python-backports-ssl_match_hostname-3.5.0.1-1.el7.noarch                                         513/670 
  Installing : python-setuptools-0.9.8-7.el7.noarch                                                             514/670 
  Installing : python-coverage-3.6-0.5.b3.el7.x86_64                                                            515/670 
  Installing : cryptsetup-2.0.3-6.el7.x86_64                                                                    516/670 
  Installing : 1:python-blivet-0.61.15.76-1.el7_9.noarch                                                        517/670 
  Installing : setools-libs-3.3.8-4.el7.x86_64                                                                  518/670 
  Installing : policycoreutils-python-2.5-34.el7.x86_64                                                         519/670 
  Installing : setroubleshoot-server-3.2.30-8.el7.x86_64                                                        520/670 
  Installing : setroubleshoot-plugins-3.0.67-4.el7.noarch                                                       521/670 
  Installing : libuser-python-0.60-9.el7.x86_64                                                                 522/670 
  Installing : hplip-common-3.15.9-5.el7.x86_64                                                                 523/670 
  Installing : usermode-1.111-6.el7.x86_64                                                                      524/670 
  Installing : adobe-mappings-pdf-20180407-1.el7.noarch                                                         525/670 
  Installing : libgs-9.25-5.el7.x86_64                                                                          526/670 
  Installing : libspectre-0.2.8-1.el7.x86_64                                                                    527/670 
  Installing : evince-libs-3.28.2-10.el7.x86_64                                                                 528/670 
  Installing : libiptcdata-1.0.4-11.el7.x86_64                                                                  529/670 
  Installing : tracker-1.10.5-8.el7.x86_64                                                                      530/670 
  Installing : grilo-plugins-0.3.7-1.el7.x86_64                                                                 531/670 
  Installing : brasero-3.12.2-5.el7_9.1.x86_64                                                                  532/670 
  Installing : brasero-nautilus-3.12.2-5.el7_9.1.x86_64                                                         533/670 
  Installing : libgcab1-0.7-4.el7_4.x86_64                                                                      534/670 
  Installing : libappstream-glib-0.7.8-2.el7.x86_64                                                             535/670 
  Installing : flatpak-libs-1.0.9-12.el7_9.x86_64                                                               536/670 
  Installing : xdg-desktop-portal-1.0.2-1.el7.x86_64                                                            537/670 
  Installing : flatpak-1.0.9-12.el7_9.x86_64                                                                    538/670 
  Installing : gnome-desktop3-3.28.2-2.el7.x86_64                                                               539/670 
  Installing : 2:cheese-libs-3.28.0-1.el7.x86_64                                                                540/670 
  Installing : gnome-settings-daemon-3.28.1-11.el7_9.x86_64                                                     541/670 
  Installing : gnome-session-3.28.1-8.el7.x86_64                                                                542/670 
  Installing : mutter-3.28.3-32.el7_9.x86_64                                                                    543/670 
  Installing : evince-3.28.2-10.el7.x86_64                                                                      544/670 
  Installing : xdg-desktop-portal-gtk-1.0.2-1.el7.x86_64                                                        545/670 
  Installing : fwupd-1.0.8-5.el7.x86_64                                                                         546/670 
  Installing : seavgabios-bin-1.11.0-2.el7.noarch                                                               547/670 
  Installing : 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64                                                             548/670 
  Installing : flite-1.3-22.el7.x86_64                                                                          549/670 
  Installing : speech-dispatcher-0.7.1-15.el7.x86_64                                                            550/670 
  Installing : speech-dispatcher-python-0.7.1-15.el7.x86_64                                                     551/670 
  Installing : mozjs52-52.9.0-1.el7.x86_64                                                                      552/670 
  Installing : gjs-1.52.5-1.el7_6.x86_64                                                                        553/670 
  Installing : libXres-1.2.0-1.el7.x86_64                                                                       554/670 
  Installing : libwnck3-3.24.1-2.el7.x86_64                                                                     555/670 
  Installing : ncompress-4.2.4.4-3.1.el7_8.x86_64                                                               556/670 
  Installing : file-roller-3.28.1-2.el7.x86_64                                                                  557/670 
  Installing : radvd-2.17-3.el7.x86_64                                                                          558/670 
  Installing : libvirt-daemon-driver-network-4.5.0-36.el7_9.5.x86_64                                            559/670 
  Installing : libvirt-daemon-driver-qemu-4.5.0-36.el7_9.5.x86_64                                               560/670 
  Installing : libvirt-daemon-kvm-4.5.0-36.el7_9.5.x86_64                                                       561/670 
  Installing : libvirt-daemon-config-network-4.5.0-36.el7_9.5.x86_64                                            562/670 
  Installing : xcb-util-renderutil-0.3.9-3.el7.x86_64                                                           563/670 
  Installing : qt5-qtbase-gui-5.9.7-5.el7_9.x86_64                                                              564/670 
  Installing : adwaita-qt5-1.0-1.el7.x86_64                                                                     565/670 
  Installing : highcontrast-qt5-0.1-2.el7.x86_64                                                                566/670 
  Installing : xdg-user-dirs-0.15-5.el7.x86_64                                                                  567/670 
  Installing : 1:emacs-filesystem-24.3-23.el7_9.1.noarch                                                        568/670 
  Installing : desktop-file-utils-0.23-2.el7.x86_64                                                             569/670 
  Installing : gvfs-1.36.2-7.el7_9.x86_64                                                                       570/670 
  Installing : ibus-gtk2-1.5.17-12.el7_9.x86_64                                                                 571/670 
  Installing : ibus-gtk3-1.5.17-12.el7_9.x86_64                                                                 572/670 
  Installing : ibus-setup-1.5.17-12.el7_9.noarch                                                                573/670 
  Installing : ibus-1.5.17-12.el7_9.x86_64                                                                      574/670 
  Installing : nautilus-3.26.3.1-7.el7.x86_64                                                                   575/670 
  Installing : 1:gnome-bluetooth-3.28.2-1.el7.x86_64                                                            576/670 
  Installing : 1:control-center-3.28.1-8.el7_9.1.x86_64                                                         577/670 
  Installing : gnome-shell-3.28.3-34.el7_9.x86_64                                                               578/670 
  Installing : 1:gdm-3.28.2-26.el7.x86_64                                                                       579/670 
  Installing : pulseaudio-gdm-hooks-10.0-6.el7_9.x86_64                                                         580/670 
  Installing : gnome-shell-extension-common-3.28.1-17.el7_9.noarch                                              581/670 
  Installing : xdg-utils-1.1.0-0.17.20120809git.el7.noarch                                                      582/670 
  Installing : gnome-abrt-0.3.4-9.el7.x86_64                                                                    583/670 
  Installing : abrt-gui-2.1.11-60.el7.centos.x86_64                                                             584/670 
  Installing : gnome-shell-extension-launch-new-instance-3.28.1-17.el7_9.noarch                                 585/670 
  Installing : gnome-shell-extension-window-list-3.28.1-17.el7_9.noarch                                         586/670 
  Installing : gnome-shell-extension-top-icons-3.28.1-17.el7_9.noarch                                           587/670 
  Installing : gnome-shell-extension-alternate-tab-3.28.1-17.el7_9.noarch                                       588/670 
  Installing : gnome-shell-extension-user-theme-3.28.1-17.el7_9.noarch                                          589/670 
  Installing : gnome-shell-extension-apps-menu-3.28.1-17.el7_9.noarch                                           590/670 
  Installing : gnome-shell-extension-places-menu-3.28.1-17.el7_9.noarch                                         591/670 
  Installing : gnome-shell-extension-horizontal-workspaces-3.28.1-17.el7_9.noarch                               592/670 
  Installing : gvfs-fuse-1.36.2-7.el7_9.x86_64                                                                  593/670 
  Installing : 1:totem-3.26.2-1.el7.x86_64                                                                      594/670 
  Installing : libnl-1.1.4-3.el7.x86_64                                                                         595/670 
  Installing : python-ethtool-0.8-8.el7.x86_64                                                                  596/670 
  Installing : libconfig-1.4.9-5.el7.x86_64                                                                     597/670 
  Installing : lldpad-1.0.1-7.git036e314.el7_9.x86_64                                                           598/670 
  Installing : fcoe-utils-1.0.32-2.el7_6.x86_64                                                                 599/670 
  Installing : libXpm-3.5.12-2.el7_9.x86_64                                                                     600/670 
  Installing : gd-2.0.35-27.el7_9.x86_64                                                                        601/670 
  Installing : libgphoto2-2.5.15-3.el7.x86_64                                                                   602/670 
  Installing : sane-backends-libs-1.0.24-12.el7.x86_64                                                          603/670 
  Installing : sane-backends-1.0.24-12.el7.x86_64                                                               604/670 
  Installing : hplip-libs-3.15.9-5.el7.x86_64                                                                   605/670 
  Installing : pytz-2016.10-2.el7.noarch                                                                        606/670 
  Installing : anaconda-tui-21.48.22.159-1.el7.centos.x86_64                                                    607/670 
  Installing : anaconda-core-21.48.22.159-1.el7.centos.x86_64                                                   608/670 
  Installing : anaconda-gui-21.48.22.159-1.el7.centos.x86_64                                                    609/670 
  Installing : initial-setup-0.3.9.45-1.el7.centos.x86_64                                                       610/670 
  Installing : initial-setup-gui-0.3.9.45-1.el7.centos.x86_64                                                   611/670 
  Installing : libsane-hpaio-3.15.9-5.el7.x86_64                                                                612/670 
  Installing : sane-backends-drivers-scanners-1.0.24-12.el7.x86_64                                              613/670 
  Installing : gvfs-gphoto2-1.36.2-7.el7_9.x86_64                                                               614/670 
  Installing : firstboot-19.12-1.el7.x86_64                                                                     615/670 
  Installing : 1:totem-nautilus-3.26.2-1.el7.x86_64                                                             616/670 
  Installing : gnome-classic-session-3.28.1-17.el7_9.noarch                                                     617/670 
  Installing : gnome-tweak-tool-3.28.1-7.el7.noarch                                                             618/670 
  Installing : abrt-desktop-2.1.11-60.el7.centos.x86_64                                                         619/670 
  Installing : setroubleshoot-3.2.30-8.el7.x86_64                                                               620/670 
  Installing : gnome-initial-setup-3.28.0-2.el7_9.1.x86_64                                                      621/670 
  Installing : orca-3.6.3-4.el7.x86_64                                                                          622/670 
  Installing : evince-nautilus-3.28.2-10.el7.x86_64                                                             623/670 
  Installing : gvfs-archive-1.36.2-7.el7_9.x86_64                                                               624/670 
  Installing : gvfs-smb-1.36.2-7.el7_9.x86_64                                                                   625/670 
  Installing : gvfs-afp-1.36.2-7.el7_9.x86_64                                                                   626/670 
  Installing : gvfs-goa-1.36.2-7.el7_9.x86_64                                                                   627/670 
  Installing : 2:gedit-3.28.1-3.el7.x86_64                                                                      628/670 
  Installing : gvfs-mtp-1.36.2-7.el7_9.x86_64                                                                   629/670 
  Installing : gvfs-afc-1.36.2-7.el7_9.x86_64                                                                   630/670 
  Installing : xdg-user-dirs-gtk-0.10-4.el7.x86_64                                                              631/670 
  Installing : qgnomeplatform-0.3-5.el7.x86_64                                                                  632/670 
  Installing : gnome-boxes-3.28.5-4.el7.x86_64                                                                  633/670 
  Installing : file-roller-nautilus-3.28.1-2.el7.x86_64                                                         634/670 
  Installing : gnome-weather-3.26.0-1.el7.noarch                                                                635/670 
  Installing : sushi-3.28.3-1.el7.x86_64                                                                        636/670 
  Installing : gnome-software-3.28.2-3.el7.x86_64                                                               637/670 
  Installing : gnome-session-xsession-3.28.1-8.el7.x86_64                                                       638/670 
  Installing : 2:cheese-3.28.0-1.el7.x86_64                                                                     639/670 
  Installing : empathy-3.12.13-1.el7.x86_64                                                                     640/670 
  Installing : gnome-contacts-3.28.2-1.el7.x86_64                                                               641/670 
  Installing : eog-3.28.3-1.el7.x86_64                                                                          642/670 
  Installing : gnome-clocks-3.28.0-1.el7.x86_64                                                                 643/670 
  Installing : gnome-font-viewer-3.28.0-1.el7.x86_64                                                            644/670 
  Installing : compat-cheese314-3.14.2-1.el7.x86_64                                                             645/670 
  Installing : gnome-terminal-nautilus-3.28.2-3.el7.x86_64                                                      646/670 
  Installing : gnome-color-manager-3.28.0-1.el7.x86_64                                                          647/670 
  Installing : vinagre-3.22.0-14.el7.x86_64                                                                     648/670 
  Installing : gnome-system-monitor-3.28.2-1.el7.x86_64                                                         649/670 
  Installing : NetworkManager-libreswan-gnome-1.2.4-2.el7.x86_64                                                650/670 
  Installing : gucharmap-10.0.4-1.el7.x86_64                                                                    651/670 
  Installing : gnome-packagekit-3.28.0-1.el7.x86_64                                                             652/670 
  Installing : gnome-calculator-3.28.2-1.el7.x86_64                                                             653/670 
  Installing : gnome-disk-utility-3.28.3-1.el7.x86_64                                                           654/670 
  Installing : gnome-screenshot-3.26.0-1.el7.x86_64                                                             655/670 
  Installing : seahorse-3.20.0-1.el7.x86_64                                                                     656/670 
  Installing : 1:gnome-system-log-3.9.90-3.el7.x86_64                                                           657/670 
  Installing : PackageKit-gtk3-module-1.1.10-2.el7.centos.x86_64                                                658/670 
  Installing : baobab-3.28.0-2.el7.x86_64                                                                       659/670 
  Installing : mousetweaks-3.12.0-1.el7.x86_64                                                                  660/670 
  Installing : gnome-dictionary-3.26.1-2.el7.x86_64                                                             661/670 
  Installing : firewall-config-0.6.3-13.el7_9.noarch                                                            662/670 
  Installing : libproxy-mozjs-0.4.11-11.el7.x86_64                                                              663/670 
  Installing : gnome-getting-started-docs-3.28.2-1.el7.noarch                                                   664/670 
  Installing : fprintd-pam-0.8.1-2.el7.x86_64                                                                   665/670 
  Installing : gnome-icon-theme-symbolic-3.12.0-2.el7.noarch                                                    666/670 
  Installing : gnome-icon-theme-extras-3.12.0-1.el7.noarch                                                      667/670 
  Installing : PackageKit-command-not-found-1.1.10-2.el7.centos.x86_64                                          668/670 
  Installing : avahi-0.6.31-20.el7.x86_64                                                                       669/670 
  Installing : 1:nautilus-sendto-3.8.6-1.el7.x86_64                                                             670/670 
  Verifying  : gnome-initial-setup-3.28.0-2.el7_9.1.x86_64                                                        1/670 
  Verifying  : 1:xorg-x11-font-utils-7.5-21.el7.x86_64                                                            2/670 
  Verifying  : libgnomekbd-3.26.0-3.el7.x86_64                                                                    3/670 
  Verifying  : pytz-2016.10-2.el7.noarch                                                                          4/670 
  Verifying  : gvfs-archive-1.36.2-7.el7_9.x86_64                                                                 5/670 
  Verifying  : gnome-color-manager-3.28.0-1.el7.x86_64                                                            6/670 
  Verifying  : urw-base35-d050000l-fonts-20170801-10.el7.noarch                                                   7/670 
  Verifying  : oddjob-mkhomedir-0.31.5-4.el7.x86_64                                                               8/670 
  Verifying  : libXpm-3.5.12-2.el7_9.x86_64                                                                       9/670 
  Verifying  : colord-libs-1.3.4-2.el7.x86_64                                                                    10/670 
  Verifying  : xdg-user-dirs-gtk-0.10-4.el7.x86_64                                                               11/670 
  Verifying  : adobe-mappings-cmap-20171205-3.el7.noarch                                                         12/670 
  Verifying  : 1:totem-nautilus-3.26.2-1.el7.x86_64                                                              13/670 
  Verifying  : libcdio-0.92-3.el7.x86_64                                                                         14/670 
  Verifying  : openjpeg-libs-1.5.1-18.el7.x86_64                                                                 15/670 
  Verifying  : langtable-data-0.0.31-4.el7.noarch                                                                16/670 
  Verifying  : orc-0.4.26-1.el7.x86_64                                                                           17/670 
  Verifying  : realmd-0.16.1-12.el7_9.1.x86_64                                                                   18/670 
  Verifying  : libconfig-1.4.9-5.el7.x86_64                                                                      19/670 
  Verifying  : NetworkManager-libreswan-gnome-1.2.4-2.el7.x86_64                                                 20/670 
  Verifying  : deltarpm-3.6-3.el7.x86_64                                                                         21/670 
  Verifying  : dejavu-sans-fonts-2.33-6.el7.noarch                                                               22/670 
  Verifying  : abattis-cantarell-fonts-0.0.25-1.el7.noarch                                                       23/670 
  Verifying  : brasero-nautilus-3.12.2-5.el7_9.1.x86_64                                                          24/670 
  Verifying  : python-deltarpm-3.6-3.el7.x86_64                                                                  25/670 
  Verifying  : 1:totem-3.26.2-1.el7.x86_64                                                                       26/670 
  Verifying  : libnl-1.1.4-3.el7.x86_64                                                                          27/670 
  Verifying  : 1:gnome-system-log-3.9.90-3.el7.x86_64                                                            28/670 
  Verifying  : libcanberra-gtk2-0.30-9.el7.x86_64                                                                29/670 
  Verifying  : libtar-1.2.11-29.el7.x86_64                                                                       30/670 
  Verifying  : nm-connection-editor-1.8.6-2.el7.x86_64                                                           31/670 
  Verifying  : 1:emacs-filesystem-24.3-23.el7_9.1.noarch                                                         32/670 
  Verifying  : brasero-libs-3.12.2-5.el7_9.1.x86_64                                                              33/670 
  Verifying  : sane-backends-libs-1.0.24-12.el7.x86_64                                                           34/670 
  Verifying  : python-augeas-0.5.0-2.el7.noarch                                                                  35/670 
  Verifying  : festival-freebsoft-utils-0.10-7.el7.noarch                                                        36/670 
  Verifying  : xcb-util-renderutil-0.3.9-3.el7.x86_64                                                            37/670 
  Verifying  : libreport-python-2.1.11-53.el7.centos.x86_64                                                      38/670 
  Verifying  : gavl-1.4.0-4.el7.x86_64                                                                           39/670 
  Verifying  : radvd-2.17-3.el7.x86_64                                                                           40/670 
  Verifying  : urw-base35-standard-symbols-ps-fonts-20170801-10.el7.noarch                                       41/670 
  Verifying  : liblouis-python-2.5.2-12.el7_4.noarch                                                             42/670 
  Verifying  : file-roller-3.28.1-2.el7.x86_64                                                                   43/670 
  Verifying  : gtk-vnc2-0.7.0-3.el7.x86_64                                                                       44/670 
  Verifying  : ncompress-4.2.4.4-3.1.el7_8.x86_64                                                                45/670 
  Verifying  : libreport-filesystem-2.1.11-53.el7.centos.x86_64                                                  46/670 
  Verifying  : colord-gtk-0.1.25-4.el7.x86_64                                                                    47/670 
  Verifying  : sane-backends-1.0.24-12.el7.x86_64                                                                48/670 
  Verifying  : 1:pyparted-3.9-15.el7.x86_64                                                                      49/670 
  Verifying  : libXres-1.2.0-1.el7.x86_64                                                                        50/670 
  Verifying  : fprintd-pam-0.8.1-2.el7.x86_64                                                                    51/670 
  Verifying  : libreport-rhel-anaconda-bugzilla-2.1.11-53.el7.centos.x86_64                                      52/670 
  Verifying  : gsm-1.0.13-11.el7.x86_64                                                                          53/670 
  Verifying  : abrt-addon-pstoreoops-2.1.11-60.el7.centos.x86_64                                                 54/670 
  Verifying  : anaconda-tui-21.48.22.159-1.el7.centos.x86_64                                                     55/670 
  Verifying  : gssdp-1.0.2-1.el7.x86_64                                                                          56/670 
  Verifying  : setroubleshoot-plugins-3.0.67-4.el7.noarch                                                        57/670 
  Verifying  : libgtop2-2.38.0-3.el7.x86_64                                                                      58/670 
  Verifying  : 1:libglvnd-egl-1.0.1-0.8.git5baa1e5.el7.x86_64                                                    59/670 
  Verifying  : gnome-shell-extension-launch-new-instance-3.28.1-17.el7_9.noarch                                  60/670 
  Verifying  : 2:libogg-1.3.0-7.el7.x86_64                                                                       61/670 
  Verifying  : atk-2.28.1-2.el7.x86_64                                                                           62/670 
  Verifying  : gucharmap-10.0.4-1.el7.x86_64                                                                     63/670 
  Verifying  : 1:libvorbis-1.3.3-8.el7.1.x86_64                                                                  64/670 
  Verifying  : gdk-pixbuf2-2.36.12-3.el7.x86_64                                                                  65/670 
  Verifying  : libieee1284-0.2.11-15.el7.x86_64                                                                  66/670 
  Verifying  : python-ethtool-0.8-8.el7.x86_64                                                                   67/670 
  Verifying  : gstreamer1-1.10.4-2.el7.x86_64                                                                    68/670 
  Verifying  : hunspell-1.3.2-16.el7.x86_64                                                                      69/670 
  Verifying  : at-spi2-core-2.28.0-1.el7.x86_64                                                                  70/670 
  Verifying  : gvfs-smb-1.36.2-7.el7_9.x86_64                                                                    71/670 
  Verifying  : nautilus-extensions-3.26.3.1-7.el7.x86_64                                                         72/670 
  Verifying  : libgsf-1.14.26-7.el7.x86_64                                                                       73/670 
  Verifying  : mozjs52-52.9.0-1.el7.x86_64                                                                       74/670 
  Verifying  : libpeas-1.22.0-1.el7.x86_64                                                                       75/670 
  Verifying  : lzop-1.03-10.el7.x86_64                                                                           76/670 
  Verifying  : gstreamer1-plugins-bad-free-1.10.4-3.el7.x86_64                                                   77/670 
  Verifying  : accountsservice-libs-0.6.50-7.el7.x86_64                                                          78/670 
  Verifying  : flite-1.3-22.el7.x86_64                                                                           79/670 
  Verifying  : pygobject2-2.28.6-11.el7.x86_64                                                                   80/670 
  Verifying  : glib-networking-2.56.1-1.el7.x86_64                                                               81/670 
  Verifying  : libiscsi-1.9.0-7.el7.x86_64                                                                       82/670 
  Verifying  : gvfs-afp-1.36.2-7.el7_9.x86_64                                                                    83/670 
  Verifying  : libgdata-0.17.9-1.el7.x86_64                                                                      84/670 
  Verifying  : libvirt-daemon-driver-nwfilter-4.5.0-36.el7_9.5.x86_64                                            85/670 
  Verifying  : libtalloc-2.1.16-1.el7.x86_64                                                                     86/670 
  Verifying  : seavgabios-bin-1.11.0-2.el7.noarch                                                                87/670 
  Verifying  : abrt-libs-2.1.11-60.el7.centos.x86_64                                                             88/670 
  Verifying  : gstreamer-plugins-base-0.10.36-10.el7.x86_64                                                      89/670 
  Verifying  : accountsservice-0.6.50-7.el7.x86_64                                                               90/670 
  Verifying  : libgcab1-0.7-4.el7_4.x86_64                                                                       91/670 
  Verifying  : PackageKit-gtk3-module-1.1.10-2.el7.centos.x86_64                                                 92/670 
  Verifying  : geoclue2-2.4.8-1.el7.x86_64                                                                       93/670 
  Verifying  : spice-gtk3-0.35-5.el7_9.1.x86_64                                                                  94/670 
  Verifying  : libxklavier-5.4-7.el7.x86_64                                                                      95/670 
  Verifying  : ibus-gtk2-1.5.17-12.el7_9.x86_64                                                                  96/670 
  Verifying  : fprintd-0.8.1-2.el7.x86_64                                                                        97/670 
  Verifying  : gvfs-gphoto2-1.36.2-7.el7_9.x86_64                                                                98/670 
  Verifying  : gnome-classic-session-3.28.1-17.el7_9.noarch                                                      99/670 
  Verifying  : libreport-cli-2.1.11-53.el7.centos.x86_64                                                        100/670 
  Verifying  : gnome-boxes-3.28.5-4.el7.x86_64                                                                  101/670 
  Verifying  : upower-0.99.7-1.el7.x86_64                                                                       102/670 
  Verifying  : initial-setup-gui-0.3.9.45-1.el7.centos.x86_64                                                   103/670 
  Verifying  : ibus-gtk3-1.5.17-12.el7_9.x86_64                                                                 104/670 
  Verifying  : libavc1394-0.5.3-14.el7.x86_64                                                                   105/670 
  Verifying  : ModemManager-glib-1.6.10-4.el7.x86_64                                                            106/670 
  Verifying  : libmtp-1.1.14-1.el7.x86_64                                                                       107/670 
  Verifying  : urw-base35-gothic-fonts-20170801-10.el7.noarch                                                   108/670 
  Verifying  : adwaita-icon-theme-3.28.0-1.el7.noarch                                                           109/670 
  Verifying  : libpeas-loader-python-1.22.0-1.el7.x86_64                                                        110/670 
  Verifying  : libusal-1.1.11-25.el7.x86_64                                                                     111/670 
  Verifying  : fuse-2.9.2-11.el7.x86_64                                                                         112/670 
  Verifying  : xdg-desktop-portal-gtk-1.0.2-1.el7.x86_64                                                        113/670 
  Verifying  : boost-random-1.53.0-28.el7.x86_64                                                                114/670 
  Verifying  : gnome-weather-3.26.0-1.el7.noarch                                                                115/670 
  Verifying  : urw-base35-nimbus-roman-fonts-20170801-10.el7.noarch                                             116/670 
  Verifying  : gtk2-2.24.31-1.el7.x86_64                                                                        117/670 
  Verifying  : 1:nautilus-sendto-3.8.6-1.el7.x86_64                                                             118/670 
  Verifying  : libvirt-daemon-driver-qemu-4.5.0-36.el7_9.5.x86_64                                               119/670 
  Verifying  : festival-speechtools-libs-1.2.96-28.el7.x86_64                                                   120/670 
  Verifying  : anaconda-core-21.48.22.159-1.el7.centos.x86_64                                                   121/670 
  Verifying  : metacity-2.34.13-7.el7.x86_64                                                                    122/670 
  Verifying  : atkmm-2.24.2-1.el7.x86_64                                                                        123/670 
  Verifying  : libwayland-egl-1.15.0-1.el7.x86_64                                                               124/670 
  Verifying  : abrt-addon-kerneloops-2.1.11-60.el7.centos.x86_64                                                125/670 
  Verifying  : libshout-2.2.2-11.el7.x86_64                                                                     126/670 
  Verifying  : libiptcdata-1.0.4-11.el7.x86_64                                                                  127/670 
  Verifying  : pcre2-10.23-2.el7.x86_64                                                                         128/670 
  Verifying  : libusbx-1.0.21-1.el7.x86_64                                                                      129/670 
  Verifying  : flac-libs-1.3.0-5.el7_1.x86_64                                                                   130/670 
  Verifying  : evince-3.28.2-10.el7.x86_64                                                                      131/670 
  Verifying  : gtksourceview3-3.24.8-2.el7.x86_64                                                               132/670 
  Verifying  : urw-base35-nimbus-mono-ps-fonts-20170801-10.el7.noarch                                           133/670 
  Verifying  : gvnc-0.7.0-3.el7.x86_64                                                                          134/670 
  Verifying  : 1:librados2-10.2.5-4.el7.x86_64                                                                  135/670 
  Verifying  : libwayland-cursor-1.15.0-1.el7.x86_64                                                            136/670 
  Verifying  : pulseaudio-10.0-6.el7_9.x86_64                                                                   137/670 
  Verifying  : pulseaudio-libs-glib2-10.0-6.el7_9.x86_64                                                        138/670 
  Verifying  : pangomm-2.40.1-1.el7.x86_64                                                                      139/670 
  Verifying  : adobe-mappings-pdf-20180407-1.el7.noarch                                                         140/670 
  Verifying  : evolution-data-server-3.28.5-5.el7_9.1.x86_64                                                    141/670 
  Verifying  : setroubleshoot-3.2.30-8.el7.x86_64                                                               142/670 
  Verifying  : GConf2-3.2.6-8.el7.x86_64                                                                        143/670 
  Verifying  : libchamplain-gtk-0.12.16-2.el7.x86_64                                                            144/670 
  Verifying  : usermode-1.111-6.el7.x86_64                                                                      145/670 
  Verifying  : xml-common-0.6.3-39.el7.noarch                                                                   146/670 
  Verifying  : libreport-centos-2.1.11-53.el7.centos.x86_64                                                     147/670 
  Verifying  : libiec61883-1.2.0-10.el7.x86_64                                                                  148/670 
  Verifying  : elfutils-0.176-5.el7.x86_64                                                                      149/670 
  Verifying  : harfbuzz-icu-1.7.5-2.el7.x86_64                                                                  150/670 
  Verifying  : hplip-common-3.15.9-5.el7.x86_64                                                                 151/670 
  Verifying  : webkitgtk4-2.28.2-3.el7.x86_64                                                                   152/670 
  Verifying  : fwupdate-libs-12-6.el7.centos.x86_64                                                             153/670 
  Verifying  : 2:nmap-ncat-6.40-19.el7.x86_64                                                                   154/670 
  Verifying  : gnome-getting-started-docs-3.28.2-1.el7.noarch                                                   155/670 
  Verifying  : gstreamer1-plugins-base-1.10.4-2.el7.x86_64                                                      156/670 
  Verifying  : python-coverage-3.6-0.5.b3.el7.x86_64                                                            157/670 
  Verifying  : gnome-video-effects-0.4.3-1.el7.noarch                                                           158/670 
  Verifying  : libvpx-1.3.0-8.el7.x86_64                                                                        159/670 
  Verifying  : gupnp-1.0.2-6.el7_9.x86_64                                                                       160/670 
  Verifying  : festival-1.96-28.el7.x86_64                                                                      161/670 
  Verifying  : abrt-desktop-2.1.11-60.el7.centos.x86_64                                                         162/670 
  Verifying  : avahi-gobject-0.6.31-20.el7.x86_64                                                               163/670 
  Verifying  : libuser-python-0.60-9.el7.x86_64                                                                 164/670 
  Verifying  : libdv-1.0.0-17.el7.x86_64                                                                        165/670 
  Verifying  : 1:dbus-x11-1.10.24-15.el7.x86_64                                                                 166/670 
  Verifying  : libplist-1.12-3.el7.x86_64                                                                       167/670 
  Verifying  : gnome-shell-extension-window-list-3.28.1-17.el7_9.noarch                                         168/670 
  Verifying  : adobe-mappings-cmap-deprecated-20171205-3.el7.noarch                                             169/670 
  Verifying  : eog-3.28.3-1.el7.x86_64                                                                          170/670 
  Verifying  : abrt-gui-2.1.11-60.el7.centos.x86_64                                                             171/670 
  Verifying  : libXcomposite-0.4.4-4.1.el7.x86_64                                                               172/670 
  Verifying  : langtable-python-0.0.31-4.el7.noarch                                                             173/670 
  Verifying  : libtevent-0.9.39-1.el7.x86_64                                                                    174/670 
  Verifying  : setools-libs-3.3.8-4.el7.x86_64                                                                  175/670 
  Verifying  : 2:cheese-3.28.0-1.el7.x86_64                                                                     176/670 
  Verifying  : 1:folks-0.11.4-1.el7.x86_64                                                                      177/670 
  Verifying  : librsvg2-2.40.20-1.el7.x86_64                                                                    178/670 
  Verifying  : libao-1.1.0-8.el7.x86_64                                                                         179/670 
  Verifying  : wodim-1.1.11-25.el7.x86_64                                                                       180/670 
  Verifying  : gucharmap-libs-10.0.4-1.el7.x86_64                                                               181/670 
  Verifying  : evince-nautilus-3.28.2-10.el7.x86_64                                                             182/670 
  Verifying  : ibus-1.5.17-12.el7_9.x86_64                                                                      183/670 
  Verifying  : ndctl-libs-65-6.el7_9.x86_64                                                                     184/670 
  Verifying  : telepathy-glib-0.24.1-1.el7.x86_64                                                               185/670 
  Verifying  : libcanberra-0.30-9.el7.x86_64                                                                    186/670 
  Verifying  : cryptsetup-2.0.3-6.el7.x86_64                                                                    187/670 
  Verifying  : avahi-ui-gtk3-0.6.31-20.el7.x86_64                                                               188/670 
  Verifying  : brlapi-0.6.0-16.el7.x86_64                                                                       189/670 
  Verifying  : gsettings-desktop-schemas-3.28.0-3.el7.x86_64                                                    190/670 
  Verifying  : gperftools-libs-2.6.1-1.el7.x86_64                                                               191/670 
  Verifying  : python-ipaddress-1.0.16-2.el7.noarch                                                             192/670 
  Verifying  : gvfs-goa-1.36.2-7.el7_9.x86_64                                                                   193/670 
  Verifying  : gnome-shell-extension-common-3.28.1-17.el7_9.noarch                                              194/670 
  Verifying  : geoclue2-libs-2.4.8-1.el7.x86_64                                                                 195/670 
  Verifying  : dleyna-connector-dbus-0.2.0-2.el7.x86_64                                                         196/670 
  Verifying  : at-spi2-atk-2.26.2-1.el7.x86_64                                                                  197/670 
  Verifying  : glade-libs-3.22.1-1.el7.x86_64                                                                   198/670 
  Verifying  : libblockdev-part-2.18-5.el7.x86_64                                                               199/670 
  Verifying  : libgs-9.25-5.el7.x86_64                                                                          200/670 
  Verifying  : compat-libcolord1-1.0.4-1.el7.x86_64                                                             201/670 
  Verifying  : libtdb-1.3.18-1.el7.x86_64                                                                       202/670 
  Verifying  : libibverbs-22.4-6.el7_9.x86_64                                                                   203/670 
  Verifying  : cyrus-sasl-2.1.26-24.el7_9.x86_64                                                                204/670 
  Verifying  : colord-1.3.4-2.el7.x86_64                                                                        205/670 
  Verifying  : 1:gnome-bluetooth-3.28.2-1.el7.x86_64                                                            206/670 
  Verifying  : 1:cups-libs-1.6.3-51.el7.x86_64                                                                  207/670 
  Verifying  : poppler-glib-0.26.5-43.el7.1.x86_64                                                              208/670 
  Verifying  : python2-blockdev-2.18-5.el7.x86_64                                                               209/670 
  Verifying  : libldb-1.5.4-2.el7.x86_64                                                                        210/670 
  Verifying  : 1:sgabios-bin-0.20110622svn-4.el7.noarch                                                         211/670 
  Verifying  : seahorse-3.20.0-1.el7.x86_64                                                                     212/670 
  Verifying  : farstream02-0.2.3-3.el7.x86_64                                                                   213/670 
  Verifying  : libwacom-data-0.30-1.el7.noarch                                                                  214/670 
  Verifying  : vte-profile-0.52.4-1.el7.x86_64                                                                  215/670 
  Verifying  : gvfs-fuse-1.36.2-7.el7_9.x86_64                                                                  216/670 
  Verifying  : gstreamer1-plugins-good-1.10.4-2.el7.x86_64                                                      217/670 
  Verifying  : gnome-session-3.28.1-8.el7.x86_64                                                                218/670 
  Verifying  : redhat-menus-12.0.2-8.el7.noarch                                                                 219/670 
  Verifying  : 1:net-snmp-libs-5.7.2-49.el7_9.2.x86_64                                                          220/670 
  Verifying  : libmodman-2.0.1-8.el7.x86_64                                                                     221/670 
  Verifying  : compat-gnome-desktop314-3.14.2-1.el7.x86_64                                                      222/670 
  Verifying  : speech-dispatcher-0.7.1-15.el7.x86_64                                                            223/670 
  Verifying  : python-di-0.3-2.el7.noarch                                                                       224/670 
  Verifying  : gnome-session-xsession-3.28.1-8.el7.x86_64                                                       225/670 
  Verifying  : cyrus-sasl-gssapi-2.1.26-24.el7_9.x86_64                                                         226/670 
  Verifying  : libreport-gtk-2.1.11-53.el7.centos.x86_64                                                        227/670 
  Verifying  : cyrus-sasl-scram-2.1.26-24.el7_9.x86_64                                                          228/670 
  Verifying  : vinagre-3.22.0-14.el7.x86_64                                                                     229/670 
  Verifying  : 1:vorbis-tools-1.4.0-13.el7.x86_64                                                               230/670 
  Verifying  : libsmbclient-4.10.16-24.el7_9.x86_64                                                             231/670 
  Verifying  : gstreamer1-plugins-ugly-free-1.10.4-3.el7.x86_64                                                 232/670 
  Verifying  : festival-lib-1.96-28.el7.x86_64                                                                  233/670 
  Verifying  : 1:NetworkManager-glib-1.18.8-2.el7_9.x86_64                                                      234/670 
  Verifying  : 2:gedit-3.28.1-3.el7.x86_64                                                                      235/670 
  Verifying  : libcanberra-gtk3-0.30-9.el7.x86_64                                                               236/670 
  Verifying  : totem-pl-parser-3.26.1-1.el7.x86_64                                                              237/670 
  Verifying  : unbound-libs-1.6.6-5.el7_8.x86_64                                                                238/670 
  Verifying  : gnome-keyring-3.28.2-1.el7.x86_64                                                                239/670 
  Verifying  : libspectre-0.2.8-1.el7.x86_64                                                                    240/670 
  Verifying  : adwaita-gtk2-theme-3.28-2.el7.x86_64                                                             241/670 
  Verifying  : glusterfs-libs-6.0-61.el7.x86_64                                                                 242/670 
  Verifying  : exempi-2.2.0-9.el7.x86_64                                                                        243/670 
  Verifying  : libappstream-glib-0.7.8-2.el7.x86_64                                                             244/670 
  Verifying  : gspell-1.6.1-1.el7.x86_64                                                                        245/670 
  Verifying  : gvfs-mtp-1.36.2-7.el7_9.x86_64                                                                   246/670 
  Verifying  : fontconfig-2.13.0-4.3.el7.x86_64                                                                 247/670 
  Verifying  : boost-thread-1.53.0-28.el7.x86_64                                                                248/670 
  Verifying  : libvirt-daemon-driver-storage-core-4.5.0-36.el7_9.5.x86_64                                       249/670 
  Verifying  : keybinder3-0.3.0-1.el7.x86_64                                                                    250/670 
  Verifying  : startup-notification-0.12-8.el7.x86_64                                                           251/670 
  Verifying  : 10:qemu-img-1.5.3-175.el7_9.6.x86_64                                                             252/670 
  Verifying  : gnome-software-3.28.2-3.el7.x86_64                                                               253/670 
  Verifying  : libblockdev-mdraid-2.18-5.el7.x86_64                                                             254/670 
  Verifying  : hplip-libs-3.15.9-5.el7.x86_64                                                                   255/670 
  Verifying  : samba-common-4.10.16-24.el7_9.noarch                                                             256/670 
  Verifying  : gnome-packagekit-installer-3.28.0-1.el7.x86_64                                                   257/670 
  Verifying  : mpg123-libs-1.25.6-1.el7.x86_64                                                                  258/670 
  Verifying  : grilo-0.3.6-1.el7.x86_64                                                                         259/670 
  Verifying  : libreport-plugin-reportuploader-2.1.11-53.el7.centos.x86_64                                      260/670 
  Verifying  : mtools-4.0.18-5.el7.x86_64                                                                       261/670 
  Verifying  : farstream-0.1.2-8.el7.x86_64                                                                     262/670 
  Verifying  : gnome-tweak-tool-3.28.1-7.el7.noarch                                                             263/670 
  Verifying  : 1:gnome-bluetooth-libs-3.28.2-1.el7.x86_64                                                       264/670 
  Verifying  : gupnp-igd-0.2.5-2.el7.x86_64                                                                     265/670 
  Verifying  : gnome-user-docs-3.28.2-1.el7.noarch                                                              266/670 
  Verifying  : gstreamer-0.10.36-7.el7.x86_64                                                                   267/670 
  Verifying  : harfbuzz-1.7.5-2.el7.x86_64                                                                      268/670 
  Verifying  : policycoreutils-python-2.5-34.el7.x86_64                                                         269/670 
  Verifying  : rest-0.8.1-2.el7.x86_64                                                                          270/670 
  Verifying  : flatpak-1.0.9-12.el7_9.x86_64                                                                    271/670 
  Verifying  : libcdio-paranoia-10.2+0.90-11.el7.x86_64                                                         272/670 
  Verifying  : gnome-packagekit-updater-3.28.0-1.el7.x86_64                                                     273/670 
  Verifying  : avahi-0.6.31-20.el7.x86_64                                                                       274/670 
  Verifying  : gd-2.0.35-27.el7_9.x86_64                                                                        275/670 
  Verifying  : pcre2-utf16-10.23-2.el7.x86_64                                                                   276/670 
  Verifying  : speech-dispatcher-python-0.7.1-15.el7.x86_64                                                     277/670 
  Verifying  : gnome-shell-extension-top-icons-3.28.1-17.el7_9.noarch                                           278/670 
  Verifying  : libnm-gtk-1.8.6-2.el7.x86_64                                                                     279/670 
  Verifying  : compat-cheese314-3.14.2-1.el7.x86_64                                                             280/670 
  Verifying  : libpurple-2.10.11-9.el7.x86_64                                                                   281/670 
  Verifying  : festvox-slt-arctic-hts-0.20061229-28.el7.noarch                                                  282/670 
  Verifying  : gdisk-0.8.10-3.el7.x86_64                                                                        283/670 
  Verifying  : mdadm-4.1-9.el7_9.x86_64                                                                         284/670 
  Verifying  : mesa-libEGL-18.3.4-12.el7_9.x86_64                                                               285/670 
  Verifying  : anaconda-gui-21.48.22.159-1.el7.centos.x86_64                                                    286/670 
  Verifying  : qt5-qtbase-common-5.9.7-5.el7_9.noarch                                                           287/670 
  Verifying  : libreport-plugin-rhtsupport-2.1.11-53.el7.centos.x86_64                                          288/670 
  Verifying  : python-inotify-0.9.4-4.el7.noarch                                                                289/670 
  Verifying  : abrt-gui-libs-2.1.11-60.el7.centos.x86_64                                                        290/670 
  Verifying  : telepathy-salut-0.8.1-6.el7.x86_64                                                               291/670 
  Verifying  : PackageKit-glib-1.1.10-2.el7.centos.x86_64                                                       292/670 
  Verifying  : libfprint-0.8.2-1.el7.x86_64                                                                     293/670 
  Verifying  : dejavu-fonts-common-2.33-6.el7.noarch                                                            294/670 
  Verifying  : glusterfs-6.0-61.el7.x86_64                                                                      295/670 
  Verifying  : gnome-shell-extension-alternate-tab-3.28.1-17.el7_9.noarch                                       296/670 
  Verifying  : PackageKit-yum-1.1.10-2.el7.centos.x86_64                                                        297/670 
  Verifying  : libvirt-daemon-driver-storage-disk-4.5.0-36.el7_9.5.x86_64                                       298/670 
  Verifying  : abrt-addon-ccpp-2.1.11-60.el7.centos.x86_64                                                      299/670 
  Verifying  : openjpeg2-2.3.1-3.el7_7.x86_64                                                                   300/670 
  Verifying  : python-ntplib-0.3.2-1.el7.noarch                                                                 301/670 
  Verifying  : libvirt-daemon-driver-storage-gluster-4.5.0-36.el7_9.5.x86_64                                    302/670 
  Verifying  : libreport-web-2.1.11-53.el7.centos.x86_64                                                        303/670 
  Verifying  : libgusb-0.2.9-1.el7.x86_64                                                                       304/670 
  Verifying  : ldns-1.6.16-10.el7.x86_64                                                                        305/670 
  Verifying  : libblockdev-nvdimm-2.18-5.el7.x86_64                                                             306/670 
  Verifying  : gnome-clocks-3.28.0-1.el7.x86_64                                                                 307/670 
  Verifying  : createrepo-0.9.9-28.el7.noarch                                                                   308/670 
  Verifying  : lcms2-2.6-3.el7.x86_64                                                                           309/670 
  Verifying  : pulseaudio-module-bluetooth-10.0-6.el7_9.x86_64                                                  310/670 
  Verifying  : taglib-1.8-8.20130218git.el7.x86_64                                                              311/670 
  Verifying  : pygtk2-libglade-2.24.0-9.el7.x86_64                                                              312/670 
  Verifying  : flatpak-libs-1.0.9-12.el7_9.x86_64                                                               313/670 
  Verifying  : icedax-1.1.11-25.el7.x86_64                                                                      314/670 
  Verifying  : google-noto-emoji-color-fonts-20180508-4.el7.noarch                                              315/670 
  Verifying  : 40:libcacard-2.7.0-1.el7.x86_64                                                                  316/670 
  Verifying  : libcgroup-0.41-21.el7.x86_64                                                                     317/670 
  Verifying  : setroubleshoot-server-3.2.30-8.el7.x86_64                                                        318/670 
  Verifying  : frei0r-plugins-1.3-13.el7.x86_64                                                                 319/670 
  Verifying  : libxkbcommon-0.7.1-3.el7.x86_64                                                                  320/670 
  Verifying  : libwayland-server-1.15.0-1.el7.x86_64                                                            321/670 
  Verifying  : libudisks2-2.8.4-1.el7.x86_64                                                                    322/670 
  Verifying  : gnome-calculator-3.28.2-1.el7.x86_64                                                             323/670 
  Verifying  : bluez-5.44-7.el7.x86_64                                                                          324/670 
  Verifying  : rdma-core-22.4-6.el7_9.x86_64                                                                    325/670 
  Verifying  : cairomm-1.12.0-1.el7.x86_64                                                                      326/670 
  Verifying  : telepathy-logger-0.8.0-5.el7.x86_64                                                              327/670 
  Verifying  : ibus-setup-1.5.17-12.el7_9.noarch                                                                328/670 
  Verifying  : mtdev-1.1.5-5.el7.x86_64                                                                         329/670 
  Verifying  : libvirt-daemon-kvm-4.5.0-36.el7_9.5.x86_64                                                       330/670 
  Verifying  : libproxy-mozjs-0.4.11-11.el7.x86_64                                                              331/670 
  Verifying  : libburn-1.2.8-4.el7.x86_64                                                                       332/670 
  Verifying  : telepathy-farstream-0.6.0-5.el7.x86_64                                                           333/670 
  Verifying  : gdb-7.6.1-120.el7.x86_64                                                                         334/670 
  Verifying  : libtool-ltdl-2.4.2-22.el7_3.x86_64                                                               335/670 
  Verifying  : gvfs-client-1.36.2-7.el7_9.x86_64                                                                336/670 
  Verifying  : libwacom-0.30-1.el7.x86_64                                                                       337/670 
  Verifying  : urw-base35-fonts-common-20170801-10.el7.noarch                                                   338/670 
  Verifying  : systemd-python-219-78.el7_9.7.x86_64                                                             339/670 
  Verifying  : gupnp-dlna-0.10.5-1.el7.x86_64                                                                   340/670 
  Verifying  : abrt-retrace-client-2.1.11-60.el7.centos.x86_64                                                  341/670 
  Verifying  : ndctl-65-6.el7_9.x86_64                                                                          342/670 
  Verifying  : telepathy-haze-0.8.0-1.el7.x86_64                                                                343/670 
  Verifying  : python-backports-1.0-8.el7.x86_64                                                                344/670 
  Verifying  : 1:control-center-3.28.1-8.el7_9.1.x86_64                                                         345/670 
  Verifying  : cairo-gobject-1.15.12-4.el7.x86_64                                                               346/670 
  Verifying  : sos-3.9-5.el7.centos.11.noarch                                                                   347/670 
  Verifying  : yajl-2.0.4-4.el7.x86_64                                                                          348/670 
  Verifying  : libvirt-daemon-driver-storage-rbd-4.5.0-36.el7_9.5.x86_64                                        349/670 
  Verifying  : clutter-gst3-3.0.26-1.el7.x86_64                                                                 350/670 
  Verifying  : libgdither-0.6-8.el7.x86_64                                                                      351/670 
  Verifying  : gnome-packagekit-common-3.28.0-1.el7.x86_64                                                      352/670 
  Verifying  : gtk-update-icon-cache-3.22.30-8.el7_9.x86_64                                                     353/670 
  Verifying  : libvirt-gobject-1.0.0-1.el7.x86_64                                                               354/670 
  Verifying  : cdrdao-1.2.3-20.el7.x86_64                                                                       355/670 
  Verifying  : iso-codes-3.46-2.el7.noarch                                                                      356/670 
  Verifying  : libreport-anaconda-2.1.11-53.el7.centos.x86_64                                                   357/670 
  Verifying  : baobab-3.28.0-2.el7.x86_64                                                                       358/670 
  Verifying  : gnome-system-monitor-3.28.2-1.el7.x86_64                                                         359/670 
  Verifying  : libwayland-client-1.15.0-1.el7.x86_64                                                            360/670 
  Verifying  : libblockdev-swap-2.18-5.el7.x86_64                                                               361/670 
  Verifying  : gnome-shell-extension-user-theme-3.28.1-17.el7_9.noarch                                          362/670 
  Verifying  : gnome-desktop3-3.28.2-2.el7.x86_64                                                               363/670 
  Verifying  : gom-0.4-1.el7.x86_64                                                                             364/670 
  Verifying  : hunspell-en-US-0.20121024-6.el7.noarch                                                           365/670 
  Verifying  : libvirt-daemon-driver-storage-iscsi-4.5.0-36.el7_9.5.x86_64                                      366/670 
  Verifying  : libmusicbrainz5-5.0.1-9.el7.x86_64                                                               367/670 
  Verifying  : python-setuptools-0.9.8-7.el7.noarch                                                             368/670 
  Verifying  : libinput-1.10.7-2.el7.x86_64                                                                     369/670 
  Verifying  : glusterfs-client-xlators-6.0-61.el7.x86_64                                                       370/670 
  Verifying  : tracker-1.10.5-8.el7.x86_64                                                                      371/670 
  Verifying  : xcb-util-keysyms-0.4.0-1.el7.x86_64                                                              372/670 
  Verifying  : adwaita-cursor-theme-3.28.0-1.el7.noarch                                                         373/670 
  Verifying  : gupnp-av-0.12.10-1.el7.x86_64                                                                    374/670 
  Verifying  : python-IPy-0.75-6.el7.noarch                                                                     375/670 
  Verifying  : libreport-plugin-mantisbt-2.1.11-53.el7.centos.x86_64                                            376/670 
  Verifying  : libvirt-gconfig-1.0.0-1.el7.x86_64                                                               377/670 
  Verifying  : libicu-50.2-4.el7_7.x86_64                                                                       378/670 
  Verifying  : orca-3.6.3-4.el7.x86_64                                                                          379/670 
  Verifying  : abrt-addon-vmcore-2.1.11-60.el7.centos.x86_64                                                    380/670 
  Verifying  : python2-pyatspi-2.26.0-3.el7.noarch                                                              381/670 
  Verifying  : gnome-disk-utility-3.28.3-1.el7.x86_64                                                           382/670 
  Verifying  : fwupdate-efi-12-6.el7.centos.x86_64                                                              383/670 
  Verifying  : seabios-bin-1.11.0-2.el7.noarch                                                                  384/670 
  Verifying  : samba-common-libs-4.10.16-24.el7_9.x86_64                                                        385/670 
  Verifying  : libgweather-3.28.2-4.el7_9.x86_64                                                                386/670 
  Verifying  : bridge-utils-1.5-9.el7.x86_64                                                                    387/670 
  Verifying  : libosinfo-1.1.0-5.el7.x86_64                                                                     388/670 
  Verifying  : 2:cheese-libs-3.28.0-1.el7.x86_64                                                                389/670 
  Verifying  : yelp-xsl-3.28.0-1.el7.noarch                                                                     390/670 
  Verifying  : mousetweaks-3.12.0-1.el7.x86_64                                                                  391/670 
  Verifying  : libreport-2.1.11-53.el7.centos.x86_64                                                            392/670 
  Verifying  : libvirt-daemon-4.5.0-36.el7_9.5.x86_64                                                           393/670 
  Verifying  : libwinpr-2.1.1-5.el7_9.x86_64                                                                    394/670 
  Verifying  : daxctl-libs-65-6.el7_9.x86_64                                                                    395/670 
  Verifying  : evolution-data-server-langpacks-3.28.5-5.el7_9.1.noarch                                          396/670 
  Verifying  : libnma-1.8.6-2.el7.x86_64                                                                        397/670 
  Verifying  : PackageKit-1.1.10-2.el7.centos.x86_64                                                            398/670 
  Verifying  : libgxps-0.3.0-4.el7.x86_64                                                                       399/670 
  Verifying  : dnsmasq-2.76-17.el7_9.3.x86_64                                                                   400/670 
  Verifying  : libvirt-daemon-driver-interface-4.5.0-36.el7_9.5.x86_64                                          401/670 
  Verifying  : osinfo-db-20200529-1.el7.noarch                                                                  402/670 
  Verifying  : libgudev1-219-78.el7_9.7.x86_64                                                                  403/670 
  Verifying  : libbluray-0.2.3-6.el7.x86_64                                                                     404/670 
  Verifying  : qt5-qtbase-5.9.7-5.el7_9.x86_64                                                                  405/670 
  Verifying  : spice-glib-0.35-5.el7_9.1.x86_64                                                                 406/670 
  Verifying  : libvirt-libs-4.5.0-36.el7_9.5.x86_64                                                             407/670 
  Verifying  : gjs-1.52.5-1.el7_6.x86_64                                                                        408/670 
  Verifying  : vino-3.22.0-7.el7.x86_64                                                                         409/670 
  Verifying  : gtkmm30-3.22.2-1.el7.x86_64                                                                      410/670 
  Verifying  : pulseaudio-libs-10.0-6.el7_9.x86_64                                                              411/670 
  Verifying  : urw-base35-nimbus-sans-fonts-20170801-10.el7.noarch                                              412/670 
  Verifying  : libbytesize-1.2-1.el7.x86_64                                                                     413/670 
  Verifying  : color-filesystem-1-13.el7.noarch                                                                 414/670 
  Verifying  : libpeas-gtk-1.22.0-1.el7.x86_64                                                                  415/670 
  Verifying  : fontpackages-filesystem-1.44-8.el7.noarch                                                        416/670 
  Verifying  : libical-3.0.3-2.el7.x86_64                                                                       417/670 
  Verifying  : iscsi-initiator-utils-iscsiuio-6.2.0.874-22.el7_9.x86_64                                         418/670 
  Verifying  : dmraid-events-1.0.0.rc16-28.el7.x86_64                                                           419/670 
  Verifying  : sane-backends-drivers-scanners-1.0.24-12.el7.x86_64                                              420/670 
  Verifying  : gstreamer-plugins-good-0.10.31-13.el7.x86_64                                                     421/670 
  Verifying  : appstream-data-7-20180614.el7.noarch                                                             422/670 
  Verifying  : libblockdev-loop-2.18-5.el7.x86_64                                                               423/670 
  Verifying  : python2-subprocess32-3.2.6-14.el7.x86_64                                                         424/670 
  Verifying  : fribidi-1.0.2-1.el7_7.1.x86_64                                                                   425/670 
  Verifying  : espeak-1.47.11-4.el7.x86_64                                                                      426/670 
  Verifying  : 10:qemu-kvm-common-1.5.3-175.el7_9.6.x86_64                                                      427/670 
  Verifying  : lockdev-1.0.4-0.13.20111007git.el7.x86_64                                                        428/670 
  Verifying  : NetworkManager-libreswan-1.2.4-2.el7.x86_64                                                      429/670 
  Verifying  : 1:gdm-3.28.2-26.el7.x86_64                                                                       430/670 
  Verifying  : cogl-1.22.2-2.el7.x86_64                                                                         431/670 
  Verifying  : 1:NetworkManager-wifi-1.18.8-2.el7_9.x86_64                                                      432/670 
  Verifying  : libsemanage-python-2.5-14.el7.x86_64                                                             433/670 
  Verifying  : nautilus-3.26.3.1-7.el7.x86_64                                                                   434/670 
  Verifying  : libsndfile-1.0.25-12.el7_9.1.x86_64                                                              435/670 
  Verifying  : python-gobject-3.22.0-1.el7_4.1.x86_64                                                           436/670 
  Verifying  : libwebp-0.3.0-11.el7.x86_64                                                                      437/670 
  Verifying  : pycairo-1.8.10-8.el7.x86_64                                                                      438/670 
  Verifying  : 14:libpcap-1.5.3-13.el7_9.x86_64                                                                 439/670 
  Verifying  : gnome-shell-extension-apps-menu-3.28.1-17.el7_9.noarch                                           440/670 
  Verifying  : gtk3-3.22.30-8.el7_9.x86_64                                                                      441/670 
  Verifying  : mesa-libgbm-18.3.4-12.el7_9.x86_64                                                               442/670 
  Verifying  : 1:control-center-filesystem-3.28.1-8.el7_9.1.x86_64                                              443/670 
  Verifying  : meanwhile-1.1.0-12.el7.x86_64                                                                    444/670 
  Verifying  : gsound-1.0.2-2.el7.x86_64                                                                        445/670 
  Verifying  : celt051-0.5.1.3-8.el7.x86_64                                                                     446/670 
  Verifying  : xcb-util-0.4.0-2.el7.x86_64                                                                      447/670 
  Verifying  : adwaita-qt5-1.0-1.el7.x86_64                                                                     448/670 
  Verifying  : pakchois-0.4-10.el7.x86_64                                                                       449/670 
  Verifying  : genisoimage-1.1.11-25.el7.x86_64                                                                 450/670 
  Verifying  : 1:telepathy-mission-control-5.16.3-3.el7.x86_64                                                  451/670 
  Verifying  : libgee-0.20.1-1.el7.x86_64                                                                       452/670 
  Verifying  : libdvdread-5.0.3-3.el7.x86_64                                                                    453/670 
  Verifying  : avahi-glib-0.6.31-20.el7.x86_64                                                                  454/670 
  Verifying  : jasper-libs-1.900.1-33.el7.x86_64                                                                455/670 
  Verifying  : libatasmart-0.19-6.el7.x86_64                                                                    456/670 
  Verifying  : rtkit-0.11-10.el7.x86_64                                                                         457/670 
  Verifying  : libgovirt-0.3.4-5.el7.x86_64                                                                     458/670 
  Verifying  : bolt-0.7-1.el7.x86_64                                                                            459/670 
  Verifying  : python2-futures-3.1.1-5.el7.noarch                                                               460/670 
  Verifying  : python-meh-gui-0.25.3-1.el7.noarch                                                               461/670 
  Verifying  : libimobiledevice-1.2.0-1.el7.x86_64                                                              462/670 
  Verifying  : gnome-shell-extension-places-menu-3.28.1-17.el7_9.noarch                                         463/670 
  Verifying  : libreport-plugin-bugzilla-2.1.11-53.el7.centos.x86_64                                            464/670 
  Verifying  : libwbclient-4.10.16-24.el7_9.x86_64                                                              465/670 
  Verifying  : libusbmuxd-1.0.10-5.el7.x86_64                                                                   466/670 
  Verifying  : libchamplain-0.12.16-2.el7.x86_64                                                                467/670 
  Verifying  : gnome-terminal-3.28.2-3.el7.x86_64                                                               468/670 
  Verifying  : evince-libs-3.28.2-10.el7.x86_64                                                                 469/670 
  Verifying  : netcf-libs-0.2.8-4.el7.x86_64                                                                    470/670 
  Verifying  : highcontrast-qt5-0.1-2.el7.x86_64                                                                471/670 
  Verifying  : 2:yelp-libs-3.28.1-1.el7.x86_64                                                                  472/670 
  Verifying  : libxkbcommon-x11-0.7.1-3.el7.x86_64                                                              473/670 
  Verifying  : freerdp-libs-2.1.1-5.el7_9.x86_64                                                                474/670 
  Verifying  : xdg-user-dirs-0.15-5.el7.x86_64                                                                  475/670 
  Verifying  : libv4l-0.9.5-4.el7.x86_64                                                                        476/670 
  Verifying  : grilo-plugins-0.3.7-1.el7.x86_64                                                                 477/670 
  Verifying  : gnome-abrt-0.3.4-9.el7.x86_64                                                                    478/670 
  Verifying  : abrt-addon-xorg-2.1.11-60.el7.centos.x86_64                                                      479/670 
  Verifying  : usbmuxd-1.1.0-1.el7.x86_64                                                                       480/670 
  Verifying  : gnome-shell-extension-horizontal-workspaces-3.28.1-17.el7_9.noarch                               481/670 
  Verifying  : libofa-0.9.3-24.el7.x86_64                                                                       482/670 
  Verifying  : libsmbios-2.3.3-8.el7.x86_64                                                                     483/670 
  Verifying  : libraw1394-2.1.0-2.el7.x86_64                                                                    484/670 
  Verifying  : libxslt-1.1.28-6.el7.x86_64                                                                      485/670 
  Verifying  : pulseaudio-gdm-hooks-10.0-6.el7_9.x86_64                                                         486/670 
  Verifying  : dleyna-core-0.5.0-1.el7.x86_64                                                                   487/670 
  Verifying  : sox-14.4.1-7.el7.x86_64                                                                          488/670 
  Verifying  : libblockdev-fs-2.18-5.el7.x86_64                                                                 489/670 
  Verifying  : urw-base35-fonts-20170801-10.el7.noarch                                                          490/670 
  Verifying  : wavpack-4.60.1-9.el7.x86_64                                                                      491/670 
  Verifying  : clutter-gst2-2.0.18-1.el7.x86_64                                                                 492/670 
  Verifying  : dmraid-1.0.0.rc16-28.el7.x86_64                                                                  493/670 
  Verifying  : xmlrpc-c-client-1.32.5-1905.svn2451.el7.x86_64                                                   494/670 
  Verifying  : avahi-libs-0.6.31-20.el7.x86_64                                                                  495/670 
  Verifying  : 1:librbd1-10.2.5-4.el7.x86_64                                                                    496/670 
  Verifying  : mutter-3.28.3-32.el7_9.x86_64                                                                    497/670 
  Verifying  : gnome-screenshot-3.26.0-1.el7.x86_64                                                             498/670 
  Verifying  : gnome-terminal-nautilus-3.28.2-3.el7.x86_64                                                      499/670 
  Verifying  : gnome-icon-theme-3.12.0-1.el7.noarch                                                             500/670 
  Verifying  : gnome-shell-3.28.3-34.el7_9.x86_64                                                               501/670 
  Verifying  : libnotify-0.7.7-1.el7.x86_64                                                                     502/670 
  Verifying  : libwnck3-3.24.1-2.el7.x86_64                                                                     503/670 
  Verifying  : zenity-3.28.1-2.el7_9.x86_64                                                                     504/670 
  Verifying  : desktop-file-utils-0.23-2.el7.x86_64                                                             505/670 
  Verifying  : xcb-util-wm-0.4.1-5.el7.x86_64                                                                   506/670 
  Verifying  : python-backports-ssl_match_hostname-3.5.0.1-1.el7.noarch                                         507/670 
  Verifying  : fftw-libs-double-3.3.3-8.el7.x86_64                                                              508/670 
  Verifying  : rsync-3.1.2-12.el7_9.x86_64                                                                      509/670 
  Verifying  : satyr-0.13-15.el7.x86_64                                                                         510/670 
  Verifying  : iscsi-initiator-utils-6.2.0.874-22.el7_9.x86_64                                                  511/670 
  Verifying  : sound-theme-freedesktop-0.8-3.el7.noarch                                                         512/670 
  Verifying  : dvd+rw-tools-7.1-15.el7.x86_64                                                                   513/670 
  Verifying  : libvirt-daemon-driver-nodedev-4.5.0-36.el7_9.5.x86_64                                            514/670 
  Verifying  : libdmapsharing-2.9.37-1.el7.x86_64                                                               515/670 
  Verifying  : libexif-0.6.22-2.el7_9.x86_64                                                                    516/670 
  Verifying  : json-glib-1.4.2-2.el7.x86_64                                                                     517/670 
  Verifying  : numad-0.5-18.20150602git.el7.x86_64                                                              518/670 
  Verifying  : libblockdev-utils-2.18-5.el7.x86_64                                                              519/670 
  Verifying  : empathy-3.12.13-1.el7.x86_64                                                                     520/670 
  Verifying  : abrt-2.1.11-60.el7.centos.x86_64                                                                 521/670 
  Verifying  : glusterfs-api-6.0-61.el7.x86_64                                                                  522/670 
  Verifying  : ipxe-roms-qemu-20180825-3.git133f4c.el7.noarch                                                   523/670 
  Verifying  : gnome-icon-theme-symbolic-3.12.0-2.el7.noarch                                                    524/670 
  Verifying  : geocode-glib-3.26.0-3.el7.x86_64                                                                 525/670 
  Verifying  : gvfs-afc-1.36.2-7.el7_9.x86_64                                                                   526/670 
  Verifying  : gstreamer-plugins-bad-free-0.10.23-23.el7.x86_64                                                 527/670 
  Verifying  : gnome-keyring-pam-3.28.2-1.el7.x86_64                                                            528/670 
  Verifying  : libvirt-daemon-driver-storage-4.5.0-36.el7_9.5.x86_64                                            529/670 
  Verifying  : python-six-1.9.0-2.el7.noarch                                                                    530/670 
  Verifying  : dleyna-server-0.5.0-3.el7.x86_64                                                                 531/670 
  Verifying  : file-roller-nautilus-3.28.1-2.el7.x86_64                                                         532/670 
  Verifying  : libdvdnav-5.0.3-1.el7.x86_64                                                                     533/670 
  Verifying  : sbc-1.0-5.el7.x86_64                                                                             534/670 
  Verifying  : cyrus-sasl-md5-2.1.26-24.el7_9.x86_64                                                            535/670 
  Verifying  : webkitgtk4-jsc-2.28.2-3.el7.x86_64                                                               536/670 
  Verifying  : compat-exiv2-026-0.26-2.el7.x86_64                                                               537/670 
  Verifying  : libmpcdec-1.2.6-12.el7.x86_64                                                                    538/670 
  Verifying  : python-meh-0.25.3-1.el7.noarch                                                                   539/670 
  Verifying  : libvirt-daemon-config-network-4.5.0-36.el7_9.5.x86_64                                            540/670 
  Verifying  : pykickstart-1.99.66.22-1.el7.noarch                                                              541/670 
  Verifying  : brltty-4.5-16.el7.x86_64                                                                         542/670 
  Verifying  : libgphoto2-2.5.15-3.el7.x86_64                                                                   543/670 
  Verifying  : gstreamer-tools-0.10.36-7.el7.x86_64                                                             544/670 
  Verifying  : boost-iostreams-1.53.0-28.el7.x86_64                                                             545/670 
  Verifying  : clutter-1.26.2-2.el7.x86_64                                                                      546/670 
  Verifying  : mobile-broadband-provider-info-1.20170310-1.el7.noarch                                           547/670 
  Verifying  : cryptsetup-python-2.0.3-6.el7.x86_64                                                             548/670 
  Verifying  : xdg-utils-1.1.0-0.17.20120809git.el7.noarch                                                      549/670 
  Verifying  : PackageKit-command-not-found-1.1.10-2.el7.centos.x86_64                                          550/670 
  Verifying  : anaconda-widgets-21.48.22.159-1.el7.centos.x86_64                                                551/670 
  Verifying  : fros-1.0-5.el7.noarch                                                                            552/670 
  Verifying  : speex-1.2-0.19.rc1.el7.x86_64                                                                    553/670 
  Verifying  : libvirt-glib-1.0.0-1.el7.x86_64                                                                  554/670 
  Verifying  : gnome-packagekit-3.28.0-1.el7.x86_64                                                             555/670 
  Verifying  : webkitgtk3-2.4.11-2.el7.x86_64                                                                   556/670 
  Verifying  : qgnomeplatform-0.3-5.el7.x86_64                                                                  557/670 
  Verifying  : pygtk2-2.24.0-9.el7.x86_64                                                                       558/670 
  Verifying  : python-nss-0.16.0-3.el7.x86_64                                                                   559/670 
  Verifying  : libvirt-daemon-driver-storage-logical-4.5.0-36.el7_9.5.x86_64                                    560/670 
  Verifying  : gnome-dictionary-3.26.1-2.el7.x86_64                                                             561/670 
  Verifying  : python-brlapi-0.6.0-16.el7.x86_64                                                                562/670 
  Verifying  : boost-system-1.53.0-28.el7.x86_64                                                                563/670 
  Verifying  : samba-client-libs-4.10.16-24.el7_9.x86_64                                                        564/670 
  Verifying  : xcb-util-image-0.4.0-2.el7.x86_64                                                                565/670 
  Verifying  : gnome-contacts-3.28.2-1.el7.x86_64                                                               566/670 
  Verifying  : libvirt-daemon-driver-storage-mpath-4.5.0-36.el7_9.5.x86_64                                      567/670 
  Verifying  : osinfo-db-tools-1.1.0-1.el7.x86_64                                                               568/670 
  Verifying  : gnome-online-accounts-3.28.2-1.el7.x86_64                                                        569/670 
  Verifying  : glibmm24-2.56.0-1.el7.x86_64                                                                     570/670 
  Verifying  : libsigc++20-2.10.0-1.el7.x86_64                                                                  571/670 
  Verifying  : libvirt-daemon-driver-network-4.5.0-36.el7_9.5.x86_64                                            572/670 
  Verifying  : cyrus-sasl-plain-2.1.26-24.el7_9.x86_64                                                          573/670 
  Verifying  : audit-libs-python-2.8.5-4.el7.x86_64                                                             574/670 
  Verifying  : dotconf-1.3-8.el7.x86_64                                                                         575/670 
  Verifying  : sgpio-1.2.0.10-13.el7.x86_64                                                                     576/670 
  Verifying  : libsoup-2.62.2-2.el7.x86_64                                                                      577/670 
  Verifying  : graphite2-1.3.10-1.el7_3.x86_64                                                                  578/670 
  Verifying  : volume_key-libs-0.3.9-9.el7.x86_64                                                               579/670 
  Verifying  : spice-server-0.14.0-9.el7_9.1.x86_64                                                             580/670 
  Verifying  : gcr-3.28.0-1.el7.x86_64                                                                          581/670 
  Verifying  : libpaper-1.1.24-9.el7.x86_64                                                                     582/670 
  Verifying  : qt5-qtbase-gui-5.9.7-5.el7_9.x86_64                                                              583/670 
  Verifying  : fwupd-1.0.8-5.el7.x86_64                                                                         584/670 
  Verifying  : urw-base35-z003-fonts-20170801-10.el7.noarch                                                     585/670 
  Verifying  : libXv-1.0.11-1.el7.x86_64                                                                        586/670 
  Verifying  : hyphen-2.8.6-5.el7.x86_64                                                                        587/670 
  Verifying  : webrtc-audio-processing-0.3-1.el7.x86_64                                                         588/670 
  Verifying  : fcoe-utils-1.0.32-2.el7_6.x86_64                                                                 589/670 
  Verifying  : lldpad-1.0.1-7.git036e314.el7_9.x86_64                                                           590/670 
  Verifying  : abrt-addon-python-2.1.11-60.el7.centos.x86_64                                                    591/670 
  Verifying  : libreswan-3.25-9.1.el7_8.x86_64                                                                  592/670 
  Verifying  : gnome-font-viewer-3.28.0-1.el7.x86_64                                                            593/670 
  Verifying  : cdparanoia-10.2-17.el7.x86_64                                                                    594/670 
  Verifying  : libvirt-daemon-driver-secret-4.5.0-36.el7_9.5.x86_64                                             595/670 
  Verifying  : firewall-config-0.6.3-13.el7_9.noarch                                                            596/670 
  Verifying  : hicolor-icon-theme-0.12-7.el7.noarch                                                             597/670 
  Verifying  : usbredir-0.7.1-3.el7.x86_64                                                                      598/670 
  Verifying  : liblouis-2.5.2-12.el7_4.x86_64                                                                   599/670 
  Verifying  : libvirt-daemon-driver-storage-scsi-4.5.0-36.el7_9.5.x86_64                                       600/670 
  Verifying  : libreport-plugin-ureport-2.1.11-53.el7.centos.x86_64                                             601/670 
  Verifying  : pango-1.42.4-4.el7_7.x86_64                                                                      602/670 
  Verifying  : cdparanoia-libs-10.2-17.el7.x86_64                                                               603/670 
  Verifying  : gnome-menus-3.13.3-3.el7.x86_64                                                                  604/670 
  Verifying  : libsane-hpaio-3.15.9-5.el7.x86_64                                                                605/670 
  Verifying  : telepathy-gabble-0.18.1-4.el7.x86_64                                                             606/670 
  Verifying  : udisks2-2.8.4-1.el7.x86_64                                                                       607/670 
  Verifying  : 1:isomd5sum-1.0.10-5.el7.x86_64                                                                  608/670 
  Verifying  : python-pyblock-0.53-6.el7.x86_64                                                                 609/670 
  Verifying  : gnome-icon-theme-extras-3.12.0-1.el7.noarch                                                      610/670 
  Verifying  : libvisual-0.4.0-16.el7.x86_64                                                                    611/670 
  Verifying  : liboauth-0.9.7-4.el7.x86_64                                                                      612/670 
  Verifying  : poppler-data-0.4.6-3.el7.noarch                                                                  613/670 
  Verifying  : libblockdev-2.18-5.el7.x86_64                                                                    614/670 
  Verifying  : device-mapper-multipath-libs-0.4.9-136.el7_9.x86_64                                              615/670 
  Verifying  : 1:libtheora-1.1.1-8.el7.x86_64                                                                   616/670 
  Verifying  : poppler-0.26.5-43.el7.1.x86_64                                                                   617/670 
  Verifying  : telepathy-filesystem-0.0.2-6.el7.noarch                                                          618/670 
  Verifying  : soundtouch-1.4.0-9.el7.x86_64                                                                    619/670 
  Verifying  : libmediaart-1.9.4-1.el7.x86_64                                                                   620/670 
  Verifying  : firstboot-19.12-1.el7.x86_64                                                                     621/670 
  Verifying  : libtimezonemap-0.4.4-2.el7_9.x86_64                                                              622/670 
  Verifying  : xmlrpc-c-1.32.5-1905.svn2451.el7.x86_64                                                          623/670 
  Verifying  : glusterfs-cli-6.0-61.el7.x86_64                                                                  624/670 
  Verifying  : libsrtp-1.4.4-11.20101004cvs.el7.x86_64                                                          625/670 
  Verifying  : augeas-libs-1.4.0-10.el7.x86_64                                                                  626/670 
  Verifying  : ibus-libs-1.5.17-12.el7_9.x86_64                                                                 627/670 
  Verifying  : gnome-themes-standard-3.28-2.el7.x86_64                                                          628/670 
  Verifying  : clutter-gtk-1.8.4-1.el7.x86_64                                                                   629/670 
  Verifying  : glx-utils-8.3.0-10.el7.x86_64                                                                    630/670 
  Verifying  : sushi-3.28.3-1.el7.x86_64                                                                        631/670 
  Verifying  : urw-base35-p052-fonts-20170801-10.el7.noarch                                                     632/670 
  Verifying  : neon-0.30.0-4.el7.x86_64                                                                         633/670 
  Verifying  : vte291-0.52.4-1.el7.x86_64                                                                       634/670 
  Verifying  : python-pwquality-1.2.3-5.el7.x86_64                                                              635/670 
  Verifying  : 1:python-blivet-0.61.15.76-1.el7_9.noarch                                                        636/670 
  Verifying  : opus-1.0.2-6.el7.x86_64                                                                          637/670 
  Verifying  : libasyncns-0.8-7.el7.x86_64                                                                      638/670 
  Verifying  : oddjob-0.31.5-4.el7.x86_64                                                                       639/670 
  Verifying  : cups-pk-helper-0.2.6-2.el7.x86_64                                                                640/670 
  Verifying  : 2:yelp-3.28.1-1.el7.x86_64                                                                       641/670 
  Verifying  : libsecret-0.18.6-1.el7.x86_64                                                                    642/670 
  Verifying  : libthai-0.1.14-9.el7.x86_64                                                                      643/670 
  Verifying  : initial-setup-0.3.9.45-1.el7.centos.x86_64                                                       644/670 
  Verifying  : libXft-2.3.2-2.el7.x86_64                                                                        645/670 
  Verifying  : libevdev-1.5.6-1.el7.x86_64                                                                      646/670 
  Verifying  : 1:libglvnd-gles-1.0.1-0.8.git5baa1e5.el7.x86_64                                                  647/670 
  Verifying  : libepoxy-1.5.2-1.el7.x86_64                                                                      648/670 
  Verifying  : libglade2-2.6.4-11.el7.x86_64                                                                    649/670 
  Verifying  : abrt-python-2.1.11-60.el7.centos.x86_64                                                          650/670 
  Verifying  : gnome-settings-daemon-3.28.1-11.el7_9.x86_64                                                     651/670 
  Verifying  : 10:qemu-kvm-1.5.3-175.el7_9.6.x86_64                                                             652/670 
  Verifying  : pinentry-gtk-0.8.1-17.el7.x86_64                                                                 653/670 
  Verifying  : dconf-0.28.0-4.el7.x86_64                                                                        654/670 
  Verifying  : 1:enchant-1.6.0-8.el7.x86_64                                                                     655/670 
  Verifying  : brasero-3.12.2-5.el7_9.1.x86_64                                                                  656/670 
  Verifying  : abrt-dbus-2.1.11-60.el7.centos.x86_64                                                            657/670 
  Verifying  : checkpolicy-2.5-8.el7.x86_64                                                                     658/670 
  Verifying  : langtable-0.0.31-4.el7.noarch                                                                    659/670 
  Verifying  : librdmacm-22.4-6.el7_9.x86_64                                                                    660/670 
  Verifying  : cairo-1.15.12-4.el7.x86_64                                                                       661/670 
  Verifying  : libproxy-0.4.11-11.el7.x86_64                                                                    662/670 
  Verifying  : libisofs-1.2.8-4.el7.x86_64                                                                      663/670 
  Verifying  : device-mapper-multipath-0.4.9-136.el7_9.x86_64                                                   664/670 
  Verifying  : xdg-desktop-portal-1.0.2-1.el7.x86_64                                                            665/670 
  Verifying  : urw-base35-c059-fonts-20170801-10.el7.noarch                                                     666/670 
  Verifying  : urw-base35-bookman-fonts-20170801-10.el7.noarch                                                  667/670 
  Verifying  : gvfs-1.36.2-7.el7_9.x86_64                                                                       668/670 
  Verifying  : libblockdev-crypto-2.18-5.el7.x86_64                                                             669/670 
  Verifying  : libnice-0.1.3-4.el7.x86_64                                                                       670/670 

Installed:
  NetworkManager-libreswan-gnome.x86_64 0:1.2.4-2.el7     PackageKit-command-not-found.x86_64 0:1.1.10-2.el7.centos    
  PackageKit-gtk3-module.x86_64 0:1.1.10-2.el7.centos     abrt-desktop.x86_64 0:2.1.11-60.el7.centos                   
  at-spi2-atk.x86_64 0:2.26.2-1.el7                       at-spi2-core.x86_64 0:2.28.0-1.el7                           
  avahi.x86_64 0:0.6.31-20.el7                            baobab.x86_64 0:3.28.0-2.el7                                 
  cheese.x86_64 2:3.28.0-1.el7                            compat-cheese314.x86_64 0:3.14.2-1.el7                       
  control-center.x86_64 1:3.28.1-8.el7_9.1                dconf.x86_64 0:0.28.0-4.el7                                  
  empathy.x86_64 0:3.12.13-1.el7                          eog.x86_64 0:3.28.3-1.el7                                    
  evince.x86_64 0:3.28.2-10.el7                           evince-nautilus.x86_64 0:3.28.2-10.el7                       
  file-roller.x86_64 0:3.28.1-2.el7                       file-roller-nautilus.x86_64 0:3.28.1-2.el7                   
  firewall-config.noarch 0:0.6.3-13.el7_9                 firstboot.x86_64 0:19.12-1.el7                               
  fprintd-pam.x86_64 0:0.8.1-2.el7                        gdm.x86_64 1:3.28.2-26.el7                                   
  gedit.x86_64 2:3.28.1-3.el7                             glib-networking.x86_64 0:2.56.1-1.el7                        
  gnome-bluetooth.x86_64 1:3.28.2-1.el7                   gnome-boxes.x86_64 0:3.28.5-4.el7                            
  gnome-calculator.x86_64 0:3.28.2-1.el7                  gnome-classic-session.noarch 0:3.28.1-17.el7_9               
  gnome-clocks.x86_64 0:3.28.0-1.el7                      gnome-color-manager.x86_64 0:3.28.0-1.el7                    
  gnome-contacts.x86_64 0:3.28.2-1.el7                    gnome-dictionary.x86_64 0:3.26.1-2.el7                       
  gnome-disk-utility.x86_64 0:3.28.3-1.el7                gnome-font-viewer.x86_64 0:3.28.0-1.el7                      
  gnome-getting-started-docs.noarch 0:3.28.2-1.el7        gnome-icon-theme.noarch 0:3.12.0-1.el7                       
  gnome-icon-theme-extras.noarch 0:3.12.0-1.el7           gnome-icon-theme-symbolic.noarch 0:3.12.0-2.el7              
  gnome-initial-setup.x86_64 0:3.28.0-2.el7_9.1           gnome-packagekit.x86_64 0:3.28.0-1.el7                       
  gnome-packagekit-updater.x86_64 0:3.28.0-1.el7          gnome-screenshot.x86_64 0:3.26.0-1.el7                       
  gnome-session.x86_64 0:3.28.1-8.el7                     gnome-session-xsession.x86_64 0:3.28.1-8.el7                 
  gnome-settings-daemon.x86_64 0:3.28.1-11.el7_9          gnome-shell.x86_64 0:3.28.3-34.el7_9                         
  gnome-software.x86_64 0:3.28.2-3.el7                    gnome-system-log.x86_64 1:3.9.90-3.el7                       
  gnome-system-monitor.x86_64 0:3.28.2-1.el7              gnome-terminal.x86_64 0:3.28.2-3.el7                         
  gnome-terminal-nautilus.x86_64 0:3.28.2-3.el7           gnome-themes-standard.x86_64 0:3.28-2.el7                    
  gnome-tweak-tool.noarch 0:3.28.1-7.el7                  gnome-user-docs.noarch 0:3.28.2-1.el7                        
  gnome-weather.noarch 0:3.26.0-1.el7                     gucharmap.x86_64 0:10.0.4-1.el7                              
  gvfs-afc.x86_64 0:1.36.2-7.el7_9                        gvfs-afp.x86_64 0:1.36.2-7.el7_9                             
  gvfs-archive.x86_64 0:1.36.2-7.el7_9                    gvfs-fuse.x86_64 0:1.36.2-7.el7_9                            
  gvfs-goa.x86_64 0:1.36.2-7.el7_9                        gvfs-gphoto2.x86_64 0:1.36.2-7.el7_9                         
  gvfs-mtp.x86_64 0:1.36.2-7.el7_9                        gvfs-smb.x86_64 0:1.36.2-7.el7_9                             
  initial-setup-gui.x86_64 0:0.3.9.45-1.el7.centos        libcanberra-gtk2.x86_64 0:0.30-9.el7                         
  libcanberra-gtk3.x86_64 0:0.30-9.el7                    libproxy-mozjs.x86_64 0:0.4.11-11.el7                        
  librsvg2.x86_64 0:2.40.20-1.el7                         libsane-hpaio.x86_64 0:3.15.9-5.el7                          
  metacity.x86_64 0:2.34.13-7.el7                         mousetweaks.x86_64 0:3.12.0-1.el7                            
  nautilus.x86_64 0:3.26.3.1-7.el7                        nautilus-sendto.x86_64 1:3.8.6-1.el7                         
  nm-connection-editor.x86_64 0:1.8.6-2.el7               orca.x86_64 0:3.6.3-4.el7                                    
  qgnomeplatform.x86_64 0:0.3-5.el7                       sane-backends-drivers-scanners.x86_64 0:1.0.24-12.el7        
  seahorse.x86_64 0:3.20.0-1.el7                          setroubleshoot.x86_64 0:3.2.30-8.el7                         
  sushi.x86_64 0:3.28.3-1.el7                             totem.x86_64 1:3.26.2-1.el7                                  
  totem-nautilus.x86_64 1:3.26.2-1.el7                    vinagre.x86_64 0:3.22.0-14.el7                               
  vino.x86_64 0:3.22.0-7.el7                              xdg-desktop-portal-gtk.x86_64 0:1.0.2-1.el7                  
  xdg-user-dirs-gtk.x86_64 0:0.10-4.el7                   yelp.x86_64 2:3.28.1-1.el7                                   

Dependency Installed:
  GConf2.x86_64 0:3.2.6-8.el7                                                                                           
  ModemManager-glib.x86_64 0:1.6.10-4.el7                                                                               
  NetworkManager-glib.x86_64 1:1.18.8-2.el7_9                                                                           
  NetworkManager-libreswan.x86_64 0:1.2.4-2.el7                                                                         
  NetworkManager-wifi.x86_64 1:1.18.8-2.el7_9                                                                           
  PackageKit.x86_64 0:1.1.10-2.el7.centos                                                                               
  PackageKit-glib.x86_64 0:1.1.10-2.el7.centos                                                                          
  PackageKit-yum.x86_64 0:1.1.10-2.el7.centos                                                                           
  abattis-cantarell-fonts.noarch 0:0.0.25-1.el7                                                                         
  abrt.x86_64 0:2.1.11-60.el7.centos                                                                                    
  abrt-addon-ccpp.x86_64 0:2.1.11-60.el7.centos                                                                         
  abrt-addon-kerneloops.x86_64 0:2.1.11-60.el7.centos                                                                   
  abrt-addon-pstoreoops.x86_64 0:2.1.11-60.el7.centos                                                                   
  abrt-addon-python.x86_64 0:2.1.11-60.el7.centos                                                                       
  abrt-addon-vmcore.x86_64 0:2.1.11-60.el7.centos                                                                       
  abrt-addon-xorg.x86_64 0:2.1.11-60.el7.centos                                                                         
  abrt-dbus.x86_64 0:2.1.11-60.el7.centos                                                                               
  abrt-gui.x86_64 0:2.1.11-60.el7.centos                                                                                
  abrt-gui-libs.x86_64 0:2.1.11-60.el7.centos                                                                           
  abrt-libs.x86_64 0:2.1.11-60.el7.centos                                                                               
  abrt-python.x86_64 0:2.1.11-60.el7.centos                                                                             
  abrt-retrace-client.x86_64 0:2.1.11-60.el7.centos                                                                     
  accountsservice.x86_64 0:0.6.50-7.el7                                                                                 
  accountsservice-libs.x86_64 0:0.6.50-7.el7                                                                            
  adobe-mappings-cmap.noarch 0:20171205-3.el7                                                                           
  adobe-mappings-cmap-deprecated.noarch 0:20171205-3.el7                                                                
  adobe-mappings-pdf.noarch 0:20180407-1.el7                                                                            
  adwaita-cursor-theme.noarch 0:3.28.0-1.el7                                                                            
  adwaita-gtk2-theme.x86_64 0:3.28-2.el7                                                                                
  adwaita-icon-theme.noarch 0:3.28.0-1.el7                                                                              
  adwaita-qt5.x86_64 0:1.0-1.el7                                                                                        
  anaconda-core.x86_64 0:21.48.22.159-1.el7.centos                                                                      
  anaconda-gui.x86_64 0:21.48.22.159-1.el7.centos                                                                       
  anaconda-tui.x86_64 0:21.48.22.159-1.el7.centos                                                                       
  anaconda-widgets.x86_64 0:21.48.22.159-1.el7.centos                                                                   
  appstream-data.noarch 0:7-20180614.el7                                                                                
  atk.x86_64 0:2.28.1-2.el7                                                                                             
  atkmm.x86_64 0:2.24.2-1.el7                                                                                           
  audit-libs-python.x86_64 0:2.8.5-4.el7                                                                                
  augeas-libs.x86_64 0:1.4.0-10.el7                                                                                     
  avahi-glib.x86_64 0:0.6.31-20.el7                                                                                     
  avahi-gobject.x86_64 0:0.6.31-20.el7                                                                                  
  avahi-libs.x86_64 0:0.6.31-20.el7                                                                                     
  avahi-ui-gtk3.x86_64 0:0.6.31-20.el7                                                                                  
  bluez.x86_64 0:5.44-7.el7                                                                                             
  bolt.x86_64 0:0.7-1.el7                                                                                               
  boost-iostreams.x86_64 0:1.53.0-28.el7                                                                                
  boost-random.x86_64 0:1.53.0-28.el7                                                                                   
  boost-system.x86_64 0:1.53.0-28.el7                                                                                   
  boost-thread.x86_64 0:1.53.0-28.el7                                                                                   
  brasero.x86_64 0:3.12.2-5.el7_9.1                                                                                     
  brasero-libs.x86_64 0:3.12.2-5.el7_9.1                                                                                
  brasero-nautilus.x86_64 0:3.12.2-5.el7_9.1                                                                            
  bridge-utils.x86_64 0:1.5-9.el7                                                                                       
  brlapi.x86_64 0:0.6.0-16.el7                                                                                          
  brltty.x86_64 0:4.5-16.el7                                                                                            
  cairo.x86_64 0:1.15.12-4.el7                                                                                          
  cairo-gobject.x86_64 0:1.15.12-4.el7                                                                                  
  cairomm.x86_64 0:1.12.0-1.el7                                                                                         
  cdparanoia.x86_64 0:10.2-17.el7                                                                                       
  cdparanoia-libs.x86_64 0:10.2-17.el7                                                                                  
  cdrdao.x86_64 0:1.2.3-20.el7                                                                                          
  celt051.x86_64 0:0.5.1.3-8.el7                                                                                        
  checkpolicy.x86_64 0:2.5-8.el7                                                                                        
  cheese-libs.x86_64 2:3.28.0-1.el7                                                                                     
  clutter.x86_64 0:1.26.2-2.el7                                                                                         
  clutter-gst2.x86_64 0:2.0.18-1.el7                                                                                    
  clutter-gst3.x86_64 0:3.0.26-1.el7                                                                                    
  clutter-gtk.x86_64 0:1.8.4-1.el7                                                                                      
  cogl.x86_64 0:1.22.2-2.el7                                                                                            
  color-filesystem.noarch 0:1-13.el7                                                                                    
  colord.x86_64 0:1.3.4-2.el7                                                                                           
  colord-gtk.x86_64 0:0.1.25-4.el7                                                                                      
  colord-libs.x86_64 0:1.3.4-2.el7                                                                                      
  compat-exiv2-026.x86_64 0:0.26-2.el7                                                                                  
  compat-gnome-desktop314.x86_64 0:3.14.2-1.el7                                                                         
  compat-libcolord1.x86_64 0:1.0.4-1.el7                                                                                
  control-center-filesystem.x86_64 1:3.28.1-8.el7_9.1                                                                   
  createrepo.noarch 0:0.9.9-28.el7                                                                                      
  cryptsetup.x86_64 0:2.0.3-6.el7                                                                                       
  cryptsetup-python.x86_64 0:2.0.3-6.el7                                                                                
  cups-libs.x86_64 1:1.6.3-51.el7                                                                                       
  cups-pk-helper.x86_64 0:0.2.6-2.el7                                                                                   
  cyrus-sasl.x86_64 0:2.1.26-24.el7_9                                                                                   
  cyrus-sasl-gssapi.x86_64 0:2.1.26-24.el7_9                                                                            
  cyrus-sasl-md5.x86_64 0:2.1.26-24.el7_9                                                                               
  cyrus-sasl-plain.x86_64 0:2.1.26-24.el7_9                                                                             
  cyrus-sasl-scram.x86_64 0:2.1.26-24.el7_9                                                                             
  daxctl-libs.x86_64 0:65-6.el7_9                                                                                       
  dbus-x11.x86_64 1:1.10.24-15.el7                                                                                      
  dejavu-fonts-common.noarch 0:2.33-6.el7                                                                               
  dejavu-sans-fonts.noarch 0:2.33-6.el7                                                                                 
  deltarpm.x86_64 0:3.6-3.el7                                                                                           
  desktop-file-utils.x86_64 0:0.23-2.el7                                                                                
  device-mapper-multipath.x86_64 0:0.4.9-136.el7_9                                                                      
  device-mapper-multipath-libs.x86_64 0:0.4.9-136.el7_9                                                                 
  dleyna-connector-dbus.x86_64 0:0.2.0-2.el7                                                                            
  dleyna-core.x86_64 0:0.5.0-1.el7                                                                                      
  dleyna-server.x86_64 0:0.5.0-3.el7                                                                                    
  dmraid.x86_64 0:1.0.0.rc16-28.el7                                                                                     
  dmraid-events.x86_64 0:1.0.0.rc16-28.el7                                                                              
  dnsmasq.x86_64 0:2.76-17.el7_9.3                                                                                      
  dotconf.x86_64 0:1.3-8.el7                                                                                            
  dvd+rw-tools.x86_64 0:7.1-15.el7                                                                                      
  elfutils.x86_64 0:0.176-5.el7                                                                                         
  emacs-filesystem.noarch 1:24.3-23.el7_9.1                                                                             
  enchant.x86_64 1:1.6.0-8.el7                                                                                          
  espeak.x86_64 0:1.47.11-4.el7                                                                                         
  evince-libs.x86_64 0:3.28.2-10.el7                                                                                    
  evolution-data-server.x86_64 0:3.28.5-5.el7_9.1                                                                       
  evolution-data-server-langpacks.noarch 0:3.28.5-5.el7_9.1                                                             
  exempi.x86_64 0:2.2.0-9.el7                                                                                           
  farstream.x86_64 0:0.1.2-8.el7                                                                                        
  farstream02.x86_64 0:0.2.3-3.el7                                                                                      
  fcoe-utils.x86_64 0:1.0.32-2.el7_6                                                                                    
  festival.x86_64 0:1.96-28.el7                                                                                         
  festival-freebsoft-utils.noarch 0:0.10-7.el7                                                                          
  festival-lib.x86_64 0:1.96-28.el7                                                                                     
  festival-speechtools-libs.x86_64 0:1.2.96-28.el7                                                                      
  festvox-slt-arctic-hts.noarch 0:0.20061229-28.el7                                                                     
  fftw-libs-double.x86_64 0:3.3.3-8.el7                                                                                 
  flac-libs.x86_64 0:1.3.0-5.el7_1                                                                                      
  flatpak.x86_64 0:1.0.9-12.el7_9                                                                                       
  flatpak-libs.x86_64 0:1.0.9-12.el7_9                                                                                  
  flite.x86_64 0:1.3-22.el7                                                                                             
  folks.x86_64 1:0.11.4-1.el7                                                                                           
  fontconfig.x86_64 0:2.13.0-4.3.el7                                                                                    
  fontpackages-filesystem.noarch 0:1.44-8.el7                                                                           
  fprintd.x86_64 0:0.8.1-2.el7                                                                                          
  freerdp-libs.x86_64 0:2.1.1-5.el7_9                                                                                   
  frei0r-plugins.x86_64 0:1.3-13.el7                                                                                    
  fribidi.x86_64 0:1.0.2-1.el7_7.1                                                                                      
  fros.noarch 0:1.0-5.el7                                                                                               
  fuse.x86_64 0:2.9.2-11.el7                                                                                            
  fwupd.x86_64 0:1.0.8-5.el7                                                                                            
  fwupdate-efi.x86_64 0:12-6.el7.centos                                                                                 
  fwupdate-libs.x86_64 0:12-6.el7.centos                                                                                
  gavl.x86_64 0:1.4.0-4.el7                                                                                             
  gcr.x86_64 0:3.28.0-1.el7                                                                                             
  gd.x86_64 0:2.0.35-27.el7_9                                                                                           
  gdb.x86_64 0:7.6.1-120.el7                                                                                            
  gdisk.x86_64 0:0.8.10-3.el7                                                                                           
  gdk-pixbuf2.x86_64 0:2.36.12-3.el7                                                                                    
  genisoimage.x86_64 0:1.1.11-25.el7                                                                                    
  geoclue2.x86_64 0:2.4.8-1.el7                                                                                         
  geoclue2-libs.x86_64 0:2.4.8-1.el7                                                                                    
  geocode-glib.x86_64 0:3.26.0-3.el7                                                                                    
  gjs.x86_64 0:1.52.5-1.el7_6                                                                                           
  glade-libs.x86_64 0:3.22.1-1.el7                                                                                      
  glibmm24.x86_64 0:2.56.0-1.el7                                                                                        
  glusterfs.x86_64 0:6.0-61.el7                                                                                         
  glusterfs-api.x86_64 0:6.0-61.el7                                                                                     
  glusterfs-cli.x86_64 0:6.0-61.el7                                                                                     
  glusterfs-client-xlators.x86_64 0:6.0-61.el7                                                                          
  glusterfs-libs.x86_64 0:6.0-61.el7                                                                                    
  glx-utils.x86_64 0:8.3.0-10.el7                                                                                       
  gnome-abrt.x86_64 0:0.3.4-9.el7                                                                                       
  gnome-bluetooth-libs.x86_64 1:3.28.2-1.el7                                                                            
  gnome-desktop3.x86_64 0:3.28.2-2.el7                                                                                  
  gnome-keyring.x86_64 0:3.28.2-1.el7                                                                                   
  gnome-keyring-pam.x86_64 0:3.28.2-1.el7                                                                               
  gnome-menus.x86_64 0:3.13.3-3.el7                                                                                     
  gnome-online-accounts.x86_64 0:3.28.2-1.el7                                                                           
  gnome-packagekit-common.x86_64 0:3.28.0-1.el7                                                                         
  gnome-packagekit-installer.x86_64 0:3.28.0-1.el7                                                                      
  gnome-shell-extension-alternate-tab.noarch 0:3.28.1-17.el7_9                                                          
  gnome-shell-extension-apps-menu.noarch 0:3.28.1-17.el7_9                                                              
  gnome-shell-extension-common.noarch 0:3.28.1-17.el7_9                                                                 
  gnome-shell-extension-horizontal-workspaces.noarch 0:3.28.1-17.el7_9                                                  
  gnome-shell-extension-launch-new-instance.noarch 0:3.28.1-17.el7_9                                                    
  gnome-shell-extension-places-menu.noarch 0:3.28.1-17.el7_9                                                            
  gnome-shell-extension-top-icons.noarch 0:3.28.1-17.el7_9                                                              
  gnome-shell-extension-user-theme.noarch 0:3.28.1-17.el7_9                                                             
  gnome-shell-extension-window-list.noarch 0:3.28.1-17.el7_9                                                            
  gnome-video-effects.noarch 0:0.4.3-1.el7                                                                              
  gom.x86_64 0:0.4-1.el7                                                                                                
  google-noto-emoji-color-fonts.noarch 0:20180508-4.el7                                                                 
  gperftools-libs.x86_64 0:2.6.1-1.el7                                                                                  
  graphite2.x86_64 0:1.3.10-1.el7_3                                                                                     
  grilo.x86_64 0:0.3.6-1.el7                                                                                            
  grilo-plugins.x86_64 0:0.3.7-1.el7                                                                                    
  gsettings-desktop-schemas.x86_64 0:3.28.0-3.el7                                                                       
  gsm.x86_64 0:1.0.13-11.el7                                                                                            
  gsound.x86_64 0:1.0.2-2.el7                                                                                           
  gspell.x86_64 0:1.6.1-1.el7                                                                                           
  gssdp.x86_64 0:1.0.2-1.el7                                                                                            
  gstreamer.x86_64 0:0.10.36-7.el7                                                                                      
  gstreamer-plugins-bad-free.x86_64 0:0.10.23-23.el7                                                                    
  gstreamer-plugins-base.x86_64 0:0.10.36-10.el7                                                                        
  gstreamer-plugins-good.x86_64 0:0.10.31-13.el7                                                                        
  gstreamer-tools.x86_64 0:0.10.36-7.el7                                                                                
  gstreamer1.x86_64 0:1.10.4-2.el7                                                                                      
  gstreamer1-plugins-bad-free.x86_64 0:1.10.4-3.el7                                                                     
  gstreamer1-plugins-base.x86_64 0:1.10.4-2.el7                                                                         
  gstreamer1-plugins-good.x86_64 0:1.10.4-2.el7                                                                         
  gstreamer1-plugins-ugly-free.x86_64 0:1.10.4-3.el7                                                                    
  gtk-update-icon-cache.x86_64 0:3.22.30-8.el7_9                                                                        
  gtk-vnc2.x86_64 0:0.7.0-3.el7                                                                                         
  gtk2.x86_64 0:2.24.31-1.el7                                                                                           
  gtk3.x86_64 0:3.22.30-8.el7_9                                                                                         
  gtkmm30.x86_64 0:3.22.2-1.el7                                                                                         
  gtksourceview3.x86_64 0:3.24.8-2.el7                                                                                  
  gucharmap-libs.x86_64 0:10.0.4-1.el7                                                                                  
  gupnp.x86_64 0:1.0.2-6.el7_9                                                                                          
  gupnp-av.x86_64 0:0.12.10-1.el7                                                                                       
  gupnp-dlna.x86_64 0:0.10.5-1.el7                                                                                      
  gupnp-igd.x86_64 0:0.2.5-2.el7                                                                                        
  gvfs.x86_64 0:1.36.2-7.el7_9                                                                                          
  gvfs-client.x86_64 0:1.36.2-7.el7_9                                                                                   
  gvnc.x86_64 0:0.7.0-3.el7                                                                                             
  harfbuzz.x86_64 0:1.7.5-2.el7                                                                                         
  harfbuzz-icu.x86_64 0:1.7.5-2.el7                                                                                     
  hicolor-icon-theme.noarch 0:0.12-7.el7                                                                                
  highcontrast-qt5.x86_64 0:0.1-2.el7                                                                                   
  hplip-common.x86_64 0:3.15.9-5.el7                                                                                    
  hplip-libs.x86_64 0:3.15.9-5.el7                                                                                      
  hunspell.x86_64 0:1.3.2-16.el7                                                                                        
  hunspell-en-US.noarch 0:0.20121024-6.el7                                                                              
  hyphen.x86_64 0:2.8.6-5.el7                                                                                           
  ibus.x86_64 0:1.5.17-12.el7_9                                                                                         
  ibus-gtk2.x86_64 0:1.5.17-12.el7_9                                                                                    
  ibus-gtk3.x86_64 0:1.5.17-12.el7_9                                                                                    
  ibus-libs.x86_64 0:1.5.17-12.el7_9                                                                                    
  ibus-setup.noarch 0:1.5.17-12.el7_9                                                                                   
  icedax.x86_64 0:1.1.11-25.el7                                                                                         
  initial-setup.x86_64 0:0.3.9.45-1.el7.centos                                                                          
  ipxe-roms-qemu.noarch 0:20180825-3.git133f4c.el7                                                                      
  iscsi-initiator-utils.x86_64 0:6.2.0.874-22.el7_9                                                                     
  iscsi-initiator-utils-iscsiuio.x86_64 0:6.2.0.874-22.el7_9                                                            
  iso-codes.noarch 0:3.46-2.el7                                                                                         
  isomd5sum.x86_64 1:1.0.10-5.el7                                                                                       
  jasper-libs.x86_64 0:1.900.1-33.el7                                                                                   
  json-glib.x86_64 0:1.4.2-2.el7                                                                                        
  keybinder3.x86_64 0:0.3.0-1.el7                                                                                       
  langtable.noarch 0:0.0.31-4.el7                                                                                       
  langtable-data.noarch 0:0.0.31-4.el7                                                                                  
  langtable-python.noarch 0:0.0.31-4.el7                                                                                
  lcms2.x86_64 0:2.6-3.el7                                                                                              
  ldns.x86_64 0:1.6.16-10.el7                                                                                           
  libXcomposite.x86_64 0:0.4.4-4.1.el7                                                                                  
  libXft.x86_64 0:2.3.2-2.el7                                                                                           
  libXpm.x86_64 0:3.5.12-2.el7_9                                                                                        
  libXres.x86_64 0:1.2.0-1.el7                                                                                          
  libXv.x86_64 0:1.0.11-1.el7                                                                                           
  libao.x86_64 0:1.1.0-8.el7                                                                                            
  libappstream-glib.x86_64 0:0.7.8-2.el7                                                                                
  libasyncns.x86_64 0:0.8-7.el7                                                                                         
  libatasmart.x86_64 0:0.19-6.el7                                                                                       
  libavc1394.x86_64 0:0.5.3-14.el7                                                                                      
  libblockdev.x86_64 0:2.18-5.el7                                                                                       
  libblockdev-crypto.x86_64 0:2.18-5.el7                                                                                
  libblockdev-fs.x86_64 0:2.18-5.el7                                                                                    
  libblockdev-loop.x86_64 0:2.18-5.el7                                                                                  
  libblockdev-mdraid.x86_64 0:2.18-5.el7                                                                                
  libblockdev-nvdimm.x86_64 0:2.18-5.el7                                                                                
  libblockdev-part.x86_64 0:2.18-5.el7                                                                                  
  libblockdev-swap.x86_64 0:2.18-5.el7                                                                                  
  libblockdev-utils.x86_64 0:2.18-5.el7                                                                                 
  libbluray.x86_64 0:0.2.3-6.el7                                                                                        
  libburn.x86_64 0:1.2.8-4.el7                                                                                          
  libbytesize.x86_64 0:1.2-1.el7                                                                                        
  libcacard.x86_64 40:2.7.0-1.el7                                                                                       
  libcanberra.x86_64 0:0.30-9.el7                                                                                       
  libcdio.x86_64 0:0.92-3.el7                                                                                           
  libcdio-paranoia.x86_64 0:10.2+0.90-11.el7                                                                            
  libcgroup.x86_64 0:0.41-21.el7                                                                                        
  libchamplain.x86_64 0:0.12.16-2.el7                                                                                   
  libchamplain-gtk.x86_64 0:0.12.16-2.el7                                                                               
  libconfig.x86_64 0:1.4.9-5.el7                                                                                        
  libdmapsharing.x86_64 0:2.9.37-1.el7                                                                                  
  libdv.x86_64 0:1.0.0-17.el7                                                                                           
  libdvdnav.x86_64 0:5.0.3-1.el7                                                                                        
  libdvdread.x86_64 0:5.0.3-3.el7                                                                                       
  libepoxy.x86_64 0:1.5.2-1.el7                                                                                         
  libevdev.x86_64 0:1.5.6-1.el7                                                                                         
  libexif.x86_64 0:0.6.22-2.el7_9                                                                                       
  libfprint.x86_64 0:0.8.2-1.el7                                                                                        
  libgcab1.x86_64 0:0.7-4.el7_4                                                                                         
  libgdata.x86_64 0:0.17.9-1.el7                                                                                        
  libgdither.x86_64 0:0.6-8.el7                                                                                         
  libgee.x86_64 0:0.20.1-1.el7                                                                                          
  libglade2.x86_64 0:2.6.4-11.el7                                                                                       
  libglvnd-egl.x86_64 1:1.0.1-0.8.git5baa1e5.el7                                                                        
  libglvnd-gles.x86_64 1:1.0.1-0.8.git5baa1e5.el7                                                                       
  libgnomekbd.x86_64 0:3.26.0-3.el7                                                                                     
  libgovirt.x86_64 0:0.3.4-5.el7                                                                                        
  libgphoto2.x86_64 0:2.5.15-3.el7                                                                                      
  libgs.x86_64 0:9.25-5.el7                                                                                             
  libgsf.x86_64 0:1.14.26-7.el7                                                                                         
  libgtop2.x86_64 0:2.38.0-3.el7                                                                                        
  libgudev1.x86_64 0:219-78.el7_9.7                                                                                     
  libgusb.x86_64 0:0.2.9-1.el7                                                                                          
  libgweather.x86_64 0:3.28.2-4.el7_9                                                                                   
  libgxps.x86_64 0:0.3.0-4.el7                                                                                          
  libibverbs.x86_64 0:22.4-6.el7_9                                                                                      
  libical.x86_64 0:3.0.3-2.el7                                                                                          
  libicu.x86_64 0:50.2-4.el7_7                                                                                          
  libiec61883.x86_64 0:1.2.0-10.el7                                                                                     
  libieee1284.x86_64 0:0.2.11-15.el7                                                                                    
  libimobiledevice.x86_64 0:1.2.0-1.el7                                                                                 
  libinput.x86_64 0:1.10.7-2.el7                                                                                        
  libiptcdata.x86_64 0:1.0.4-11.el7                                                                                     
  libiscsi.x86_64 0:1.9.0-7.el7                                                                                         
  libisofs.x86_64 0:1.2.8-4.el7                                                                                         
  libldb.x86_64 0:1.5.4-2.el7                                                                                           
  liblouis.x86_64 0:2.5.2-12.el7_4                                                                                      
  liblouis-python.noarch 0:2.5.2-12.el7_4                                                                               
  libmediaart.x86_64 0:1.9.4-1.el7                                                                                      
  libmodman.x86_64 0:2.0.1-8.el7                                                                                        
  libmpcdec.x86_64 0:1.2.6-12.el7                                                                                       
  libmtp.x86_64 0:1.1.14-1.el7                                                                                          
  libmusicbrainz5.x86_64 0:5.0.1-9.el7                                                                                  
  libnice.x86_64 0:0.1.3-4.el7                                                                                          
  libnl.x86_64 0:1.1.4-3.el7                                                                                            
  libnm-gtk.x86_64 0:1.8.6-2.el7                                                                                        
  libnma.x86_64 0:1.8.6-2.el7                                                                                           
  libnotify.x86_64 0:0.7.7-1.el7                                                                                        
  liboauth.x86_64 0:0.9.7-4.el7                                                                                         
  libofa.x86_64 0:0.9.3-24.el7                                                                                          
  libogg.x86_64 2:1.3.0-7.el7                                                                                           
  libosinfo.x86_64 0:1.1.0-5.el7                                                                                        
  libpaper.x86_64 0:1.1.24-9.el7                                                                                        
  libpcap.x86_64 14:1.5.3-13.el7_9                                                                                      
  libpeas.x86_64 0:1.22.0-1.el7                                                                                         
  libpeas-gtk.x86_64 0:1.22.0-1.el7                                                                                     
  libpeas-loader-python.x86_64 0:1.22.0-1.el7                                                                           
  libplist.x86_64 0:1.12-3.el7                                                                                          
  libproxy.x86_64 0:0.4.11-11.el7                                                                                       
  libpurple.x86_64 0:2.10.11-9.el7                                                                                      
  librados2.x86_64 1:10.2.5-4.el7                                                                                       
  libraw1394.x86_64 0:2.1.0-2.el7                                                                                       
  librbd1.x86_64 1:10.2.5-4.el7                                                                                         
  librdmacm.x86_64 0:22.4-6.el7_9                                                                                       
  libreport.x86_64 0:2.1.11-53.el7.centos                                                                               
  libreport-anaconda.x86_64 0:2.1.11-53.el7.centos                                                                      
  libreport-centos.x86_64 0:2.1.11-53.el7.centos                                                                        
  libreport-cli.x86_64 0:2.1.11-53.el7.centos                                                                           
  libreport-filesystem.x86_64 0:2.1.11-53.el7.centos                                                                    
  libreport-gtk.x86_64 0:2.1.11-53.el7.centos                                                                           
  libreport-plugin-bugzilla.x86_64 0:2.1.11-53.el7.centos                                                               
  libreport-plugin-mantisbt.x86_64 0:2.1.11-53.el7.centos                                                               
  libreport-plugin-reportuploader.x86_64 0:2.1.11-53.el7.centos                                                         
  libreport-plugin-rhtsupport.x86_64 0:2.1.11-53.el7.centos                                                             
  libreport-plugin-ureport.x86_64 0:2.1.11-53.el7.centos                                                                
  libreport-python.x86_64 0:2.1.11-53.el7.centos                                                                        
  libreport-rhel-anaconda-bugzilla.x86_64 0:2.1.11-53.el7.centos                                                        
  libreport-web.x86_64 0:2.1.11-53.el7.centos                                                                           
  libreswan.x86_64 0:3.25-9.1.el7_8                                                                                     
  libsecret.x86_64 0:0.18.6-1.el7                                                                                       
  libsemanage-python.x86_64 0:2.5-14.el7                                                                                
  libshout.x86_64 0:2.2.2-11.el7                                                                                        
  libsigc++20.x86_64 0:2.10.0-1.el7                                                                                     
  libsmbclient.x86_64 0:4.10.16-24.el7_9                                                                                
  libsmbios.x86_64 0:2.3.3-8.el7                                                                                        
  libsndfile.x86_64 0:1.0.25-12.el7_9.1                                                                                 
  libsoup.x86_64 0:2.62.2-2.el7                                                                                         
  libspectre.x86_64 0:0.2.8-1.el7                                                                                       
  libsrtp.x86_64 0:1.4.4-11.20101004cvs.el7                                                                             
  libtalloc.x86_64 0:2.1.16-1.el7                                                                                       
  libtar.x86_64 0:1.2.11-29.el7                                                                                         
  libtdb.x86_64 0:1.3.18-1.el7                                                                                          
  libtevent.x86_64 0:0.9.39-1.el7                                                                                       
  libthai.x86_64 0:0.1.14-9.el7                                                                                         
  libtheora.x86_64 1:1.1.1-8.el7                                                                                        
  libtimezonemap.x86_64 0:0.4.4-2.el7_9                                                                                 
  libtool-ltdl.x86_64 0:2.4.2-22.el7_3                                                                                  
  libudisks2.x86_64 0:2.8.4-1.el7                                                                                       
  libusal.x86_64 0:1.1.11-25.el7                                                                                        
  libusbmuxd.x86_64 0:1.0.10-5.el7                                                                                      
  libusbx.x86_64 0:1.0.21-1.el7                                                                                         
  libuser-python.x86_64 0:0.60-9.el7                                                                                    
  libv4l.x86_64 0:0.9.5-4.el7                                                                                           
  libvirt-daemon.x86_64 0:4.5.0-36.el7_9.5                                                                              
  libvirt-daemon-config-network.x86_64 0:4.5.0-36.el7_9.5                                                               
  libvirt-daemon-driver-interface.x86_64 0:4.5.0-36.el7_9.5                                                             
  libvirt-daemon-driver-network.x86_64 0:4.5.0-36.el7_9.5                                                               
  libvirt-daemon-driver-nodedev.x86_64 0:4.5.0-36.el7_9.5                                                               
  libvirt-daemon-driver-nwfilter.x86_64 0:4.5.0-36.el7_9.5                                                              
  libvirt-daemon-driver-qemu.x86_64 0:4.5.0-36.el7_9.5                                                                  
  libvirt-daemon-driver-secret.x86_64 0:4.5.0-36.el7_9.5                                                                
  libvirt-daemon-driver-storage.x86_64 0:4.5.0-36.el7_9.5                                                               
  libvirt-daemon-driver-storage-core.x86_64 0:4.5.0-36.el7_9.5                                                          
  libvirt-daemon-driver-storage-disk.x86_64 0:4.5.0-36.el7_9.5                                                          
  libvirt-daemon-driver-storage-gluster.x86_64 0:4.5.0-36.el7_9.5                                                       
  libvirt-daemon-driver-storage-iscsi.x86_64 0:4.5.0-36.el7_9.5                                                         
  libvirt-daemon-driver-storage-logical.x86_64 0:4.5.0-36.el7_9.5                                                       
  libvirt-daemon-driver-storage-mpath.x86_64 0:4.5.0-36.el7_9.5                                                         
  libvirt-daemon-driver-storage-rbd.x86_64 0:4.5.0-36.el7_9.5                                                           
  libvirt-daemon-driver-storage-scsi.x86_64 0:4.5.0-36.el7_9.5                                                          
  libvirt-daemon-kvm.x86_64 0:4.5.0-36.el7_9.5                                                                          
  libvirt-gconfig.x86_64 0:1.0.0-1.el7                                                                                  
  libvirt-glib.x86_64 0:1.0.0-1.el7                                                                                     
  libvirt-gobject.x86_64 0:1.0.0-1.el7                                                                                  
  libvirt-libs.x86_64 0:4.5.0-36.el7_9.5                                                                                
  libvisual.x86_64 0:0.4.0-16.el7                                                                                       
  libvorbis.x86_64 1:1.3.3-8.el7.1                                                                                      
  libvpx.x86_64 0:1.3.0-8.el7                                                                                           
  libwacom.x86_64 0:0.30-1.el7                                                                                          
  libwacom-data.noarch 0:0.30-1.el7                                                                                     
  libwayland-client.x86_64 0:1.15.0-1.el7                                                                               
  libwayland-cursor.x86_64 0:1.15.0-1.el7                                                                               
  libwayland-egl.x86_64 0:1.15.0-1.el7                                                                                  
  libwayland-server.x86_64 0:1.15.0-1.el7                                                                               
  libwbclient.x86_64 0:4.10.16-24.el7_9                                                                                 
  libwebp.x86_64 0:0.3.0-11.el7                                                                                         
  libwinpr.x86_64 0:2.1.1-5.el7_9                                                                                       
  libwnck3.x86_64 0:3.24.1-2.el7                                                                                        
  libxkbcommon.x86_64 0:0.7.1-3.el7                                                                                     
  libxkbcommon-x11.x86_64 0:0.7.1-3.el7                                                                                 
  libxklavier.x86_64 0:5.4-7.el7                                                                                        
  libxslt.x86_64 0:1.1.28-6.el7                                                                                         
  lldpad.x86_64 0:1.0.1-7.git036e314.el7_9                                                                              
  lockdev.x86_64 0:1.0.4-0.13.20111007git.el7                                                                           
  lzop.x86_64 0:1.03-10.el7                                                                                             
  mdadm.x86_64 0:4.1-9.el7_9                                                                                            
  meanwhile.x86_64 0:1.1.0-12.el7                                                                                       
  mesa-libEGL.x86_64 0:18.3.4-12.el7_9                                                                                  
  mesa-libgbm.x86_64 0:18.3.4-12.el7_9                                                                                  
  mobile-broadband-provider-info.noarch 0:1.20170310-1.el7                                                              
  mozjs52.x86_64 0:52.9.0-1.el7                                                                                         
  mpg123-libs.x86_64 0:1.25.6-1.el7                                                                                     
  mtdev.x86_64 0:1.1.5-5.el7                                                                                            
  mtools.x86_64 0:4.0.18-5.el7                                                                                          
  mutter.x86_64 0:3.28.3-32.el7_9                                                                                       
  nautilus-extensions.x86_64 0:3.26.3.1-7.el7                                                                           
  ncompress.x86_64 0:4.2.4.4-3.1.el7_8                                                                                  
  ndctl.x86_64 0:65-6.el7_9                                                                                             
  ndctl-libs.x86_64 0:65-6.el7_9                                                                                        
  neon.x86_64 0:0.30.0-4.el7                                                                                            
  net-snmp-libs.x86_64 1:5.7.2-49.el7_9.2                                                                               
  netcf-libs.x86_64 0:0.2.8-4.el7                                                                                       
  nmap-ncat.x86_64 2:6.40-19.el7                                                                                        
  numad.x86_64 0:0.5-18.20150602git.el7                                                                                 
  oddjob.x86_64 0:0.31.5-4.el7                                                                                          
  oddjob-mkhomedir.x86_64 0:0.31.5-4.el7                                                                                
  openjpeg-libs.x86_64 0:1.5.1-18.el7                                                                                   
  openjpeg2.x86_64 0:2.3.1-3.el7_7                                                                                      
  opus.x86_64 0:1.0.2-6.el7                                                                                             
  orc.x86_64 0:0.4.26-1.el7                                                                                             
  osinfo-db.noarch 0:20200529-1.el7                                                                                     
  osinfo-db-tools.x86_64 0:1.1.0-1.el7                                                                                  
  pakchois.x86_64 0:0.4-10.el7                                                                                          
  pango.x86_64 0:1.42.4-4.el7_7                                                                                         
  pangomm.x86_64 0:2.40.1-1.el7                                                                                         
  pcre2.x86_64 0:10.23-2.el7                                                                                            
  pcre2-utf16.x86_64 0:10.23-2.el7                                                                                      
  pinentry-gtk.x86_64 0:0.8.1-17.el7                                                                                    
  policycoreutils-python.x86_64 0:2.5-34.el7                                                                            
  poppler.x86_64 0:0.26.5-43.el7.1                                                                                      
  poppler-data.noarch 0:0.4.6-3.el7                                                                                     
  poppler-glib.x86_64 0:0.26.5-43.el7.1                                                                                 
  pulseaudio.x86_64 0:10.0-6.el7_9                                                                                      
  pulseaudio-gdm-hooks.x86_64 0:10.0-6.el7_9                                                                            
  pulseaudio-libs.x86_64 0:10.0-6.el7_9                                                                                 
  pulseaudio-libs-glib2.x86_64 0:10.0-6.el7_9                                                                           
  pulseaudio-module-bluetooth.x86_64 0:10.0-6.el7_9                                                                     
  pycairo.x86_64 0:1.8.10-8.el7                                                                                         
  pygobject2.x86_64 0:2.28.6-11.el7                                                                                     
  pygtk2.x86_64 0:2.24.0-9.el7                                                                                          
  pygtk2-libglade.x86_64 0:2.24.0-9.el7                                                                                 
  pykickstart.noarch 0:1.99.66.22-1.el7                                                                                 
  pyparted.x86_64 1:3.9-15.el7                                                                                          
  python-IPy.noarch 0:0.75-6.el7                                                                                        
  python-augeas.noarch 0:0.5.0-2.el7                                                                                    
  python-backports.x86_64 0:1.0-8.el7                                                                                   
  python-backports-ssl_match_hostname.noarch 0:3.5.0.1-1.el7                                                            
  python-blivet.noarch 1:0.61.15.76-1.el7_9                                                                             
  python-brlapi.x86_64 0:0.6.0-16.el7                                                                                   
  python-coverage.x86_64 0:3.6-0.5.b3.el7                                                                               
  python-deltarpm.x86_64 0:3.6-3.el7                                                                                    
  python-di.noarch 0:0.3-2.el7                                                                                          
  python-ethtool.x86_64 0:0.8-8.el7                                                                                     
  python-gobject.x86_64 0:3.22.0-1.el7_4.1                                                                              
  python-inotify.noarch 0:0.9.4-4.el7                                                                                   
  python-ipaddress.noarch 0:1.0.16-2.el7                                                                                
  python-meh.noarch 0:0.25.3-1.el7                                                                                      
  python-meh-gui.noarch 0:0.25.3-1.el7                                                                                  
  python-nss.x86_64 0:0.16.0-3.el7                                                                                      
  python-ntplib.noarch 0:0.3.2-1.el7                                                                                    
  python-pwquality.x86_64 0:1.2.3-5.el7                                                                                 
  python-pyblock.x86_64 0:0.53-6.el7                                                                                    
  python-setuptools.noarch 0:0.9.8-7.el7                                                                                
  python-six.noarch 0:1.9.0-2.el7                                                                                       
  python2-blockdev.x86_64 0:2.18-5.el7                                                                                  
  python2-futures.noarch 0:3.1.1-5.el7                                                                                  
  python2-pyatspi.noarch 0:2.26.0-3.el7                                                                                 
  python2-subprocess32.x86_64 0:3.2.6-14.el7                                                                            
  pytz.noarch 0:2016.10-2.el7                                                                                           
  qemu-img.x86_64 10:1.5.3-175.el7_9.6                                                                                  
  qemu-kvm.x86_64 10:1.5.3-175.el7_9.6                                                                                  
  qemu-kvm-common.x86_64 10:1.5.3-175.el7_9.6                                                                           
  qt5-qtbase.x86_64 0:5.9.7-5.el7_9                                                                                     
  qt5-qtbase-common.noarch 0:5.9.7-5.el7_9                                                                              
  qt5-qtbase-gui.x86_64 0:5.9.7-5.el7_9                                                                                 
  radvd.x86_64 0:2.17-3.el7                                                                                             
  rdma-core.x86_64 0:22.4-6.el7_9                                                                                       
  realmd.x86_64 0:0.16.1-12.el7_9.1                                                                                     
  redhat-menus.noarch 0:12.0.2-8.el7                                                                                    
  rest.x86_64 0:0.8.1-2.el7                                                                                             
  rsync.x86_64 0:3.1.2-12.el7_9                                                                                         
  rtkit.x86_64 0:0.11-10.el7                                                                                            
  samba-client-libs.x86_64 0:4.10.16-24.el7_9                                                                           
  samba-common.noarch 0:4.10.16-24.el7_9                                                                                
  samba-common-libs.x86_64 0:4.10.16-24.el7_9                                                                           
  sane-backends.x86_64 0:1.0.24-12.el7                                                                                  
  sane-backends-libs.x86_64 0:1.0.24-12.el7                                                                             
  satyr.x86_64 0:0.13-15.el7                                                                                            
  sbc.x86_64 0:1.0-5.el7                                                                                                
  seabios-bin.noarch 0:1.11.0-2.el7                                                                                     
  seavgabios-bin.noarch 0:1.11.0-2.el7                                                                                  
  setools-libs.x86_64 0:3.3.8-4.el7                                                                                     
  setroubleshoot-plugins.noarch 0:3.0.67-4.el7                                                                          
  setroubleshoot-server.x86_64 0:3.2.30-8.el7                                                                           
  sgabios-bin.noarch 1:0.20110622svn-4.el7                                                                              
  sgpio.x86_64 0:1.2.0.10-13.el7                                                                                        
  sos.noarch 0:3.9-5.el7.centos.11                                                                                      
  sound-theme-freedesktop.noarch 0:0.8-3.el7                                                                            
  soundtouch.x86_64 0:1.4.0-9.el7                                                                                       
  sox.x86_64 0:14.4.1-7.el7                                                                                             
  speech-dispatcher.x86_64 0:0.7.1-15.el7                                                                               
  speech-dispatcher-python.x86_64 0:0.7.1-15.el7                                                                        
  speex.x86_64 0:1.2-0.19.rc1.el7                                                                                       
  spice-glib.x86_64 0:0.35-5.el7_9.1                                                                                    
  spice-gtk3.x86_64 0:0.35-5.el7_9.1                                                                                    
  spice-server.x86_64 0:0.14.0-9.el7_9.1                                                                                
  startup-notification.x86_64 0:0.12-8.el7                                                                              
  systemd-python.x86_64 0:219-78.el7_9.7                                                                                
  taglib.x86_64 0:1.8-8.20130218git.el7                                                                                 
  telepathy-farstream.x86_64 0:0.6.0-5.el7                                                                              
  telepathy-filesystem.noarch 0:0.0.2-6.el7                                                                             
  telepathy-gabble.x86_64 0:0.18.1-4.el7                                                                                
  telepathy-glib.x86_64 0:0.24.1-1.el7                                                                                  
  telepathy-haze.x86_64 0:0.8.0-1.el7                                                                                   
  telepathy-logger.x86_64 0:0.8.0-5.el7                                                                                 
  telepathy-mission-control.x86_64 1:5.16.3-3.el7                                                                       
  telepathy-salut.x86_64 0:0.8.1-6.el7                                                                                  
  totem-pl-parser.x86_64 0:3.26.1-1.el7                                                                                 
  tracker.x86_64 0:1.10.5-8.el7                                                                                         
  udisks2.x86_64 0:2.8.4-1.el7                                                                                          
  unbound-libs.x86_64 0:1.6.6-5.el7_8                                                                                   
  upower.x86_64 0:0.99.7-1.el7                                                                                          
  urw-base35-bookman-fonts.noarch 0:20170801-10.el7                                                                     
  urw-base35-c059-fonts.noarch 0:20170801-10.el7                                                                        
  urw-base35-d050000l-fonts.noarch 0:20170801-10.el7                                                                    
  urw-base35-fonts.noarch 0:20170801-10.el7                                                                             
  urw-base35-fonts-common.noarch 0:20170801-10.el7                                                                      
  urw-base35-gothic-fonts.noarch 0:20170801-10.el7                                                                      
  urw-base35-nimbus-mono-ps-fonts.noarch 0:20170801-10.el7                                                              
  urw-base35-nimbus-roman-fonts.noarch 0:20170801-10.el7                                                                
  urw-base35-nimbus-sans-fonts.noarch 0:20170801-10.el7                                                                 
  urw-base35-p052-fonts.noarch 0:20170801-10.el7                                                                        
  urw-base35-standard-symbols-ps-fonts.noarch 0:20170801-10.el7                                                         
  urw-base35-z003-fonts.noarch 0:20170801-10.el7                                                                        
  usbmuxd.x86_64 0:1.1.0-1.el7                                                                                          
  usbredir.x86_64 0:0.7.1-3.el7                                                                                         
  usermode.x86_64 0:1.111-6.el7                                                                                         
  volume_key-libs.x86_64 0:0.3.9-9.el7                                                                                  
  vorbis-tools.x86_64 1:1.4.0-13.el7                                                                                    
  vte-profile.x86_64 0:0.52.4-1.el7                                                                                     
  vte291.x86_64 0:0.52.4-1.el7                                                                                          
  wavpack.x86_64 0:4.60.1-9.el7                                                                                         
  webkitgtk3.x86_64 0:2.4.11-2.el7                                                                                      
  webkitgtk4.x86_64 0:2.28.2-3.el7                                                                                      
  webkitgtk4-jsc.x86_64 0:2.28.2-3.el7                                                                                  
  webrtc-audio-processing.x86_64 0:0.3-1.el7                                                                            
  wodim.x86_64 0:1.1.11-25.el7                                                                                          
  xcb-util.x86_64 0:0.4.0-2.el7                                                                                         
  xcb-util-image.x86_64 0:0.4.0-2.el7                                                                                   
  xcb-util-keysyms.x86_64 0:0.4.0-1.el7                                                                                 
  xcb-util-renderutil.x86_64 0:0.3.9-3.el7                                                                              
  xcb-util-wm.x86_64 0:0.4.1-5.el7                                                                                      
  xdg-desktop-portal.x86_64 0:1.0.2-1.el7                                                                               
  xdg-user-dirs.x86_64 0:0.15-5.el7                                                                                     
  xdg-utils.noarch 0:1.1.0-0.17.20120809git.el7                                                                         
  xml-common.noarch 0:0.6.3-39.el7                                                                                      
  xmlrpc-c.x86_64 0:1.32.5-1905.svn2451.el7                                                                             
  xmlrpc-c-client.x86_64 0:1.32.5-1905.svn2451.el7                                                                      
  xorg-x11-font-utils.x86_64 1:7.5-21.el7                                                                               
  yajl.x86_64 0:2.0.4-4.el7                                                                                             
  yelp-libs.x86_64 2:3.28.1-1.el7                                                                                       
  yelp-xsl.noarch 0:3.28.0-1.el7                                                                                        
  zenity.x86_64 0:3.28.1-2.el7_9                                                                                        

Complete!
[root@centos ~]# enable xrdp --now  
-bash: enable: xrdp: not a shell builtin
-bash: enable: --now: not a shell builtin
[root@centos ~]# sudo systemctl enable xrdp
Created symlink from /etc/systemd/system/multi-user.target.wants/xrdp.service to /usr/lib/systemd/system/xrdp.service.
[root@centos ~]# sudo systemctl start xrdp
[root@centos ~]# sudo systemctl status xrdp
● xrdp.service - xrdp daemon
   Loaded: loaded (/usr/lib/systemd/system/xrdp.service; enabled; vendor preset: disabled)
   Active: active (running) since Tue 2023-08-22 18:03:01 CST; 1min 32s ago
     Docs: man:xrdp(8)
           man:xrdp.ini(5)
 Main PID: 4746 (xrdp)
    Tasks: 1
   CGroup: /system.slice/xrdp.service
           └─4746 /usr/sbin/xrdp --nodaemon

Aug 22 18:03:01 centos systemd[1]: Started xrdp daemon.
Aug 22 18:03:01 centos xrdp[4746]: [INFO ] starting xrdp with pid 4746
Aug 22 18:03:01 centos xrdp[4746]: [INFO ] address [0.0.0.0] port [3389] mode 1
Aug 22 18:03:01 centos xrdp[4746]: [INFO ] listening to port 3389 on 0.0.0.0
Aug 22 18:03:01 centos xrdp[4746]: [INFO ] xrdp_listen_pp done
[root@centos ~]# vim /etc/xrdp/xrdp.ini
[root@centos ~]# systemctl restart xrdp
[root@centos ~]# sudo systemctl status xrdp
● xrdp.service - xrdp daemon
   Loaded: loaded (/usr/lib/systemd/system/xrdp.service; enabled; vendor preset: disabled)
   Active: active (running) since Tue 2023-08-22 18:05:10 CST; 11s ago
     Docs: man:xrdp(8)
           man:xrdp.ini(5)
 Main PID: 4760 (xrdp)
    Tasks: 1
   CGroup: /system.slice/xrdp.service
           └─4760 /usr/sbin/xrdp --nodaemon

Aug 22 18:05:10 centos systemd[1]: Started xrdp daemon.
Aug 22 18:05:10 centos xrdp[4760]: [INFO ] starting xrdp with pid 4760
Aug 22 18:05:10 centos xrdp[4760]: [INFO ] address [0.0.0.0] port [3389] mode 1
Aug 22 18:05:10 centos xrdp[4760]: [INFO ] listening to port 3389 on 0.0.0.0
Aug 22 18:05:10 centos xrdp[4760]: [INFO ] xrdp_listen_pp done
[root@centos ~]# sudo systemctl status xrdp
● xrdp.service - xrdp daemon
   Loaded: loaded (/usr/lib/systemd/system/xrdp.service; enabled; vendor preset: disabled)
   Active: active (running) since Tue 2023-08-22 18:05:10 CST; 16s ago
     Docs: man:xrdp(8)
           man:xrdp.ini(5)
 Main PID: 4760 (xrdp)
    Tasks: 1
   CGroup: /system.slice/xrdp.service
           └─4760 /usr/sbin/xrdp --nodaemon

Aug 22 18:05:10 centos systemd[1]: Started xrdp daemon.
Aug 22 18:05:10 centos xrdp[4760]: [INFO ] starting xrdp with pid 4760
Aug 22 18:05:10 centos xrdp[4760]: [INFO ] address [0.0.0.0] port [3389] mode 1
Aug 22 18:05:10 centos xrdp[4760]: [INFO ] listening to port 3389 on 0.0.0.0
Aug 22 18:05:10 centos xrdp[4760]: [INFO ] xrdp_listen_pp done
[root@centos ~]# systemctl stop firewalld
[root@centos ~]# systemctl disable firewalld
Removed symlink /etc/systemd/system/multi-user.target.wants/firewalld.service.
Removed symlink /etc/systemd/system/dbus-org.fedoraproject.FirewallD1.service.
[root@centos ~]# yum install -y nvidia-detect
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirrors.tuna.tsinghua.edu.cn
 * epel: mirrors.tuna.tsinghua.edu.cn
 * extras: mirrors.bupt.edu.cn
 * updates: mirrors.tuna.tsinghua.edu.cn
No package nvidia-detect available.
Error: Nothing to do
[root@centos ~]# rpm -Uvh http://www.elrepo.org/elrepo-release-7.0-2.el7.elrepo.noarch.rpm
Retrieving http://www.elrepo.org/elrepo-release-7.0-2.el7.elrepo.noarch.rpm
Retrieving http://elrepo.org/elrepo-release-7.0-4.el7.elrepo.noarch.rpm
warning: /var/tmp/rpm-tmp.w1oz9V: Header V4 DSA/SHA1 Signature, key ID baadae52: NOKEY
Preparing...                          ################################# [100%]
Updating / installing...
   1:elrepo-release-7.0-4.el7.elrepo  ################################# [100%]
[root@centos ~]# yum install -y nvidia-detect
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirrors.tuna.tsinghua.edu.cn
 * elrepo: mirrors.tuna.tsinghua.edu.cn
 * epel: mirrors.tuna.tsinghua.edu.cn
 * extras: mirrors.bupt.edu.cn
 * updates: mirrors.tuna.tsinghua.edu.cn
elrepo                                                                                           | 3.0 kB  00:00:00     
elrepo/primary_db                                                                                | 357 kB  00:00:00     
Resolving Dependencies
--> Running transaction check
---> Package nvidia-detect.x86_64 0:525.85.05-1.el7.elrepo will be installed
--> Finished Dependency Resolution

Dependencies Resolved

========================================================================================================================
 Package                      Arch                  Version                                 Repository             Size
========================================================================================================================
Installing:
 nvidia-detect                x86_64                525.85.05-1.el7.elrepo                  elrepo                 27 k

Transaction Summary
========================================================================================================================
Install  1 Package

Total download size: 27 k
Installed size: 37 k
Downloading packages:
warning: /var/cache/yum/x86_64/7/elrepo/packages/nvidia-detect-525.85.05-1.el7.elrepo.x86_64.rpm: Header V4 DSA/SHA256 Signature, key ID baadae52: NOKEY
Public key for nvidia-detect-525.85.05-1.el7.elrepo.x86_64.rpm is not installed
nvidia-detect-525.85.05-1.el7.elrepo.x86_64.rpm                                                  |  27 kB  00:00:00     
Retrieving key from file:///etc/pki/rpm-gpg/RPM-GPG-KEY-elrepo.org
Importing GPG key 0xBAADAE52:
 Userid     : "elrepo.org (RPM Signing Key for elrepo.org) <secure@elrepo.org>"
 Fingerprint: 96c0 104f 6315 4731 1e0b b1ae 309b c305 baad ae52
 Package    : elrepo-release-7.0-4.el7.elrepo.noarch (installed)
 From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-elrepo.org
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
Warning: RPMDB altered outside of yum.
  Installing : nvidia-detect-525.85.05-1.el7.elrepo.x86_64                                                          1/1 
  Verifying  : nvidia-detect-525.85.05-1.el7.elrepo.x86_64                                                          1/1 

Installed:
  nvidia-detect.x86_64 0:525.85.05-1.el7.elrepo                                                                         

Complete!
[root@centos ~]# yum install -y kmod
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirrors.tuna.tsinghua.edu.cn
 * elrepo: mirrors.tuna.tsinghua.edu.cn
 * epel: mirrors.tuna.tsinghua.edu.cn
 * extras: mirrors.bupt.edu.cn
 * updates: mirrors.tuna.tsinghua.edu.cn
Package kmod-20-28.el7.x86_64 already installed and latest version
Nothing to do
[root@centos ~]# nvidia-detect
kmod-nvidia
WARNING: Xorg log file /var/log/Xorg.0.log does not exist
WARNING: Unable to determine Xorg ABI compatibility
WARNING: The driver for this device does not support the current Xorg version
[root@centos ~]# -470xx
-bash: -470xx: command not found
[root@centos ~]# 1
-bash: 1: command not found
[root@centos ~]# -470xx
-bash: -470xx: command not found
[root@centos ~]# 1
-bash: 1: command not found
[root@centos ~]# yum search kmod-nvidi
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirrors.tuna.tsinghua.edu.cn
 * elrepo: mirrors.tuna.tsinghua.edu.cn
 * epel: mirrors.tuna.tsinghua.edu.cn
 * extras: mirrors.bupt.edu.cn
 * updates: mirrors.tuna.tsinghua.edu.cn
=============================================== N/S matched: kmod-nvidi ================================================
kmod-nvidia.x86_64 : nvidia kernel module(s)
kmod-nvidia-340xx.x86_64 : nvidia-340xx kernel module(s)
kmod-nvidia-390xx.x86_64 : nvidia-390xx kernel module(s)
kmod-nvidia-470xx.x86_64 : nvidia-470xx kernel module(s)

  Name and summary matches only, use "search all" for everything.
[root@centos ~]# yum -y install kmod-nvidia-470xx.x86_64^C
[root@centos ~]# yum search all kmod-nvidi
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirrors.tuna.tsinghua.edu.cn
 * elrepo: mirrors.tuna.tsinghua.edu.cn
 * epel: mirrors.tuna.tsinghua.edu.cn
 * extras: mirrors.bupt.edu.cn
 * updates: mirrors.tuna.tsinghua.edu.cn
================================================= Matched: kmod-nvidi ==================================================
kmod-nvidia.x86_64 : nvidia kernel module(s)
kmod-nvidia-340xx.x86_64 : nvidia-340xx kernel module(s)
kmod-nvidia-390xx.x86_64 : nvidia-390xx kernel module(s)
kmod-nvidia-470xx.x86_64 : nvidia-470xx kernel module(s)
[root@centos ~]# yum -y install kmod-nvidia-470xx.x86_64
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirrors.tuna.tsinghua.edu.cn
 * elrepo: mirrors.tuna.tsinghua.edu.cn
 * epel: mirrors.tuna.tsinghua.edu.cn
 * extras: mirrors.bupt.edu.cn
 * updates: mirrors.tuna.tsinghua.edu.cn
Resolving Dependencies
--> Running transaction check
---> Package kmod-nvidia-470xx.x86_64 0:470.199.02-1.el7_9.elrepo will be installed
--> Processing Dependency: nvidia-x11-drv-470xx = 470.199.02 for package: kmod-nvidia-470xx-470.199.02-1.el7_9.elrepo.x86_64
--> Running transaction check
---> Package nvidia-x11-drv-470xx.x86_64 0:470.199.02-1.el7_9.elrepo will be installed
--> Processing Dependency: nvidia-x11-drv-470xx-libs(x86-64) = 470.199.02-1.el7_9.elrepo for package: nvidia-x11-drv-470xx-470.199.02-1.el7_9.elrepo.x86_64
--> Processing Dependency: xorg-x11-server-Xorg <= 1.20.99 for package: nvidia-x11-drv-470xx-470.199.02-1.el7_9.elrepo.x86_64
--> Processing Dependency: vulkan-filesystem for package: nvidia-x11-drv-470xx-470.199.02-1.el7_9.elrepo.x86_64
--> Processing Dependency: libnvidia-glcore.so.470.199.02()(64bit) for package: nvidia-x11-drv-470xx-470.199.02-1.el7_9.elrepo.x86_64
--> Processing Dependency: libnvidia-ml.so.1()(64bit) for package: nvidia-x11-drv-470xx-470.199.02-1.el7_9.elrepo.x86_64
--> Processing Dependency: libnvidia-tls.so.470.199.02()(64bit) for package: nvidia-x11-drv-470xx-470.199.02-1.el7_9.elrepo.x86_64
--> Running transaction check
---> Package nvidia-x11-drv-470xx-libs.x86_64 0:470.199.02-1.el7_9.elrepo will be installed
--> Processing Dependency: libvdpau(x86-64) >= 1.0 for package: nvidia-x11-drv-470xx-libs-470.199.02-1.el7_9.elrepo.x86_64
--> Processing Dependency: libglvnd-opengl(x86-64) >= 1.0 for package: nvidia-x11-drv-470xx-libs-470.199.02-1.el7_9.elrepo.x86_64
---> Package vulkan-filesystem.noarch 0:1.1.97.0-1.el7 will be installed
---> Package xorg-x11-server-Xorg.x86_64 0:1.20.4-23.el7_9 will be installed
--> Processing Dependency: xorg-x11-server-common >= 1.20.4-23.el7_9 for package: xorg-x11-server-Xorg-1.20.4-23.el7_9.x86_64
--> Running transaction check
---> Package libglvnd-opengl.x86_64 1:1.0.1-0.8.git5baa1e5.el7 will be installed
---> Package libvdpau.x86_64 0:1.1.1-3.el7 will be installed
---> Package xorg-x11-server-common.x86_64 0:1.20.4-23.el7_9 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

========================================================================================================================
 Package                              Arch              Version                                Repository          Size
========================================================================================================================
Installing:
 kmod-nvidia-470xx                    x86_64            470.199.02-1.el7_9.elrepo              elrepo              48 M
Installing for dependencies:
 libglvnd-opengl                      x86_64            1:1.0.1-0.8.git5baa1e5.el7             base                43 k
 libvdpau                             x86_64            1.1.1-3.el7                            base                34 k
 nvidia-x11-drv-470xx                 x86_64            470.199.02-1.el7_9.elrepo              elrepo             4.4 M
 nvidia-x11-drv-470xx-libs            x86_64            470.199.02-1.el7_9.elrepo              elrepo             181 M
 vulkan-filesystem                    noarch            1.1.97.0-1.el7                         base               6.3 k
 xorg-x11-server-Xorg                 x86_64            1.20.4-23.el7_9                        updates            1.5 M
 xorg-x11-server-common               x86_64            1.20.4-23.el7_9                        updates             57 k

Transaction Summary
========================================================================================================================
Install  1 Package (+7 Dependent packages)

Total download size: 236 M
Installed size: 612 M
Downloading packages:
(1/8): libvdpau-1.1.1-3.el7.x86_64.rpm                                                           |  34 kB  00:00:00     
(2/8): libglvnd-opengl-1.0.1-0.8.git5baa1e5.el7.x86_64.rpm                                       |  43 kB  00:00:00     
(3/8): vulkan-filesystem-1.1.97.0-1.el7.noarch.rpm                                               | 6.3 kB  00:00:00     
(4/8): xorg-x11-server-common-1.20.4-23.el7_9.x86_64.rpm                                         |  57 kB  00:00:00     
(5/8): xorg-x11-server-Xorg-1.20.4-23.el7_9.x86_64.rpm                                           | 1.5 MB  00:00:03     
(6/8): nvidia-x11-drv-470xx-470.199.02-1.el7_9.elrepo.x86_64.rpm                                 | 4.4 MB  00:00:04     
(7/8): kmod-nvidia-470xx-470.199.02-1.el7_9.e 27% [=========-                         ] 4.6 MB/s |  66 MB  00:00:36 ETA 

```