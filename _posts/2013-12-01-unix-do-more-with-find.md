---
layout: post
title: Do more with Find
tags: unix commandline find
---

Find is an easy way to search for a file and with its ability to navigate directories and call other commands, this is a great tool.

## Change all files of search criteria

I have searched a couple of time for this one, this is how you do it

		find . -type f -print0 | xargs -0 -n 1 sed -i -e 's/twentytwelve/twentythirty/g'

But for some reason that creates a new copy of the files (`file_name.php-e`), so to remove those, do

		find . -name '*-e' -exec rm -f {} \;
		
Maybe it is the version of OSX I am running, or some other reason, just another step to do.
