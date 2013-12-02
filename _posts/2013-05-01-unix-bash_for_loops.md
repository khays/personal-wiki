---
layout: post
title: Bash for loops
tags: unix bash loops commandline
---

Bash for loops are great ways to make your life easier.

## Useful commands

Truncate after 7 characters `filename=${files:0:7}`

Remove whitespace from dir 

    for f in *; do mv "$f" `echo $f | tr ' ' '_'`; done

## Change the extension of all files in directory

    for files in *.html;
      do
        mv "$files" "${files%.html}.txt"
      done

I think this calls all the files with an `.html` and saves them to files, than you can call `$files`. The `mv` command to looks like it is taking the variable, search

## Get the mtime for files in directory

This one is pretty cool, at least I thought so. You print out the `ctime` for all files in a dir by using
	
	for files in *.md; do eval $(stat -s $files);echo $st_ctime;done

And I needed to move all the files so that they started with the date and had their name in place.

	for files in *.md; 
		do 
			eval $(stat -s $files);
			mv $files $(date -r $st_ctime ‘+%Y-%m-%d-‘)$files;
		done

When you throw `stat` into an `eval` you will get a whole host of different options, including `st_dev`, `st_ino`, `st_mode`, and so on, check it out.

## A loop to convert files with pandoc

I needed to convert all the files in certain directory to a pdf. Using my bash function pandoc-clean (which calls pandoc with a few added parameters, such as a specific template) exported a pdf of all the files in a directory

	for files in *
		do eval $(pandoc-clean $files --toc -o $files.pdf)
		echo $files 'has been converted to a pdf'
	done

## Brace Expansion

What is interesting is [Brace Expansion](http://www.thegeekstuff.com/2010/06/bash-shell-brace-expansion/), read up on it to find out what exactly this does.
