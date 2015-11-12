Data Representation and Querying Project 2015
# Penalty Points Issued in Ireland
### 19th October 2015
### Ed Lasauskas

##Overview
This is a project to design and document an API for a dataset, not to implement it. I found the dataset on [data.gov.ie](https://data.gov.ie/data), but dataset was taken from the road safety authority website - [RSA.ie](http://www.rsa.ie/). This dataset is designed to be easy to use and access and is to be used by the appropriate audience.

##The dataset
The dataset is in PDF format and is available 
[here](http://www.rsa.ie/Documents/PenaltyPointsStats/2015/Jan/Analysis%20of%20Penalty%20Points%20(Current)%20Issued%20-%20(Cumulative)%20January%20%202015.pdf).

This is a dataset for the number drivers in all counties in Ireland and the amount of penalty
points the drivers have. This PDF is based on the total figures across all of Ireland on *31st of January 2015* and the number of penalty points issued changes every day.

There are 29 rows of all counties in Ireland (eg. **Galway**) plus foreign licence holders, the "unknown" row and the total row.

There are 13 columns across 1 - 12 being (**penalty points** 1 to 12) and total number of penalty points in the last column.

# Queries

## Get - method will return a table, row, column or cell from the dataset

There are a few variations of the get query and how much detail or specification you want in the data returned from the query.

###List of total Penalty points issued by Year.

For Example
url: *https://rsa.ie/documents/penaltypointsstats/(Year)* , you can replace (Year) with a value for the year to show data table for that given year.

The Url: https://rsa.ie/documents/penaltypointsstats/2015 will return the data table of issued penalty points for the year 2015.

The data is returned in JSON and for the given year, it will be displayed with the following properties:

**- ID of the table - year(2015 - id = 15)**

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
url: *https://rsa.ie/documents/penaltypointsstats/(Year)/(Month)* , you can replace (Year) and (Month) with a value for the year and month to show data table for that given year and month.

The Url: https://rsa.ie/documents/penaltypointsstats/2015/January will return the data table of issued penalty points for the month of January of 2015.

The data is returned in JSON and for the given year & month, it will be displayed with the following properties:

**- ID of the table - year/month(2015 January - id = 15-01)**

**- Year of the Data**

**- Month of the Year for the data**

**- Category of No. of points (1-12)**

**- Total points for a given Category**

**- Type of request**

**- URL of the request**

In code example:

```json
[{"id": 15-01,
"Year": 2015,
"Month": "January",
"Category(1-12)": 3, 
"Total points": 2345, 
"type" : "Get",
"url" : "https://rsa.ie/documents/penaltypointsstats/2015/January"}]
```

###List of total Penalty points issued by County.

For Example
url: *https://rsa.ie/documents/penaltypointsstats/(Year)/(County)* , you can replace (Year) and (County) with a value for the year and county of Ireland to show the data table for that given year and county.

The Url: https://rsa.ie/documents/penaltypointsstats/2015/Galway will return the data table of issued penalty points for the county of Galway in 2015.

The data is returned in JSON and for the given year & county, it will be displayed with the following properties:

**- ID of the table - year/county(2015 Galway - id = 15-Galway)**

**- Year of the Data**

**- County in Ireland for the data**

**- Category of No. of points (1-12)**

**- Total points for a given Category**

**- Type of request**

**- URL of the request**

In code example:

```json
[{"id": "15-Galway",
"Year": 2015, 
"County": "Galway",
"Category(1-12)": 3, 
"Total points": 4123, 
"type" : "Get",
"url" : "https://rsa.ie/documents/penaltypointsstats/2015/Galway"}]
```

###List of total Penalty points issued by Category.

For Example
url: *https://rsa.ie/documents/penaltypointsstats/(Year)penaltypoints?id=(Category)* , you can replace (Year) and (Category) with a value for the year and category(1-12) of penalty points to show data for that given year and category of points.

The Url: https://rsa.ie/documents/penaltypointsstats/2015/penaltypoints?id=3 will return the data table of issued penalty points for the category of 3 points in 2015.

The data is returned in JSON and for the given year & category of points(1-12), it will be displayed with the following properties:

**- ID of the table - year/category(1-12) (2015 3 - id = 15_3, underscore is used to not be mixed up with month id denoted by - )**

**- Year of the Data**

**- Category of No. of points (1-12)**

**- Total points for a given Category**

**- Type of request**

**- URL of the request**

In code example:

```json
[{"id": "15_3",
"Year": 2015, 
"Category(1-12)": 3, 
"Total points": 645, 
"type" : "Get",
"url" : "https://rsa.ie/documents/penaltypointsstats/2015/penaltypoints?id=3"}]
```

## Delete - method will delele a value in a specific cell in the dataset

###Delete the value of cell 2015 - January - Galway - Category 3.

You can replace (Year), (Month), (County) and (Category) with a value for the year, month, county and category(1-12) of penalty points to delete the value of that specific cell.

The Uri: /penaltypointsstats/2015/January/Galway/penaltypoints?id=3 will delete the value of the cell for the category of 3 points in Galway of January 2015.

For Example the request in http:

```html
DELETE /penaltypointsstats/2015/January/Galway/penaltypoints?id=3 HTTP/1.1
User-Agent: Chrome/46.0.2490 (compatible; Windows NT)
Host: localhost
Content-Type: text/html; charset=utf-8
Accept-Language: en-us
Connection: keep-alive
```

A responce example in http:

```html
HTTP/1.1 200 OK
Date: 13:16:53 Monday November 9 2015
Server: Some Server
Connection: Closed
Content-Type: text/html
uri: "http://localhost/penaltypointsstats/2015/January/Galway/penaltypoints?id=3"

<html>
<body>
<h1>Cell Value deleted.</h1>
</body>
</html>
```

## Post - method will post a value to be placed/updated in a specific cell in the dataset

###Post the value for cell 2015 - January - Galway - Category 3.

You can replace (Year), (Month), (County) and (Category) with a value for the year, month, county and category(1-12) of penalty points to post to update the value of that specific cell.

The Uri: /penaltypointsstats/2015/January/Galway/penaltypoints?id=3 will post the value of the cell for the category of 3 points in Galway of January 2015.

For Example the request in http:

```html
POST /penaltypointsstats/2015/January/Galway/penaltypoints?id=3 HTTP/1.1
User-Agent: Chrome/46.0.2490 (compatible; Windows NT)
Host: localhost
Content-Type: text/html; charset=utf-8
Accept-Language: en-us
Connection: Keep-Alive

<html>
<body>
<p>234</p>
</body>
</html>
```

A responce example in http:

```html
HTTP/1.1 200 OK
Date: 14:27:53 Monday November 9 2015
Server: Some Server
Last-Modified: 13:56:53 Monday November 9 2015 GMT
ETag: "ghfgnHR5435Y"
Content-Type: text/html
Connection: Closed

<html>
<body>
<h1>Request Processed Successfully</h1>
</body>
</html>
```

##Summary
In doing this documentation for an API for my project , I have learned how to use github markdown for editing text files and the use of http request and responce methods like Get, Post and others. I hope this API is easy to read, understand, easy to extend if needed and is useful as it is efficient. 
