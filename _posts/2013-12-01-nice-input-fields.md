---
layout: post
title: Nicer html input boxes
tags: html input textbox
---
I really like having my input forms look nicer then the default the operating system provides, so I have created the ones that look a bit better.

### The code

This will produce a nice looking input forms with a little illusion of depth. The shadow isn't too strong, so it isn't really that noticable, but it does look pretty nice:

	input, textarea{
		border-width: 1px;
		border-style: solid;
		border-color: #AAA #DEDEDE #DEDEDE #BBB;
		box-shadow: 2px 2px 13px rgba(0, 0, 0, .081) inset;
		padding: 7px 5px 5px;
	}

## Other useful info

If you want select a button, you need to use a selector like `input["type=submit"]`. In order to make this work you must have the right doctype set at the top of the document: `<!DOCTYPE HTML PUBLIC ...`
