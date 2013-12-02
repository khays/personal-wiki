---
layout: post
title: Connecting to my home mac via ssh
tags: ssh mac firewall
---

Connecting to my home computer was fairly simple. Telus doesn't allow you to access your machine through the traditional port of 22, so you have to:

1. Change the port that you ssh into
2. Add a port forwarding in your router
3. Connect from the outside

## Change the port for sshd on OSX

The easiest way to do this is to 

* Create a new service in the `/etc/services` file. Search for `ssh` and add another service that makes sense.
* Make changes to the two lines of the ports that you would like to use.
* Make the changes to the `/System/Library/LaunchDaemons/ssh.plist` file and change the `<string>ssh</string>` to `<string>sssh</string>`
* Restart the daemon by running
	* `sudo launchctl unload /System/Library/LaunchDaemons/ssh.plist`
	* `sudo launchctl load /System/Library/LaunchDaemons/ssh.plist`
* Test it out, `ssh username@ipaddress -p newportnumber`

## Add a port forwarding in your router

This was actually very easy,

* Log into the utility that manages the router
* Go to port forwarding: firewall -> Port Forwarding
* Add in the starting port and end port the same as the number mentioned above (`newportnumber`)
* Click apply

The utility only seems to let you choose certain ports, so make sure that you pick on that works for you. I used a VNC port and that worked.

## Connect from the outside

* Find out what you ipaddress is, you will have to use an external website for this one
* From the outside, log in `ssh username@ipaddress -p newportnumber
