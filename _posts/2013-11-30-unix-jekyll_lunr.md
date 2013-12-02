---
title: Seaching with Jekyll
layout: post
tags: jekyll lunr javascript
---
I really like Jekyll, not because I know ruby (because I don't) but Jekyll just seems to offer an elegant way to dispaly blog posts, super fast. And...there is a healthy group of great people working with it and improving.

## lunr.js and Jekyll

It isn't hard to see why lunr.js is great, expecially with the non-database indexing and ability to integrate with Jekyll, it is very cool. I had a hard time setting it up, but it was because I didn't follow the directions exactly. Once I followed all 9 steps of [slashdotdash](https://github.com/slashdotdash/jekyll-lunr-js-search)'s method, I was good to go.

### Adding other items to index

I wanted website to index more than just the body of posts, this is what you have to do to add additional fields to the index:

1. Open `_plugins/ekyll_lunr_js_search.rb` and searching for `body`, wherever I saw it I added tags as well (see code examples below)
2. Open `js/jquery.lunr.search.js` and add `this.field('tags');` to the *LunrSearch.prototype.createIndex* function
3. Test the code and make sure it works

### Examples

It is a little hard to explain, 

* look for `SearchEntry.new(title, url, date, categories, body)` and add *tags*, like `SearchEntry.new(title, url, date, categories, body, tags)`
* Add the line `:tags => entry.tags` below the line `:body => entry.body` (don't forget to add a comma after the *entry.body* line
* Change `@title, @url, @date, @categories, @body = title, url, date, categories, body` to `@title, @url, @date, @categories, @body, @tags = title, url, date, categories, body, tags`

I guess you are really just looking for paterns, and adding in what you need (tags in this case). This worked for me.
