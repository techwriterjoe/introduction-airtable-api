# Introduction to Airtable API

This overiew describes the use of the Airtable API to communicate between an Airtable base and a custom built website. Airtable is a web application that creates base apps, which are colorful, intuitive, easy-to-use spreadsheet sets. The base tables organize images, tags, descriptions, and much more. With the Airtable API, the user-freindly base apps provide databases, which are interactable with any part of the web. Specifically, this material covers an API request for a list of data table records and another request for a single record.

##Getting Started with Airtable
Create an [Airtable account](https://airtable.com/) and select the example base named "Art Gallery". When finished, the browser displays a prefilled example table, pictured below (Fig 1).

![alt text](https://github.com/techwriterjoe/introduction-airtable-api/blob/master/art-gallery-base-outline.png "Art Gallery base and Artists table")

Notice different aspects of the example data:
- The name of the base app, "Art Gallery", is displayed at the top center of the page. 
- This sample base has two tables, named "Artists" and "Collections". 
- "Artists" is currently selected and open. 
- In Artists, there are 19 example records or entries with the first 6 pictured above. 
- There are several columns including Name, Attachments, and Bio. 

The table data has the ability to be used or updated with the Airtable API for outside applications.

##Understanding an API Call 
For a case study using the API, imagine a simple website that pulls the "Artists"' data from the table and displays the artists' names as a list on it's homepage. Each list item is also a link to information from the other columns of the "Artists" table. The hompegae for the example website is pictured below (Fig  2).

![alt text](https://github.com/techwriterjoe/introduction-airtable-api/blob/master/artists-website-homepage-outline.png "Artists homepage")

The example site requests data from the "Artists" database table with every refresh of the browser. The Airtable API and Airtable base apps update in real time. For instance, if the "Name" column is re-ordered in the Airtable web interface, for example by an added table filter, then the list displaying on the homepage is also reordered after the browser is refreshed. Every request to the Airtable API handles up-to-date information from the spreadsheets.  

##API Request Example for a List of Records
To learn how the Airtable API provides the public website with the "Name" data from the "Artists" table, recreate the same API request with a tool called [Hurl.it](https://www.hurl.it/). [Hurl.it](https://www.hurl.it/) is a web based REST client. Aftertaking some inputs, it sends the same request to the "Artists" table as the example website. 

To set up the first API request and retrieve the list of artists' records, use the image and directions below: 

![alt text](https://github.com/techwriterjoe/introduction-airtable-api/blob/master/hurl-it-request-outline.png "Hurl.it request information")

To complete the [Hurl.it](https://www.hurl.it/) web form, gather the Airtable account API key and the Airtable base or app ID.  

To locate the API key:

1. From the "Art Gallery" base page at the top right, select the profile image icon, which is displayed as an empty profile image in Figure 1 above.
2. In the profile drop down menu under the account's email address, select the "Account" option.
3. From the "Your Account" page, select "Generate API key".

To locate the app ID:

1. From the "Art Gallery" base page at the top right, select the "HELP" option.
2. In the "HELP" drop-down menu, select the "API docs" option.

   >Note: Airtable's API docs are dynamically generated to use the current accounts information. Meaning, if the account is signed into the same web browser, then the API docs display that specific base, table, API key, and other data in the docs' examples. 

3. From the "Airtable API for 'Art Gallery'" page, select the "AUTHENTICATION" link, which is displayed on the left side-bar.
4. The app ID is listed on the right, blackened window-pane. It is located in the URL between "v0/" and "/Artists".

###Reading the URL
Enter the API key, the app ID, and the remaining field information as displayed above (Fig 3). Before launching the request, analyze the below URL.

>https://api.airtable.com/v0/appFMngUhBgzpTEsk/Artists/?view=Main%20View&limit=3&offset=&sortField=Name&sortDirection=asc Note: if this link is selected, then a browser with an Authication error should appear.

Initially, the URL locates the "Artists" table:
- https://api.airtable.com/v0 points the request to the Airtable API. 
- /appFMngUhBgzpTEsk is the base or app id, in this case, the id for the specific "Art Gallery" base
- /Artists is the specific table within the base "Art Gallery"

After the table has been located, the URL contains a query string in order to search the table:

- "?" represents the start of the query set.
- "view=Main%20View" is the first query field, along with the view value Main View. 
- "%20" represents a space in HTTP.
- "&" is also part of the query string and allows the next URL parameter to be added
- "limit=3" is a query parameter requests that only 3 records of the original 19 be returned in the response; Airtable handles a limit up to 100
- "&offset=" requests how many records are remaining after the initial 3 that will be returned, no value necessary
- "&sortField=Name&sortDirection=asc" by default, the reponse returns the list of records in the same order as they are listed in the Main View. However, the sortField and sortDirection override the default sort order.

###Authentication and Launching the Request
For authentication, Airtable recommends using the API key as a header. Headers are part of HTTP protocol and a typical HTTP request usually contains several. Headers are not typically displayed with the HTML. As demonstrated (Fig 4), enter the __"Authorization"__ as the header name and __"Bearer keyV6E7OIK5SJudPy"__ as the header value, but replace with the appropriate text according to the account.

Return to [Hurl.it](https://www.hurl.it/) and lauch the request.

##Reading the Response
After the request is launched, [Hurl.it](https://www.hurl.it/) displays the JSON response from Airtable. APIs typically communicate in either XML or JSON. Airtable uses JSON, which is a standard within the JavaScript language. 

>Below is a small sample of only one JSON record of the three requested, within that record only one JSON attachment is displayed. The "{...}" symbols are used to represent the collapsed or code folded, hidden records and attachments. To view the entire JSON records list with all the child-objects and child-arrays, explore the response on [Hurl.it](https://www.hurl.it/) with various limit values within the request. This request is designed for the list of many records. Requesting a single record is covered later on in this document.

```javascript
Response Body
{
   "records": [
      {
         "id": "recwNr9rKGIekjxzk",
         "fields": {
            "Name": "Alexander Calder",
            "Attachments": [
               {
                  "id": "attYqPQyYoWue1S1m",
                  "url": "https://dl.airtable.com/48PltjWqScqDZEQmLJHl_20120621-114822.jpg",
                  "filename": "20120621-114822.jpg",
                  "size": 158060,
                  "type": "image/jpeg",
                  "thumbnails": {
                     "small": {
                        "url": "https://dl.airtable.com/9PkZEE7PTv6SGIZmFcFr_small_20120621-114822.jpg",
                        "width": 40,
                        "height": 36
                     },
                     "large": {
                        "url": "https://dl.airtable.com/w92GiIvtROixep7uqfFk_large_20120621-114822.jpg",
                        "width": 256,
                        "height": 230
                     }
                  }
               },
               {...},
               {...}
            ],
            "Bio": "Alexander Calder was an American sculptor known as the originator of the mobile, a type of kinetic sculpture made with delicately balanced or suspended components which move in response to motor power or air currents. Calder’s stationary sculptures are called stabiles. He also produced numerous wire figures, notably for a miniature circus.\n",
            "Genre": [
               "Surrealism",
               "Modern art",
               "Kinetic Art"
            ],
            "Collection": [
               "recmuGWV1K17eIWCa"
            ],
            "On Display?": true
         },
         "createdTime": "2015-02-09T23:04:03.000Z"
      }
      {...}
      {...}
   ],
   "offset": "itrJHzurZ3IkRqnaY/recwNr9rKGIekjxzk"
}
```

As shown above, a record contains an "id" value, "fields" object, and a "createdTime" value. The fields object has 6 child objects or child arrays, including the large attachment array, which contains child-objects of its own and so on. A JSON record contains all of the information displayed in the original "Artists" Airtable; for example the links of the attachment thumbnails, the "Genre" tags, and the "On Display?" boolean.

Notice the last value listed on the same level as the records array, the "offset" value. This information allows the next request to call the remaindor of the records. If there are 19 total records, and 3 were already requested, then the offset value tracks the 16 left.
 
##Creating an Artists' Details Page: Retrieve a Single Record
The example website's homepage uses a request designed to respond with a list of multiple records. However, for an individual artist's detail page, a request only needs a single record from the Airtable database.

Each artist's name listed on the homepage links to a detail similar to the one pictured below (Fig 5). To create this page, the website enters a different single record request to the API.    

![alt text](https://github.com/techwriterjoe/introduction-airtable-api/blob/master/artist-link-outline.png "Example website bio page")

The artist's detail page request is smaller and easier than the list example. Return to [Hurl.it](https://www.hurl.it/) and fill in the web form with the following URL and the previous header information, pictured below (Fig 6).

![alt text](https://github.com/techwriterjoe/introduction-airtable-api/blob/master/hurl-it-single-record-outline.png "Single record API request")

Prior to launching the request, examine the URL.

> https://api.airtable.com/v0/appdAud8ZSY3JcFYT/Artists/recOHPNmxtTbEstyu

The URL locates the individual record:
- The API link, app id, and table name are similar to the previous request URL
- The new item is the record id at the end of the URL, listed above as: "recOHPNmxtTbEstyu"

To locate the record id:

1. Return to the API docs, specifically the "Airtable API for 'Art Gallery'" page.
2. From the "Airtable API for 'Art Gallery'" page, select the "Retrieve a Record" link, which is displayed on the left side-bar.
3. The rec ID for the signed in account is listed on the right, blackened window-pane. It is located in the URL after "/Artists".

Authentication for the single record request is handled the same as the list of records' request. 

##What to do Next?

This overview demonstrated how to send two different requests to the Airtable API. Also, a sample website was pictured for a pratical use case. However, the Airtable API is capable of setting, deleting, and changing records as well. The external use of the API is near endless. Continue to read the Airtable API docs and additional Airtable videos. 


