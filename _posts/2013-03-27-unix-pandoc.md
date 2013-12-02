---
layout: post
title: Pandoc settings
tags: pandoc latex pdf document automation unix documents
---
What I have to install to get pandoc working the way I want it to.

## Install

I was able to install and configure templates by

1. Installing cabal (I think it is a script, search for it)
2. Running `cabal install pandoc`
3. Install latex, see the script on the internet
4. Install the required latex packages

### Required latex packages

These were installed with yum on Fedora 19. If you are using an older version you might want to read the [fedora TeXLive page](http://fedoraproject.org/wiki/Features/TeXLive)

* texlive
* texlive-luatex
* texlive-oberdiek
* texlive-luatexbase
* texlive-lualibs
* texlive-luaotfload
* texlive-xetex
* tex-euenc
* texlive-lastpage
* texlive-titlesec

Install the fonts and make sure that you have the correct images and directories and you should be ready to go.

## Templates

On my **work machine (Fedora)**, the template files are located in: `~/.cabal/share/pandoc-1.10.1/data/templates/clean-modern.tex`

On my **home machine (Mac)**, the template files are located in: `/usr/local/share/pandoc-1.10.1/data/templates`
