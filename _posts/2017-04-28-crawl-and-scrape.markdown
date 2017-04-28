---
layout: post
title:  "Python - I Crawl and Srape!"
date:   2017-04-28 10:30:35 +0000
categories: data science, scrapy
---

I had to use crawl a large number of websites to scrape data for my capstone project during my Data Science Immersive course.

Here is the link to my bot:
`https://github.com/roshanlulu/bots`

While researching different ways to crawl the web

#### Create the framework in just one line !!! Its that simple !
    The magic line: 
    `scrapy startproject <projname>`

    input - Run the magic line from the command line
    expected output - A set of project files/folders are created in that location.

        scrapy.cfg: the project configuration file
        <projname>/: the project’s python module, you’ll later import your code from here.
        <projname>/items.py: the project’s items file.
        <projname>/pipelines.py: the project’s pipelines file.
        <projname>/settings.py: the project’s settings file.
        <projname>/spiders/: a directory where you’ll later put your spiders.

#### Add this to settings.py file
    `DOWNLOAD_HANDLERS = {'s3': None,}`
        I am yet to check why we are doing this.

#### Create the scrapy python file
Create your spider file inside the folder called `spider' that was created using the magic line

#### Create your spider class
{% highlight python %}
import scrapy

#### Define the spider class
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

#### To list out the spiders you have from command line
`scrapy list`


#### Command to kickstart your spider to start crawling
    `scrapy crawl <spider-name>
    `scrapy crawl <spider-name> -o <filename>