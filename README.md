Data Representation and Querying Project 2015
# Penalty Points Issued in Ireland
### 19th October 2015
### Ed Lasauskas

##Overview
This is a project to design and document an API for a dataset. The dataset was taken from the road safety authority website - [RSA.ie](http://www.rsa.ie/)

##The dataset
The dataset is in PDF format and is available 
[here](http://www.rsa.ie/Documents/PenaltyPointsStats/2015/Jan/Analysis%20of%20Penalty%20Points%20(Current)%20Issued%20-%20(Cumulative)%20January%20%202015.pdf).

This is a dataset for the number drivers in all counties in Ireland and the amount of penalty
points the drivers have. This PDF is based on the total figures across all of Ireland on *31st of January 2015* and the number of penalty points issued changes every day.

There are 28 rows of all counties in Ireland (eg. **Galway**) plus foreign licence holders and the "unknown" row.

There are 13 columns across 1 - 12 being (**penalty points** 1 to 12) and total number of penalty points in the last column.

# Queries

## Get

There are a few variations of the get query and how much detail or specification you want in the data returned from the query.

###List of total Penalty points issued by Year.

For Example
url: *https://rsa.ie/documents/penaltypointsstats/(Year)* , you can replace (Year) with a value for the year to show data for that given year.

The Url: https://rsa.ie/documents/penaltypointsstats/2015 will return the total data of issued penalty points for the year 2015.

The data is returned in JSON and for the year will be displayed with the following properties:

**- ID of the table - year(2015 - 15)**

**- Year of the Data**

**- Category of No. of points (1-12)**

**- Total points for a given Category**

**- Type of request**

**- URL of the request**

In code example:

```json
[{"id": 15,
"Year": 2015, 
"Category(1-12)": 3, 
"Total points": 7865, 
"type" : "Get",
"url" : "https://rsa.ie/documents/penaltypointsstats/2015"}]
```

###List of total Penalty points issued by Month.

For Example
url: *https://rsa.ie/documents/penaltypointsstats/(Year)/(Month)* , you can replace (Year) and (Month) with a value for the year and month to show data for that given year and month.

The Url: https://rsa.ie/documents/penaltypointsstats/2015/January will return the total data of issued penalty points for the month of January of  2015.

The data is returned in JSON and for the year will be displayed with the following properties:

**- ID of the table - year/month(2015 January - 15/01)**

**- Year of the Data**

**- Month of the Year for the data**

**- Category of No. of points (1-12)**

**- Total points for a given Category**

**- Type of request**

**- URL of the request**

In code example:

```json
[{"id": 15/01,
"Year": 2015,
"Month": January,
"Category(1-12)": 3, 
"Total points": 2345, 
"type" : "Get",
"url" : "https://rsa.ie/documents/penaltypointsstats/2015/January"}]
```

###List of total Penalty points issued by County.

For Example
url: *https://rsa.ie/documents/penaltypointsstats/(Year)/County* , you can replace (Year) and (County) with a value for the year and county of Ireland to show data for that given year and county.

The Url: https://rsa.ie/documents/penaltypointsstats/2015/Galway will return the total data of issued penalty points for the county of Galway in 2015.

The data is returned in JSON and for the year will be displayed with the following properties:

**- ID of the table - year/county(2015 Galway - 15/Galway)**

**- Year of the Data**

**- County in Ireland for the data**

**- Category of No. of points (1-12)**

**- Total points for a given Category**

**- Type of request**

**- URL of the request**

In code example:

```json
[{"id": 15/Galway,
"Year": 2015, 
"County": Galway,
"Category(1-12)": 3, 
"Total points": 4123, 
"type" : "Get",
"url" : "https://rsa.ie/documents/penaltypointsstats/2015/Galway"}]
```
