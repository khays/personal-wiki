---
layout: post
title: VimOutliner
tags: vim outlines documents unix
---

A great tool to create an outline in Vim, works similar to the word version, just much faster because it is with Vim.

## File types

Current, VimOutliner will be used on any file type with the `otl` extention, you can add others if you would like

    vim $HOME/.vim/ftdetect/vo_base.vim

And add `au! BufRead,BufNewFile *.emdl   setfiletype vo_base` or whatever filetype to a line that looks fairly similar to that.

## Known Issues

If you have a leading with a hash `#`, it doesn't work, I susspect that this is because of the markdown plugin that I have installed.

## Commands

* `,,1`, `,,2` show only the different levels
* `zc`, `zo` will fold a tree of itmes into one, `zO` will expand everything below
* `,,-` adds a number of dashes across the screen
* `,,cb` and `,,cx` makes items an empty checkbox and a checked checkbox
* If you want to put text that is not part of the outline (like body text), put a `:` at the begining of the line, while in the insert mode
