---
layout: post
title: Common location for Apache settings
tags: apache mac unix settings
---

## On the iMac

All the settings can be found in:
		
		/etc/apache2/httpd.conf

Virtual host settings are stored in
		
		/private/etc/apache2/extra/httpd-vhosts.conf
		
To restart apache, `sudo apachectl restart`
