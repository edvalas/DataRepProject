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

For Example
url: *https://rsa.ie/documents/penaltypointsstats/(Year)* , you can replace (Year) with a value for the year to show data for that given year.

The Url: https://rsa.ie/documents/penaltypointsstats/2015 will return the total data of issued penalty points for the year 2015.

The data is returned in JSON and for the year will be displayed with the following properties:

**- Year of the Data**
**- Category of No. of points (1-12)**
**- Total points for a given Category**

In code example:

```json
[{"Year": 2015, "Category(1-12)": 3, "Total points": 100, ....}]
```
