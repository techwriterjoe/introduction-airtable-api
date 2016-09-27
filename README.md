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
To learn how the Airtable API provides the public website with the "Name" data from the "Artists" table, recreate the same API calls with a tool call [Hurl.it](https://www.hurl.it/).
<!--will need info on the dynamic API Docs and where to find Auth Key-->
![alt text](https://github.com/techwriterjoe/introduction-airtable-api/blob/master/hurl-it-request-outline.png "Hurl.it request information")




