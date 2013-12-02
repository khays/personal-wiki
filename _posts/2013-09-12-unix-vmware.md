---
layout: post
title: VM Ware Notes
tags: vmware windows vm commandline
---

Running windows blows, running a vm with [vmware’s unity mode](http://pubs.vmware.com/workstation-10/index.jsp?topic=%2Fcom.vmware.ws.using.doc%2FGUID-8C477788-7700-4030-8C4A-039C02AABB74.html) sucks less, but it still sucks. Here are my lessons running a windows in VMware workstation on my Fedora host.

## Don't update the Kernel

If you are running Fedora and you update the Kernel, you will likely run into problems because VMware doesn't keep up with the Kernels. The easiest way around this is to avoid updating the Kernel... YA RIGHT.

The last working Kernel appears to be 3.10.10-200.fc19.x86_64

## Icons on the host with Unity

When you hit `alt-tab` it is nice to see the icons of the application that you are swtiching to. In VMware, I noticed that sometimes the icon of the application would show up (like outlook, word, etc) and other times the only thing that would show up would be the VMware with many windows under that one.

The trick is to launch the VMware workstation from the command line. For whatever reason when you do that and switch into unity mode, you will get the icons.

## Drives won't map in the VM

I had a weird thing happen where I couldn't get the drives to map while I was in the VM. It was giving me an error like, 'You have already logged into this server with a different username and you will have to log out first before you can map these drives'. I remember that I mounted the drives on my Linux machine earlier today and when I look under the network tab in windows explorer I see all the servers that I have access to. 

If you mount drive in linux, you don't have to worry about mounting them in the VM. Not sure if this was true or not..

## VMware won't boot a VM

I ran into this problem one day, and there was no reason for it. I would get these messages mentions that there was a problem with certain modules:

* vmmon
* vvmci

The issue was easy enough to remidy by running

    sudo modprobe vmmon
    sudo modprobe vmci

After doing this the VM would load, but I didn't have any network access, to fix this, I had to

    sudo modprobe vmnet
    sudo vmware-networks --start

Which seemed to work just fine, here is the oneline 

    sudo modprobe vmmon;sudo modprobe vmci;sudo modprobe vmnet;sudo vmware-networks --start
