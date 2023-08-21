---
title: conda
date: 2023-08-17 16:14:50
tags: server
---

![image](../img/IMG_20180806_121455.jpg)

## Miniconda
Miniconda is a free minimal installer for conda. It is a small, bootstrap version of Anaconda that includes only conda, Python, the packages they depend on, and a small number of other useful packages, including pip, zlib and a few others. Use the conda install command to install 720+ additional conda packages from the Anaconda repository.

See if Miniconda is right for you.

## System requirements
License: Free use and redistribution under the terms of the EULA for Miniconda.
Operating system: Windows 10 or newer, 64-bit macOS 10.13+, or Linux, including Ubuntu, RedHat, CentOS 7+, and others.
If your operating system is older than what is currently supported, you can find older versions of the Miniconda installers in our archive that might work for you.
System architecture: Windows- 64-bit x86, 32-bit x86; macOS- 64-bit x86 & Apple M1 (ARM64); Linux- 64-bit x86, 64-bit aarch64 (AWS Graviton2), 64-bit IBM Power8/Power9, s390x (Linux on IBM Z & LinuxONE).
The linux-aarch64 Miniconda installer requires glibc >=2.26 and thus will not work with CentOS 7, Ubuntu 16.04, or Debian 9 (“stretch”).
Minimum 400 MB disk space to download and install.
On Windows, macOS, and Linux, it is best to install Miniconda for the local user, which does not require administrator permissions and is the most robust type of installation. However, if you need to, you can install Miniconda system wide, which does require administrator permissions.

## Installing 
```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-py310_23.5.2-0-Linux-x86_64.sh
mkdir -p /opt/module
bash Miniconda3-py310_23.5.2-0-Linux-x86_64.sh -b -p /opt/module/miniconda3/
/opt/module/miniconda3/bin/conda init
source ~/.bashrc
```

```bash
$ conda install numpy
```
...
```bash
$ conda create -n py3k anaconda python=3
```
...
There are two variants of the installer: Miniconda is Python 2 based and Miniconda3 is Python 3 based. Note that the choice of which Miniconda is installed only affects the root environment. Regardless of which version of Miniconda you install, you can still install both Python 2.x and Python 3.x environments.

The other difference is that the Python 3 version of Miniconda will default to Python 3 when creating new environments and building packages. So for instance, the behavior of:
```bash
$ conda create -n myenv python
```
will be to install Python 2.7 with the Python 2 Miniconda and to install Python 3.10 with the Python 3 Miniconda. You can override the default by explicitly setting python=2 or python=3. It also determines the default value of CONDA_PY when using conda build.

Note

If you already have Miniconda or Anaconda installed, and you just want to upgrade, you should not use the installer. Just use conda update.

For instance:
```bash
$ conda update conda
```