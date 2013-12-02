---
layout: post
title: Vim Tips
tags: vim unix tips ftp md
---

I love Vim, I try to find an excuse to use it as much as possible. Here are a few tricks I have learnt along the way.

## Duplicate tab

Like in Firefox or Chrome, you can open the current file in a new tab by going

    :tab split

I use Tabs all the time

## Using vim as an FTP client

The way to make this work is to keep it simple, just use ftp (not sftp) and the command looks like this

    :e ftp://username@host/

This seems to work the best,

* Don't put the location in the there, like `/home/public_html/` as the ftp will set you to a default dir
* You shouldn't need a port

With *netrw* Vim will allow you to navigate directories.

## Word count

There are two ways that you can do this, these include

* if you press `g CTRL-G`, vim will provide you with a number of stats on the file, one of which is the word count
* use an external program to do it for you `:wc %`

## Spelling

If you use Vim to edit markdown files, you should enable spellchecking when you load a file. This works in gVim and terminal Vim, but you need to have syntax hightlighting turned on.

    autocmd BufNewFile,BufRead *.md set spell

* `]s` will navigate to the next spelling error
* `[s` will navigate to the last spelling errot
* `z=` will proivde a list of suggestions

Take a look at `:help spell` to see all that you can do. As I just found out, this offers a lot of function, something one might nowt always expect from Vim.

## Human readable json

To make a minified json file easy to read, simply open the file in vim and run the command `:%!python -m json.tool`. 

[Looks like](http://stackoverflow.com/a/1920585/1325168) you need python 2.6 installed. [Read about it on](http://blog.realnitro.be/2010/12/20/format-json-in-vim-using-pythons-jsontool-module/)
