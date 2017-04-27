---
layout: post
title:  "Python - I Crawl and Srape!"
date:   2017-04-28 07:14:00 +0000
categories: data science, scrapy
---



1. `scrapy startproject craigslist`
- input - command line from folder path - `scrapy startproject <projname>`
- expected output - A set of project files

scrapy.cfg: the project configuration file
<projname>/: the project’s python module, you’ll later import your code from here.
<projname>/items.py: the project’s items file.
<projname>/pipelines.py: the project’s pipelines file.
<projname>/settings.py: the project’s settings file.
<projname>/spiders/: a directory where you’ll later put your spiders.

2. Add this to settings.py file.
`DOWNLOAD_HANDLERS = {'s3': None,}`

3. Create the scrapy python file

4. Create your scrape class. 
    Name your spider!
    Write the code for your url and parse/scrape.

5. `scrapy list` gives yout the list of spiders. your spider should have that name

6. `scrapy crawl <spider-name>
    `scrapy crawl <spider-name> -o <filename>