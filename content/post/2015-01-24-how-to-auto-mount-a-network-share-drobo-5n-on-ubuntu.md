---
title: How To Auto Mount a Network Share (Drobo 5N) on Ubuntu
author: logan
layout: post
date: 2015-01-24
url: /2015/01/how-to-auto-mount-a-network-share-drobo-5n-on-ubuntu/
categories:
  - Stuff
tags:
  - cifs
  - drobo 5n
  - linux
  - plex
  - ubuntu
---
Fed up with the performance limitations of running Plex Media Server, or PMS, (which I really love) on our Drobo 5N, I decided (with my wife&#8217;s scrupulous approval) to build a dedicated PMS box to handle future 1080p streams. Being that the Drobo is still highly capable as a media server in general, I&#8217;m keeping all of our media there and will just use that to serve content to the new PMS box. I have a small amount of experience with Linux, but this gave me an opportunity to dive into it a bit more, while being able to enjoy movies on the big screen.

The main hurdle I ran into is mounting a network share. Mac OSX and Windows really makes this stupid easy, but in Ubuntu, there is some config needed to have the server ready to serve (forgive the pun) when the computer boots up.

_Note: Some of this may pertain to just Plex configuration, but I believe it&#8217;s helpful in general_

After installing Plex (not the client, the media server), make sure to install two Linux utilities:

  * `cifs-utils` (Allows for the use of CIFS, a sort of newer replacement for Samba (or SMB. The details of different file systems are out of scope for this post)
  * `avahi` (Allows us to grab our local server by its hostname (friendly name) rather than specifying the IP address of the device. Think of it as a local DNS)

With that out of the way, let&#8217;s get the mount point ready.

```
$ sudo mkdir /mnt/shares/server
```

Feel free to replace `server` with whatever name you want. Our server is named R2 after an [obscure science-fiction universe][1] from the mind of George Lucas. 😉

Next, we need to edit a configuration file known as `fstab`, which will handle auto mounting the share for us when the pc restarts.

Use whatever editor you are comfortable with (vi, nano, or Gedit). I used Gedit since my keyboard was mapped in a weird way with vi.

```
$ sudo gedit /etc/fstab
```

This opens the file for editing. Follow this pattern to get the server setup:

```
//server.local /mnt/shares/server cifs username=mickey,password=mouse,iocharset=utf8,sec=ntlm 0 0
```

Of course, replace the username and password with whatever you are using.Some shares won&#8217;t require them, so they can be omitted. Look [here][2] for further detail. Also, some servers may prefer NFS, NTFS or SMB, so read up on their native file system.

now, to mount the share type:

```
$ sudo mount -a
```

and your share should be visible in the file manager.

Now, go forth and add some libraries to your PMS and watch away!

 [1]: http://en.wikipedia.org/wiki/Star_Wars "Star Wars"
 [2]: https://wiki.ubuntu.com/MountWindowsSharesPermanently
