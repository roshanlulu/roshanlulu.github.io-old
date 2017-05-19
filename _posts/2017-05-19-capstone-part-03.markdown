---
layout: post
title:  "Capstone Part 3"
date:   2017-05-19 07:19:35 +0000
categories: data science
---

## Progress Report - Capstone Part 03
*Project Summary of Aviation Accident Analysis*
### Submitted by Roshan Lulu
*https://roshanlulu.github.io/*
___
![](./assets/QantasLead.jpg)
___

<img src="./assets/Week7.png" alt="Drawing" style="width:60px" align="left"/>

# **<span>&nbsp;&nbsp;Throwback to Capstone part 02</span>**
___
> 
- Obtained primary dataset from `www.planecrashinfo.com`
- Peformed Data cleaning and Exploratory data analysis.
- During EDA, It was found that the dataset had quite a few missing values. As a result of which, a potential dataset needed to be taken into consideration for part 03

<img src="./assets/Week9.png" alt="Drawing" style="width:60px" align="left"/>

# **<span>&nbsp;&nbsp;Back to Week 9 - Capstone part 03</span>**
___

> ** I have divided this phase into 3 notebooks. Further ahead is the summary of all the notebooks **


## **`Notebook 1 - eda_aviationnet_db`**
___

- Imported dataset from the Aviation Safety Network Website: `https://aviation-safety.net/database/`
- Performed Initial Data cleaning/wrangling and EDA on the raw dataset.
- Examined the data - There are 37 features
- Check the null counts and remove nulls. This is a very important step for further EDA
- Check the datatypes and convert them where required.
- Clean each feature and perform Univariate data analysis: Use matplotlib/seaborn for plotting
- Feature Engineering: Grouping data into categories were required
- Feature Extraction: Extracting new features from the existing features
- Evaluate features required for this project
- Save the cleaned dataset to a csv file. This will be used as the dataset reference during the phase of this project.

> ### Summary of EDA
*Categorizing the features during Data munging was helpful to decide the useful features for the project. The features I have retained, extracted or dropped have been described below. *

> **Airline details: **
- ['LeasedFrom', 'OperatedBy', 'OperatingFor', 'Operator', 'OnBehalfOf']
- There were 5 columns that indicated the operator or the airline. Checking the null counts and description of these columns I decided to merge Operator and Operatingfor into 1 column and drop the other 3
- Distinct Operators 2748. This is a lot! But, at this stage I do not want to drop the operators with least counts. Because the crash locations might still be important. 
- I was interested in the operator with highest accidents.

>![operator](./gen_plots/operator.png)

>**Accident Details**
>
- 'Nature' - The nature of the flight. The categories were quite dispersed and I was able to group them logically and create lesser groups

>![FlightNature](./gen_plots/nature_of_flight.png)
- 'Type' - I had a look at the famous aircraft manufacturers to ensure that I did not move it to the Others category. All the manufacturers with less than 10 crashes hvebeen grouped as the Others category
The names had o be cleaned to remove the exact mdoel number as I am primarily interested in the manufacturer performance.

>![AircraftType](./gen_plots/AircraftType.png)
- 'FlightNumber' - It is kept as a unique ID
- 'CarrierNumber' - Dropped it!
- 'FirstFlight' - extracted the year that the particular aircraft mentioned was flown the first time.
    I have kept this as it would be a good indicator to calculate age of the airline at the time of the accident.
>![FirstFlight](./gen_plots/FirstFlight.png)
- 'Registration' - Dropped it!  
- 'Number' - Dropped it!
- 'Engines' - Split this feature into No of engines and Engine Count
![EngineType](./gen_plots/EngineType.png)

> **Fatalities**
- ['Crew','Passengers','CollisionCasualties','TotalFatalities','GroundCasualities'] 
- These features were converted to integer datatype and renamed. It is a good feature for visualizing and modelling at a later stage.
## ADD SOME HERE

> **Crash Details**
- 'CrashSiteElevation' - This provides the elevation at which crashes occured. I have cleaned the feature and retained it.
- 'Phase' - The phase during which the accident occured is mentioned here. It is quite an interesting aspect.
![AccidentByPhase](./gen_plots/AccidentByPhase.png)
- 'TotalAirFrameHrs','Duration' - Drop it
- 'Date' - Split into Day, Date, Month, year
## Regenerate YearCountCloud
- 'Narrative' - Kept to be analysed later
- 'DepartureAirport' - I have not decided what to do with this column. But Ill keep it
- 'DestinationAirport'- I have not decided what to do with this column. But Ill keep it
- 'AirplaneDamage' - Describes the damage to the airplane after the incident.
- 'AirplaneFate' - Described the fate of the airplane after the accident
![AircraftDamage](./gen_plots/AircraftDamageCount.png)
## PlotDamage vs Fate
- 'Time' - Time of the accident
- 'Cycles' - Drop it
- 'Location' - Accident Location. Extracted it into Sublocation(Exact Location) and Location(Country names)

> **Investigation Results** 
- I am not sure if this category is useful. But I'll keep the features with more valid values values. It can be dropped later if it is not used.
- 'InvestigatingAgency' - Keep it
- 'Status' - Kept it
- 'Released' - Drop it
- 'DownloadReport' - Drop it
- 'Issued' - Drop it
- 'DurationOfInvestigation' - Keep it

> ** Latitude Longitude Extraction**
- Now that we have the location in terms of country, an important feature to extract is the Latitude Longitude information.
- The Google Geocode Api was used to extract Latitude Longitudes from the Locations. This is also a very important feature for the analysis.
- This portion will only be run once to get the latlong values. After that only the saved file will be used. APIs are not meant to be called everytime a notebook is run.

## Add Graphs


```python
data_dict = {
    'Operator' : 'The operator of the crashed flight. There are around 2748 unique values'
    'Nature_Code': 'Nature of flight,
    'Type': 'Aircraft Manufacturer',
    'FlightNumber' : 'Unique Identification Number',
    'Engine_count' :
    'Engine_Type' :
    
    
}

```

## **` Notebook 2 - data_map_viz`**
> 
- In the previous notebook I was able to use matplotlib and seaborn for the univariate and bivariate analysis.
- Further, Since the data is distributed across the world, I am interested in getting a world view of the incidents.
- I was able to use two plottong techniques: **Plot.ly and Folium**. These are open source map plot libraries. I would definitely be exploring more of this for the next phase. 

> ![mapit_country](./gen_plots/map_plot_heat.png "Title")

## **`Notebook 3 - text_analytics_modelling`**
- The accident narrative in the dataset was quite informative. In order to be able to use it efficiently, I decided to use Natural Language Processing on it.
- Along with analysing the patterns in accidents based on different features, I thought it would be interesting to classify the incidents based on the narrative.


> 
**Text Pre-Processing - Noise Removal**
>
- Text is one of the most unstructured forms of data and Noise removal is a very important step before any data can be analysed. So is the case for text.
> 
- Noise is information that either corrupts your data or is not useful. Below are some of the common forms of noise in text and that I will be employing going ahead:
    1. Stop words are the most commonly used words in a language. i.e the words that do not convey meaniful information if on its own. eg: The, A, An, Is, for etc
    2. Punctuations also do not convey any information from an analytics point of view. Hence, it can also be considered as Noise.
>
*Noise(text) = Stopwords(text language) + Punctuation(text)*

> 
**Text Normalisation**
> 
- Normalisation of data is converting different forms of the same word into a common one. Two of the commonly used forms are :
    - 1. Stemming i.e. stripping the suffixes (“ing”, “ly”, “es”, “s” etc) from a word.
        - I tried using Stemming for my text, but it stripped the word of all its meaning, hence currently I am not using stemming. 
    - 2. Lemmatization i.e. an organised and step by step procedure of obtaining the root form of the word, it makes use of vocabulary and word structure and grammar relations.
        - Lemmatization, did not help me much. For now, I am not using these functions. But at a later point I will come back to it if required.
> 
**Feature Extraction**
- Count Vectorizer is used to get the most commonly used vocabulary. Count vectorizer is one of the basic techniques when dealing with textual content. It is the process of getting a word count of the text/document. The parameters of a count vectorizer can be modified depending on the problem at hand.

> ![frequentwords](./gen_plots/wordcount.png)
> 
**Unsupervised Topic Modelling using LDA (Latent Dirichlet Allocation)**
> 
- I am interested to divide the topics based on the cause of accidents. Hence Clustering them based on the description is the next task. There are many approaches for obtaining topics from a text. 
    - Latent Dirichlet Allocation is the most popular topic modeling technique and I am planning to try that first.
> 
**Cleaning and Preprocessing**
> 
- Cleaning is an important step before any text mining task. Since this has already been done above. we wont be looking at it.
> 
**Preparing Document-Term(DT) Matrix**
> 
- All the text documents combined is known as the **corpus**. To run any mathematical model on text corpus, it is a good practice to convert it into a matrix representation. LDA model looks for repeating term patterns in the DT matrix.
> 
**Running LDA Model**
> 
- Next step is to create an object for LDA model. The dataset does not have enough information to divide it into train and test sets. To begin, I will be using the LDA model to come up with similar words to create topics for the incidents. This can also be seen as feature engineering using the model. I expect to see some interesting results with this model.

## **Summary** - TBD
> 
The topic modelling results are not very convincing. It requires more iterations before it can come up with meaningful distributions. Few of the options I am planning to try are:
> 
- I think the stop words list needs to be expanded such that relevant words are picked by LDA model.
- I have seen that Topic extraction with Non-negative Matrix Factorization is an alternate method for LDA. I would like to try that and see its results too.
- SVM is supposedly a good way to check the accuracy of the LDA results. But the challenge is that the results cannot be compared to any training set. 
- If the topic results from modelling seem convincing enough, I will go ahead and use them. The idea is to add the extracted topics as a feature into the dataset. With this as a new feature, it would be an extra addition to analyzing the aviation accidents.

# Next Steps

- 


## Describe successes, setbacks, & lessons learned along the way. _ TBD!




```python

```
