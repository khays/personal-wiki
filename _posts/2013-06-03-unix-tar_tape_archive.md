---
layout: post
title: Using Tape Archive - tar
tags: tar archive unix zip
---

## To Compress:
 
    tar -pczvf desitination.tar.gz unCompressedFolder
 
where 

 * z, --gizp, --ungzip: Filters the archive though gzip
 * c, --create: create a new archive
 * f, --file: use archive file
 * v, --verbouse: show files as they are being processed
 * p: this will preserve the permissions
 
It appears that the `p` needs to be first for some reason, otherwise it will fail, and create a tar with the name of p.

## Zip directory to a sub directory

In the case where you don't want to zip up a whole file in a directory (if you were extracting the file to MYRA's test or prod web env where you don't have access to anything by html), you would do this

tar -pczf ../destination.tar.gz .
