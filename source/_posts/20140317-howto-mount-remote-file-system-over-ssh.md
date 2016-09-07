---
title: >-
  How to mount a remote file system over ssh
date: 2014-03-17 10:54:00
categories:
  - HOWTO
subcategories:
  - Mount Remote Filesystem
tags:
  - fuse
  - homebrew
  - macosx
  - sqlite
  - ssh
  - sshfs
  - vagrant
  - virtualbox
---

The following post describes how to mount a remote file system over `ssh` on Mac OS X 10.9.2. With minor modifications, the same thing can be achieved on other platforms.

#### Background

I recently needed to manipulate a `sqlite` database on a virtual machine and my gui tool lacked the ability to tunnel over `ssh`.

Enter `sshfs`: Secure SHell FileSystem – a file system for Linux (and other operating systems with a FUSE implementation, such as Mac OS X or FreeBSD) capable of operating on files on a remote computer using just a secure shell login on the remote computer.

In the example below, I’m mounting a file system from a VirtualBox virtual machine controlled by `vagrant` (which happens to use port 2200 on the loopback address 127.0.0.1).

#### Prerequisites

- Mac OS X 10.9.2
- [Homebrew](http://brew.sh)

#### Installation

Install `sshfs` via Homebrew:

```` bash
$ brew install sshfs
````

Follow instructions for `osxfuse` (refer to `brew info osxfuse`):

```` bash
$ mount -t osxfusefs
$ sudo kextunload -b com.github.osxfuse.filesystems.osxfusefs
$ sudo /bin/cp -RfX /usr/local/Cellar/osxfuse/2.6.2/Library/Filesystems/osxfusefs.fs /Library/Filesystems
$ sudo chmod +s /Library/Filesystems/osxfusefs.fs/Support/load_osxfusefs
````

The remote file system is now mounted at `/Volumes/mount_name` and one can access files via Mac OS applications and/or the Finder.

#### Unmount

Close any open files and `cd` out of the `mount_name` directory before executing the following command to unmount the remote file system:

```` bash
$ umount /Volumes/mount_name
````

#### Conclusion

`sshfs` is a lightweight solution to efficiently mount a remote file system for local access.

####  Reference(s)

- [SSH Filesystem](https://github.com/libfuse/sshfs)
