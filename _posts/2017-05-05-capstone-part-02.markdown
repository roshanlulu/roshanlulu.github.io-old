---
layout: post
title:  "Capstone Part 2"
date:   2017-05-05 07:19:35 +0000
categories: data science
---
### A quick introduction to my project aim and dataset.

The aim of this project is to analyse performance of various airlines. I have an aviation accident database covering incidents from the lasts few decades. All civil and commercial aviation accidents of scheduled and non-scheduled passenger airliners worldwide, which resulted in a fatality.

These are the initial goals I planned to acheive:

- Is there a preferred airline?
- Is there any aircraft that is highly reliable or unreliable?
- Are there flight routes that require extra attention?
- Which was the time period with more accidents?
- Come up with an estimation of what can be considered as a safe flight.

### Are there any risks or assumptions?
 
Accidents are never trivial, but considering the frequency of aviation accidents, a potential risk I foresee is the less number of data points/features to apply the various machine learning models that I have learnt during the data science course. The potential datasets are added to cover this case.

### How did I get the Dataset? What are the Potential Datasets?

- Dataset
- http://www.planecrashinfo.com/database.htm
    - This dataset was in Unstructured format and datapoints were available in different html pages.
    - The challenge here was to scrap the data.
    - A scrapy bot was used to scrap the data and convert it into csv format. (Refer: ../Capstone_Roshan/bots)  
    https://roshanlulu.github.io/data/science,/scrapy/2017/04/28/crawl-and-scrape.html
 

- Potential Datasets:
- https://www.kaggle.com/usdot/flight-delays
    - This dataset has information about the on-time arrival/delay information of domestic flights operated by large air carriers in USA.
    - Why this? It is a good dataset for measuring the airline performance model and applying the machine learning models.

- https://aviation-safety.net/database/
    - Aviation Safety also provides similar information as plane crash info in a different structure
    - Data is in unstructured format, hence needs to be scrapped from the website.
    
### Further Evaluation
- Proposed Methods and Models
    - Machine learning algorithms such as KNN Classifiers etc would be were I would like to go next. In case of a prediction model, I would like to use the regression models.

- Tuning Metrics and Evaluation Approaches
    - I am interested in applying the basic confidence intervals and k-tests for further investigation.

### Usage of Google APIs

I will be using google maps api to get the Latitude and Longitude for the Location information.
Below code will be run once to save the data into csv file for location.
It is an iterative process since at 1st run, google api returns a maximum of only 2500 calls in 24 hours.
Plus, out of the 2500 calls, there may be around 10-20% of Api timeout error.
The list is a growing list.
Aim of this part: The plan is to use this Latitude and Longitude information to plot on the map.

{% highlight python %}
from geopy.geocoders import GoogleV3
from geotext import GeoText
from geopy.exc import GeocoderTimedOut
import time

geolocator = GoogleV3(api_key="apikey")
geoloc_default = geolocator.reverse("0, 0")

crash_loc = pd.DataFrame()
crash_loc['Location'] = crashes['Location']
crash_loc['latlon'] = ''
crash_loc['place'] = ''
crash_loc.head()

start = 11
stop = 2500
for index in range(start,stop):
    print(index)
    try:
        place,(lat,lon) = geolocator.geocode(crash_loc.ix[index, 'Location'])
        crash_loc.set_value(index, 'latlon', (lat,lon))
        crash_loc.set_value(index, 'place', place)  
    except Exception as e:
        print('error', item, e)

# Write save it to a csv file
saveit.to_csv('./crashes_geolocation.csv', index = False)

import sqlite3import pandas as pd
import sqlite3

geoloc = pd.read_csv('../datasets/crashes_geolocation.csv')sqlite_db = '../database/crashes_geolocation.sqlite'
conn = sqlite3.connect(sqlite_db) 
c = conn.cursor()

geoloc.to_sql('crashes_geo',     # Name of the table
            con=conn,                    # The handle to the file that is setup
            if_exists='replace',         # Overwrite, append, or fail
            index=False)                 # Add index as column

c.close()
        {% endhighlight %}

### Summary of Topics that I was able to learn and apply during this phase of the project
- Data Cleaning Techniques
- Data Munging Techniques
- Perform EDA
- Summarize EDA
- Usage of Google APIs
- Pandas to SQL DB connection
- Improve python skills