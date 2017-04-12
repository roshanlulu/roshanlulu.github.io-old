---
layout: post
title:  "Capstone Part 1"
date:   2017-04-12 21:02:35 +0000
categories: jekyll update
---
### About

My Capstone project is an analysis of accidents in the aviation industry. Of the incidents reported over the last few decades, I am looking for patterns and correlations in the data.

### Goal and Success Criteria
Most of the recorded accidents have obvious recorded parameters like the Airline, Aircraft, Flight route, Incident location, Date. 
Is there any parameter that stands out from the others in terms of numbers. 
It could be an airline in an international/domestic sector that does not follow maintenence strictly.
It could be a certain aircraft model from a particular manufacturer. 
I have heard more than one incident of flight crashing into the mountains/hills. 
If it is a common reason then why is it so? Is it that pilots dont have enough knowledge flying in such conditions? 
The questions that can be posed are numerous wrt this topic.
 
I may not be able to answer all the questions at this point. But analysing the data is definitely a good place to start. 

### Potential Audience
If there is a pattern found, then it would be of equal interest to the stakeholders involved in the industry as well as the customers i.e. travellers like us.

Insurance companies can use this information to charge more for flights with a higher risk.

Pilot training schools could use it to perform indepth case studies

With the increased connectivity around the world, ppeople are travelling all around the world and out of their comfort zones. Wouldnt it be helpful to know how safe it is to fly to a non-native region?

Aircraft manufacturers could use information to think of ways to prevent related incidents in the future.

### Dataset

There are numerous datasets available in the internet for this topic. However, I was able to get a collection of the database in html format from [Plane Crash Info][plane-crash-info-db] website. The author of the website has done a great job in compiling the data from almost the past century.

In order for me to use the database, my first task is to convert the html files into a csv format in order to start with analysis. My first idea was to either use [web scraping or crawling][Introduction to crawling] to extract the html data.I was able to understand certain [Best Practices][Crawling-BestPractices] on web crawling.

This is when i came across 2 new words - Scrapy and Beautiful Soup.

References found on Scrapy:
Scrapy - `pip install scrapy`
[Scrapy HW][Scrapy github] : This is an opensource code in python using scrapy, that can crawl a webpage and give desired output. Using the github code, I did a test to extract one data sample. The output was in a dictionary format.
Further i have to extend scrapy to run through all the webpages with the data samples and compile lal the dictionary data into a loadable dataset in csv format.

References found on Beautiful soup - `pip install bs4`
[Crawl with BS4][Beautiful Soup 4]
[BS4 Notebook][BS4 Notebook]


[Crawling-BestPractices]:https://www.import.io/post/how-to-crawl-a-website-the-right-way/
[Introduction to crawling]:http://www-rohan.sdsu.edu/~gawron/python_for_ss/course_core/book_draft/web/web_intro.html
[Beautiful Soup 4]:http://www.pythonforbeginners.com/beautifulsoup/beautifulsoup-4-python
[BS4 Notebook]:http://web.stanford.edu/~zlotnick/TextAsData/Web_Scraping_with_Beautiful_Soup.html
[Scrapy github]:https://github.com/scrapy/quotesbot
[plane-crash-info-db]:http://www.planecrashinfo.com/database.htm