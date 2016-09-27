# Introduction to Airtable API

This overiew describes the use of the Airtable API to communicate between an Airtable base and a custom built website. Airtable is a web application that creates base apps, which are colorful, intuitive, easy-to-use spreadsheet sets. The base tables organize images, tags, descriptions, and much more. With the Airtable API, the user-freindly base apps provide a database admin that can be interacted with from anywhere across the web.

##Get Started with Airtable
To proceed, create an [Airtable account](https://airtable.com/) and select the example base named "Art Gallery". When finished, the browser displays a prefilled example table, pictured below (Fig 1).

![alt text](https://github.com/techwriterjoe/introduction-airtable-api/blob/master/art-gallery-base-outline.png "Art Gallery base and Artists table")

Notice different aspects of the example data:
- The name of the base app, "Art Gallery", is displayed at the top center of the page. 
- This sample base has two tables, named "Artists" and "Collections". 
- "Artists" is currently selected and open. 
- In Artists, there are 19 example records or entries with the first 6 pictured above. 
- There are several columns including Name, Attachments, and Bio. 

The table data has the ability to be used or updated with the Airtable API for outside applications.

##Understanding an API Call 
For a case study using the API, a simple website pulls the "Artists"' data the table and displays the artists' names as a list. Each list item is a link to information from the other columns of the "Artists'" table, pictured below (Fig  2).

![alt text](https://github.com/techwriterjoe/introduction-airtable-api/blob/master/artists-website-homepage-outline.png "Artists homepage")

The sample site requests data from the database table with every refresh of the browser. If the "Name" column is re-ordered in the Airtable web interface, for example by an added table filter, then the list displaying on the homepage is also reordered after the browser is refreshed. The artists' names are linked to the additional information on the site, which was provided by the through requests or calls to the API.

##API Request and Response Examples
To learn how the Airtable API provides the public website with the "Name" data from the "Artists" table, recreate the same API request with a tool called [Hurl.it](https://www.hurl.it/). [Hurl.it](https://www.hurl.it/) is a web based REST client. Aftertaking some inputs, it sends the same request to the "Artists" table as the sample website. 

To set up the first API request and retrieve the list of artists' records, use the image and directions below: 

![alt text](https://github.com/techwriterjoe/introduction-airtable-api/blob/master/hurl-it-request-outline.png "Hurl.it request information")

To complete the Hurl.it web form, gather the API key and the base or app ID.  

To find the API key:

1. From the Art Gallery base page at the top right, select the profile image icon, which is displayed as an empty profile image in Figure 1 above.
2. In the profile drop down menu under the account's email address, select the Account option.
3. From the "Your Account" page, select "Generate API key"

To find the app ID:

1. From the Art Gallery base page at the top right, select the "HELP" option.
2. In the HELP drop-down menu, select the "API docs" option.

   >Note: Airtable's API docs are dynamically generated to use the current accounts information. Meaning, if the account is signed into the web browser, then the API docs display that specific base, table, API key, and other data in the examples. 

3. From the "Airtable API for 'Art Gallery'" page, select the "AUTHENTICATION" option, which is displayed on the left side-bar.
4. The app ID is listed in the right, blackened window-pane. It is located in the URL between "v0/" and "/Artists".

###Analyzing the URL and Lauching the Request
Enter the API key, the app ID, and the remaining field information as displayed above (Fig 3). Before launching the request, analyze the below URL.

>https://api.airtable.com/v0/appFMngUhBgzpTEsk/Artists/?view=Main%20View&limit=3&offset=&sortField=Name&sortDirection=asc

Initially, the URL locates the "Artists" table:
- https://api.airtable.com/v0 points the request to the Airtable API. 
- /appFMngUhBgzpTEsk is the base or app id, in this case, the id for the specific "Art Gallery" base
- /Artists is the specific table within the base "Art Gallery"

After the table has been located, the URL contains a query string:

- "?" represents the start of the query set.
- "view=Main%20View" is the first query field, along with the view value Main View. 
- "%20" represents a space in HTTP.
- "&" is also part of the query string and allows the next URL parameter to be added
- "limit=3" requests that only 3 records of the original 19 be returned in the response
- "&offset=" requests how many records are remaining after the 3 that will be returned, no value necessary
- "&sortField=Name&sortDirection=asc" by default, the reponse returns the list of records in the same order as they are listed in the Main View. However, the sortField and sortDirection override the default sort.

###Authentication
For authentication, Airtable recommends using the API key as a header.









