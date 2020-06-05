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
    
The data from the World Bank comes from two sources:

1.	[World Bank Indicator Data](https://data.worldbank.org/indicator) - This data contains socio-economic indicators (statistics) for countries around the world. A few example indicators include population, arable land, and central government debt.

2.	[World Bank Project Data](https://datacatalog.worldbank.org/dataset/world-bank-projects-operations) - This data set contains information about World Bank project lending since 1947.

Both of these data sets are available in different formats including as a csv file, json, or xml. You can download the csv directly or you can use the World Bank APIs to extract data from the World Bank's servers.

The end goal is to clean these data sets and bring them together into one table so that we'll have an ETL pipeline to extract, transform, and load this data into a new database.

* **If you don’t have experience manipulating data with the Pandas library, check [this Repo](https://github.com/A2Amir/Introduction-To-Numpy-and-Pandas), or these resources [10 minute Intro to Pandas](https://pandas.pydata.org/pandas-docs/stable/10min.html),  [Pandas Basic Functionality](https://pandas.pydata.org/pandas-docs/stable/basics.html) to get you familiar.**

## Extract data from different sources:
The first step in an ETL pipeline is extraction. Data comes in all types of different formats, and you'll practice extracting data from csv files, JSON files, XML files, SQL databases, and the web.

### CSV files

CSV stands for comma-separated values. These types of files separate values with a comma, and each entry is on a separate line. Oftentimes, the first entry will contain variable names. Here is an example of what CSV data looks like. This is an abbreviated version of the first two lines in the World Bank projects data csv file.

     id,regionname,countryname,prodline,lendinginstr
     P162228,Other,World;World,RE,Investment Project Financing

* **Take a look at [this Jupyter notebook]() to familiarize yourself with reading csv files.**
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

* **Check [this Jupyter notebook]() to familiarize yourself with reading JSON and XML files.**


### SQL databases
SQL databases store data in tables using [primary and foreign keys](https://docs.microsoft.com/en-us/sql/relational-databases/tables/primary-and-foreign-key-constraints?view=sql-server-2017). In a SQL database, the same data would look like this:

<p align="right">
  <img src="/imgs/2.PNG" alt="" width="300" height="100" >
 </p>
 
* **Take a look at [this Jupyter notebook]() to familiarize yourself with reading SQL databases.**

### APIs

Companies and organizations provide APIs so that programmers can access data in an official, safe way. APIs allow you to download, and sometimes even upload or modify, data from a web server without giving you direct access. APIs generally provide data in either JSON or XML format.
* **Take a look at [this Jupyter notebook]() to familiarize yourself with reading from APIs.**


