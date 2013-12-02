---
layout: post
title: Character Encoding
tags: html utf8 unix documents
---

## Converting from word

When you copy things from word into a text based format, sometime you gather entities such as right quotes, or .... To get around this, you can use a utility called **recode**.

    recode utf8..html < original-file > output-file

And it works great, it will make all of these anoying files converted into the right html structure (&amp; or &rquo;).
