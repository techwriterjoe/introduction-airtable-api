# Introduction to Airtable API

This overiew displays the use of the Airtable API to communicate between an Airtable base table and a custom built website. Airtable is a web application that creates base apps, which are colorful, intuitive, easy-to-use spreadsheet sets. The base tables organize images, tags, descriptions, and much more. With the Airtable API, the user-freindly base apps provide a database admin that can be interacted from anywhere across the web.  

##Get Started with Airtable
To proceed, create an [Airtable account](https://airtable.com/) and select the example base named "Art Gallery". When finished, the browser displays a prefilled example table, pictured below in figure 1.
![alt text](https://github.com/techwriterjoe/introduction-airtable-api/blob/master/art-gallery-base-outline.png "Art Gallery base and Artists table")
Notice the name of the base app, Art Gallery, is displayed at the top center of the page. This base has two tables Artists and Collections. Artists is currently selected and open. In Artists, there are 19 example records or entries with the first 6 pictured above. There are several columns including Name, Attachments, and Bio. All of the table data has the ability to be updated with the Airtable API for outside applications.

##Understanding an API Call 
Using the API, a simple website pulls the data from the "Artists" table and displays the artists' names as a list. Each list item is linked to information from the other columns of the "Artists", pictured below in figure 2.

![alt text](https://github.com/techwriterjoe/introduction-airtable-api/blob/master/artists-website-homepage-outline.png "Artists homepage")

The sample site requests data from the database table with every refresh of the browser. If the "Name" column is re-ordered in the Airtable web interface, for example by an added table filter, then the list displaying on the homepage is also reordered after the browser is refreshed.

##API Request and Response Examples
To learn how the Airtable API provides the public website with the "Name" data from the "Artists" table, recreate the same API request with a tool call [Hurl.it](https://www.hurl.it/). Hurl.it is a web based REST client.

Set up the first API request to retrieve the list of records, which is the data listed in the rows of the "Artists" table. Use the image and directions below: 
<!--will need info on the dynamic API Docs and where to find Auth Key-->
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




