---
layout: post
title: Serving Tracks with Apache via Passenger
tags: gtd tracks apache unix passenger ruby
---

[Tracks](http://getontracks.org/) is a great GTD web based tool. I [ no longer](http://pm2.be/tools/Task-management/) use this tool, but this is a great tool. Originally I had the default setup, using [WEBrick](http://www.ruby-doc.org/stdlib-2.0/libdoc/webrick/rdoc/WEBrick.html) serving the content, but when my host starting to give me errors, I moved to [passenger](https://www.phusionpassenger.com/) to serve the content via Apache.

## Starting Tracks, the old fashion way

Go to the direcotry that holds the tracks file, on the liquid host, that is `/var/www/tracks`. Once there, run:

		bundle exec script/server -e production -d

## Starting Tracks, with apache

If you read the docs on github they say that you should use apache for tracks if you have a lot of people visiting the site. I thought I would give it a go and see if that worked. In order to make that work, I used a *gem* called [Passenger](https://www.phusionpassenger.com/download). Passenger worked fine:

1. Download the gem
2. Run the script
3. Change the setting as the say what they say in the install wizard
4. Restart apache and it just works...it took a while, but it eventually work.

### Apache config

This is what I put into the my `/etc/httpd/conf/httpd.conf`

		<VirtualHost *:80>
			ServerName utils.pm2.be
			# !!! Be sure to point DocumentRoot to 'public'!
			DocumentRoot /var/www/tracks/public/
			<Directory /var/www/tracks/public/>
				 # This relaxes Apache security settings.
				 AllowOverride all
				 # MultiViews must be turned off.
				 Options -MultiViews
			</Directory>
		</VirtualHost>

And it worked.	
