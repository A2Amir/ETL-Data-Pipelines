## Data Pipelines: 

Data pipeline is a generic term for moving data from one place to another. For example, it could be moving data from one server to another server.

An [ETL pipeline](https://en.wikipedia.org/wiki/Extract,_transform,_load) is a specific kind of data pipeline and very common. ETL stands for Extract, Transform, Load. Before cloud computing, businesses stored their data on large, expensive, private servers. Running queries on large data sets, like raw web log data, could be expensive both economically and in terms of time. But data analysts might need to query a database multiple times even in the same day; hence, pre-aggregating the data with an ETL pipeline makes sense.


## Introduction

Throughout this Repo I am going to use data from the World Bank Website to create a data pipline that can do the steps explained below in one step.:

1.	Extract data from different sources such as:
    *	csv files
    *	json files
    *	APIs
2.	Transform data
    *	combining data from different sources
    *	data cleaning
    *	data types
    *	parsing dates
    *	file encodings
    *	missing data
    *	duplicate data
    *	dummy variables
    *	remove outliers
    *	scaling features
    *	engineering features
3.	Load
    *	send the transformed data to a database
4.	ETL Pipeline
    *	code an ETL pipeline
    
**The data from the World Bank comes from two sources:**

1.	[World Bank Indicator Data](https://data.worldbank.org/indicator) - This data contains socio-economic indicators (statistics) for countries around the world. A few example indicators include population, arable land, and central government debt.

2.	[World Bank Project Data](https://datacatalog.worldbank.org/dataset/world-bank-projects-operations) - This data set contains information about World Bank project lending since 1947.

Both of these data sets are available in different formats including as a csv file, json, or xml. You can download the csv directly or you can use the World Bank APIs to extract data from the World Bank's servers.

The end goal is to clean these data sets and bring them together into one table so that we'll have an ETL pipeline to extract, transform, and load this data into a new database.

* **If you don’t have experience manipulating data with the Pandas library, check [this Repo](https://github.com/A2Amir/Introduction-To-Numpy-and-Pandas), or these resources [10 minute Intro to Pandas](https://pandas.pydata.org/pandas-docs/stable/10min.html),  [Pandas Basic Functionality](https://pandas.pydata.org/pandas-docs/stable/basics.html) to get you familiar.**

## 1. Extract data from different sources:
The first step in an ETL pipeline is extraction. Data comes in all types of different formats, and you'll practice extracting data from csv files, JSON files, XML files, SQL databases, and the web.

### CSV files

CSV stands for comma-separated values. These types of files separate values with a comma, and each entry is on a separate line. Oftentimes, the first entry will contain variable names. Here is an example of what CSV data looks like. This is an abbreviated version of the first two lines in the World Bank projects data csv file.

     id,regionname,countryname,prodline,lendinginstr
     P162228,Other,World;World,RE,Investment Project Financing

* **Take a look at [this Jupyter notebook](https://github.com/A2Amir/ETL-Data-Pipelines/blob/master/codes/1_csv.ipynb) to familiarize yourself with reading csv files.**

### JSON
JSON is a file format with **key/value** pairs. It looks like a Python dictionary. The exact same CSV file represented above could look like this in JSON:

      [{"id":"P162228","regionname":"Other","countryname":"World;World","prodline":"RE","lendinginstr":"Investment Project Financing"}]

Each line in the data is inside of a squiggly bracket {}. The variable names are the keys, and the variable values are the values. There are other ways to organize JSON data, but the general rule is that JSON is organized into **key/value** pairs. 

### XML
Another data format is called XML (Extensible Markup Language). XML is very similar to HTML at least in terms of formatting. The main difference between the two is that HTML has pre-defined tags that are standardized. In XML, tags can be tailored to the data set. Here is what this same data would look like as XML.

         <ENTRY>
           <ID>P162228</ID>
           <REGIONNAME>Other</REGIONNAME>
           <COUNTRYNAME>World;World</COUNTRYNAME>
           <PRODLINE>RE</PRODLINE>
           <LENDINGINSTR>Investment Project Financing</LENDINGINSTR>
         </ENTRY>

XML is falling out of favor especially because JSON tends to be easier to navigate; however, you still might come across XML data. From a data perspective, the process for handling HTML and XML data is essentially the same.

* **Check [this Jupyter notebook](https://github.com/A2Amir/ETL-Data-Pipelines/blob/master/codes/2_JSON_XML.ipynb) to familiarize yourself with reading JSON and XML files.**


### SQL databases
SQL databases store data in tables using [primary and foreign keys](https://docs.microsoft.com/en-us/sql/relational-databases/tables/primary-and-foreign-key-constraints?view=sql-server-2017). In a SQL database, the same data would look like this:

<p align="center">
  <img src="/imgs/2.PNG" alt="" width="400" height="150" >
 </p>
 
* **Take a look at [this Jupyter notebook](https://github.com/A2Amir/ETL-Data-Pipelines/blob/master/codes/3_sql.ipynb) to familiarize yourself with reading SQL databases.**

### APIs

Companies and organizations provide APIs so that programmers can access data in an official, safe way. APIs allow you to download, and sometimes even upload or modify, data from a web server without giving you direct access. APIs generally provide data in either JSON or XML format.
* **Take a look at [this Jupyter notebook](https://github.com/A2Amir/ETL-Data-Pipelines/blob/master/codes/4_API.ipynb) to familiarize yourself with reading from APIs.**


## 2.	Transform data

In surveys, data scientists have said that they spend 80% of their time transforming data.In this section I am going through each of these steps.

### combining data from different sources

In this [Jupyter notebook](https://github.com/A2Amir/ETL-Data-Pipelines/blob/master/codes/5_combining_data.ipynb) we will combine two data sets together into one pandas data frame. check it to get more familiar.

### Cleaning Data

Cleaning data is a big topic. Every data set might have its own issues whether that involves missing values, duplicated entries, data entry mistakes, etc. In this [Jupyter notebook](https://github.com/A2Amir/ETL-Data-Pipelines/blob/master/codes/6_cleaning_data.ipynb) , I'll do some data cleaning on the World Bank projects and World Bank indicators data sets. 

## Data Types

When reading in a data set, pandas will try to guess the data type of each column like float, integer, datettime, bool, etc. In Pandas, strings are called "object" dtypes. However, Pandas does not always get this right. That is an issue. Check this [Jupyter notebook](https://github.com/A2Amir/ETL-Data-Pipelines/blob/master/codes/7_datatypes.ipynb) for more infomation.

## Parsing Dates

Another common data transformation involves parsing dates. Parsing generally means that you start with a string and then transform that string into a different data type. In this case, that means taking a date in the format of a string and transforming the string into a date type. Check this [Jupyter notebook](https://github.com/A2Amir/ETL-Data-Pipelines/blob/master/codes/8_parsingdates.ipynb) for more infomation.

## Encodings

Encodings are a set of rules mapping string characters to their binary representations. Python supports dozens of different encoding as seen here in this [link](https://docs.python.org/3/library/codecs.html#standard-encodings). Because the web was originally in English, the first encoding rules mapped binary code to the English alphabet.

<p align="center">
  <img src="/imgs/3.PNG" alt="" width="250" height="250" >
 </p>
 
The English alphabet has only 26 letters. But other languages have many more characters including accents, tildes and umlauts. As time went on, more encodings were invented to deal with languages other than English. The utf-8 standard tries to provide a single encoding schema that can encompass all text.

The problem is that it's difficult to know what encoding rules were used to make a file unless somebody tells you. The most common encoding by far is utf-8. Pandas will assume that files are utf-8 when you read them in or write them out. but if Pandas dosent know the encoding of a file, can not read in. Check this [Jupyter notebook](https://github.com/A2Amir/ETL-Data-Pipelines/blob/master/codes/9_encodings.ipynb) for more infomation.

* There is a Python library that can be of some help when you don't know an encoding [chardet](https://pypi.org/project/chardet/). 

## Missing Data

A machine learning algorithm won't work with missing values. This is essentially correct; however, There are also implementations of some machine learning algorithms, such as [gradient boosting decision trees](https://xgboost.readthedocs.io/en/latest/) that can [handle missing values](https://github.com/dmlc/xgboost/issues/21). 

If you have missing data, you really only have two options, you can **delete data**, or you can **fill in the missing values**. 


* When I say **delete data**, I mean that deleting rows and columns that have more than %95 constantly missing values and deleting these rows and columns has no effect on the analysis.

* The process of **filling in missing values** is called **imputation**. A few ways to impute are using the mean or median or mode so that you don't have to delete entire rows or columns of data. Another common method especially for time series data is to use **Forward Fill** (values are pushed forward down to replace any empty values) or **Backward Fill** (Backward Fill does the opposite,values move up to fill in empty values). These technique really only work if the data is ordered by time. 

* Filling in missing values can be somewhat of an art and you'll need to test how different strategies affect the results of your Machine Learning models. 

Check this [Jupyter notebook](https://github.com/A2Amir/ETL-Data-Pipelines/blob/master/codes/10_imputations.ipynb) for more infomation.

## Duplicate Data

A data set might have duplicate data: in other words, A same record is represented multiple times. Sometimes, it's easy to find and eliminate duplicate data like when two records are exactly the same. At other times, duplicate data is hard to spot.Check this [Jupyter notebook]() for more infomation.

## Dummy Variables 

If you plan to use categorical variables with linear regression, oftentimes you should convert those variables into a set of numbers called dummy variables. The reasoning behind these transformations is that machine learning algorithms read in numbers not text. Text needs to be converted into numbers. You could assign a number to each category.  Check this [Jupyter notebook](https://github.com/A2Amir/ETL-Data-Pipelines/blob/master/codes/12_dummyvariables.ipynb) for more infomation.

## Outliers

An outlier is a data point that is far away from the rest of the data. Outliers can appear in your data for similar reasons to missing data. An outlier could be due to a data entry error or a processing mistake,  or an outlier might be legitimate data because, in any situation, there's always some probability of obtaining an extreme value. 

**The questions is how to find outliers what to do with them?**

* First I will introduce a few ways for detecting outliers:

  *  When working in one or two dimensions, you can use data visualizations to spot outliers. In the case of one dimensional data, you can plot the data along a number line and data point that falls far to the left or far to the right of most of the data could be considered an outlier. OR using two dimensional plots work the same.
         <p align="center">
           <img src="/imgs/5.PNG" alt="" width="500" height="150" >
          </p>
  * There are also statistical methods for finding outliers, These include using z-scores from a normal distribution or the tukey method.  Both of these methods use basic statistics like means, standard deviations, or quantiles to identify outliers that are far away from most of the data. 
  * To find outliers in three or more dimensions, we can use machine learning techniques like PCA to reduce the data to one or two dimensions then we could use the graphical or statistical methods. Another example would be to use a clustering method. In this case, you would first calculate the cluster centroids and then you would measure the distance between each centroid and each point. A large distance might indicate an outlier.
     <p align="center">
     <img src="/imgs/6.PNG" alt="" width="300" height="250" >
    </p>
  * Scikit-learn also includes various outlier detection algorithms, the links provided abelow. 
    * [Anomaly-Detection](https://github.com/A2Amir/Anomaly-Detection)
    * [scikit-learn novelty and outlier detection](http://scikit-learn.org/stable/modules/outlier_detection.html)
    * [statistical and machine learning methods for outlier detection](https://towardsdatascience.com/a-brief-overview-of-outlier-detection-techniques-1e0b2c19e561)
  * Check this [Jupyter notebook](https://github.com/A2Amir/ETL-Data-Pipelines/blob/master/codes/13_outliers.ipynb) for more infomation.

* By founding some outliers, what do you do with them:

   * If removing an outlier improves the model,then consider removing extreme isolated data points.
   * On the other hand, if removing an extreme value has no or little effect on your results, you can leave the point as is. 
   * Check this [Jupyter notebook](https://github.com/A2Amir/ETL-Data-Pipelines/blob/master/codes/14_outliers.ipynb) for more infomation.

## Scaling Data

Numerical data comes in all different distribution patterns and ranges. However, some machine learning algorithms work better when all of the features are within a similar numerical range.Changing the numerical range of data is called **Normalization or Feature Scaling**. Two common ways to scale features are called **Rescaling** and **Standardization**. 

* With **Rescaling**, you take your data and scale down the range, so that the minimum value is zero and the maximum value is one.

* With **Standardization**, you transform the data, so that it has a mean of zero and a standard deviation of one. 

**Notice:** the general shape of the distribution remains the same, which means the information contained in the data hasn't changed. Check this [Jupyter notebook](https://github.com/A2Amir/ETL-Data-Pipelines/blob/master/codes/15_scaling.ipynb) for more infomation.

## Feature Engineering

Creating new features is especially useful if your model is underfitting. If you  decide to engineer new features from your dataset, there are quite a few different ways to make new features including,
**creating categorical variables from numerical variables** , **multiplying features together**, **gathering more data**, **ratios**, **taking the sum or difference between features** or **taking the polynomial of a feature** . 

* A data engineer wouldn't necessarily decide what would be a good feature to engineer, That would be the job of a data scientist. 
* Check this [Jupyter notebook](https://github.com/A2Amir/ETL-Data-Pipelines/blob/master/codes/16_featureengineering.ipynb) for more infomation.

## 3.	Load
Now We've transformed the data, we'll want to store the data somewhere, otherwise we'd lose all your work. There are so many options for data storage. What we choose will depend on our needs. For example, with structured data, a relational database like SQL could be appropriate. If our data fits in a Pandas DataFrame, then a CSV file might work well. * Check this [Jupyter notebook]() for more infomation.
