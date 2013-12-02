---
layout: post
title: Printing with Cups
tags: printing unix cups
---

Printing with Cups can be easy. Assumes that you have CUPS installed and the daemon is running, how to setup the printer at work.

1. Log into the CUPS web interface: http://localhost:631
2. Use the system's root username and password
3. Click *Add Printers and Classes*
4. Click *Add Printer*
5. Select the printer you would like to add. The system seems to know about the networked printers, so you just have to select them.
6. use the CUPS driver supplied by Xerox.
7. Change the settings so that the printer has two extra trays
8. Set the *Paper Source* to tray 3 and *Media Size* to letter
