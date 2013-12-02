---
layout: post
title: Reading Apache Logs
tags: hmtl logs apache
---

## lnav

[lnav](http://lnav.org/) is an application that parses log files. Super powerful because you can run whatever query on it you would like on the log using SQL format. 

Here is how you would show all ip addresses that called a `GET` request, ordered by the size of the request in MB:

	SELECT c_ip, sum(sc_bytes)/1000000 AS total from access_log WHERE cs_method LIKE '%GET%' GROUP BY c_ip ORDER BY total DESC;
	
Show the total MB

	SELECT c_ip, sum(sc_bytes)/1000000 AS total, cs_uri_stem FROM access_log GROUP BY cs_uri_stem ORDER BY total DESC;
	
Show all files that were requested, number of times requested, file size and total requested size.

	SELECT cs_uri_stem, count(cs_uri_stem) AS '# of requests', sc_bytes/1000000 AS 'File Size MB', sum(sc_bytes) AS total from access_log WHERE cs_method LIKE '%GET%' GROUP BY c_ip ORDER BY total DESC;
	
Show which IP address accessed which file how many time and how much bandwidth they used, *useful when local site is using all the bandwidth*

	SELECT cs_uri_stem, c_ip, count(c_ip), sum(sc_bytes) FROM access_log GROUP BY cs_uri_stem ORDER BY sum(sc_bytes) DESC

## goaccess

Works as well, but I don't like it as much as lnav.
