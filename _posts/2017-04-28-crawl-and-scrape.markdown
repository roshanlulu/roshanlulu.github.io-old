---
layout: post
title:  "Python - I Crawl and Srape!"
<!--date:   2017-03-25 21:02:35 +0000-->
date:   2017-04-28 10:30:35 +0000
categories: data science, scrapy
---

#### A. Preface
As a part of my Data science capstone project, I had to get data from website links. I started my search and found numerous ways to scrape data of the web. I found Beautiful soup and scrapy to scrape data of a website. Thanks to the open source community and documentation, the web has enough information, all i had to do was to adapt it to what I wanted.

The next concern to address was how to scrape data from around 5000 web pages! That is when I came across spiders. And Scrapy spider was what I found. The data was scattered across the web, but this particular article on github did help me.

Credits: 
- `https://github.com/scrapy/quotesbot`

Bot I created to crawl and scrape:
- `https://github.com/roshanlulu/bots`

#### B. Step by step guide on how to create a bot for yourself.

##### 1. Create the bot/spider framework in just one line !!! Its that simple !
- TODO: `Run from the command line: scrapy startproject <projname>`
- NOTES: A set of project files/folders will be created in that location.
    - scrapy.cfg: the project configuration file
    - <projname>/: the project’s python module, you’ll later import your code from here.
    - <projname>/items.py: the project’s items file.
    - <projname>/pipelines.py: the project’s pipelines file.
    - <projname>/settings.py: the project’s settings file.
    - <projname>/spiders/: a directory where you’ll later put your spiders.
- project path created - 

####3 2. Update settings file
- TODO: `Add this line to settings.py file 'DOWNLOAD_HANDLERS = {'s3': None,}'`
- NOTES: I am yet to check why we are doing this.

##### 3. Create the spider
- TODO: `Create your spider file Spiderfile.py inside the folder called spiders[from from step 1]`
- NOTES: Spider sounds fancy and complicated. But a spider is just another .py file.

##### 4 .Define the spider class
- TODO: `Add a spider class inside 'Spiderfile.py'` from Step 3
- Code/Pseudocode:
{% highlight python %}
# import libraries
import scrapy

class GiveAnyClassName(scrapy.Spider):
    # Naming ceremony of the spider
    name = 'thats_the_spiders_name'
    # Provide the list of urls that you want to parse through
    start_urls = [List of urls to parse through]
    # Define your parse function inside your class

    def parse(self, response):
       yield {
            response.xpath('//b/text()').extract()[0]:response.xpath('//td/font/text()').extract()[0],
            response.xpath('//b/text()').extract()[1]: response.xpath('//td/font/text()').extract()[1]
       }
        {% endhighlight %}

##### 5. To list out the spiders you have from command line
- TODO: `Run the command 'scrapy list'` from your bot path. If you can find your spider from step 4, Yaay!

##### 6. Command to kickstart your spider to start crawling
- TODO: Your spider is ready to crawl the web. 
    - Command to crawl using your spider and write output to command line
        - `scrapy crawl <spider-name>`
    - Command to crawl using your spider and write the output to a filename
        - `scrapy crawl <spider-name> -o <filename.json/.csv>`