# Workshop

##Clients
**NOTE** : every **GET** method request can be made with **browsers**

For this work shop you have the option of using either Postman or curl. Postman is an easy graphical chrome app, while CURL is a command line program, built in to Mac and Linux. You can use either, but Postman is reccommended for beginners:

* Postman
  * https://chrome.google.com/webstore/detail/postman-rest-client-short/mkhojklkhkdaghjjfdnphfphiaiohkef?hl=en (Old version)
  * https://www.getpostman.com (New version)
* CURL
  * http://bagder.github.io/curl-cheat-sheet/http-sheet.html




##Information about our Server - dvcoders home brewed API 
##### Our API stack 
  * Java 8
  * Dropwizard framework [Jetty (HTTP), Jersey (REST), Jackson (JSON)] 
     * http://www.dropwizard.io/getting-started.html
  * MongoDB 
     * http://docs.mongodb.org/manual/
  * It's open source
     * https://github.com/dvcoders/workshop-server 

##### REST API (Ref : https://github.com/dvcoders/intro-web/tree/master/reference#http-hypertext-transfer-protocol)
  * **GET - Read a record**. Body request is not needed. Query Param and Path Param are optional 
  * **POST - Create a record**. Body request needed
  * **PUT - Update a record**. Body request needed 
  * **DELETE - Delete a record**. Body request needed
  * **HEAD - Get the header**. Body request is not needed.

##### HTTP Status Code 
  * **200 - OK**. Everything is good
  * **307 - Temporary Redirect**. Temporarily redirecting the Client to abc.xyz 
  * **400 - Bad Request**. Client did not give me what Server was expecting 
  * **401 - Unauthorized**. Client needs to identify itself. Usually by including `Authorization` in header 
  * **403 - Forbidden**. Server refuses to respond to the Client 
  * **404 - Not Found**. Data or endpoint not found 
  * **409 - Conflict**. Request may conflict with existing data
  * **500 - Internal Server Error**. Server's error. Failed to process the request 




## Beginning the workshop - Working with REST Endpoint
**NOTE** :
 * **Request** - Client to Server
 * **Response** - Server to Client

You're going to be making different HTTP requests, using Postman or curl. In order to make it easy, Jake created an easy to use list of requests that you can import. In order to do so follow these steps:

![](images/2.png)

Go to the import section on Postman (at the top). Click on download from link. Paste this link: 

https://raw.githubusercontent.com/JakeLoo/intro-web/master/workshop/dvcoders-workshop.json

![](images/1.png)

All the HTTP requests you'll be doing from now on will be in the "collections" list in Postman:

![](images/4.png)


**GET /user/list** - *Get all of the users in the database*
```
Response :
{
    "result": [
        {
            "student_id": "1234567",
            "github_url": "https://www.github.com/daniel-awai",
            "first_name": "daniel",
            "last_name": "awai"
        },
        {
            "student_id": "0000000",
            "first_name": "John",
            "last_name": "Doe"
        }
        ...
    ],
    "code": 200,
    "current_at": 1443047995829,
    "event_id": "db471924-b33b-4b18-b8a8-dc0951677dcf"
}
```
*The client makes a request to the server. The server find all of the saved users in database, then return the users (JSON formatted) to the client with an OK.*


**GET /user?student_id=1234567** - *Get the infomation of the user with the student_id of 1234567*
```
Response :
{
    "student_id": "1234567",
    "github_url": "https://www.github.com/daniel-awai",
    "first_name": "daniel",
    "last_name": "awai",
    "code": 200,
    "current_at": 1443047644053,
    "event_id": "d70d3abd-1dea-4589-8231-e7589ba34267"
}
```
*The client makes a GET request to the server with the data of student_id of 1234567. The server takes the student_id=1234567 from that request and does a lookup for that user in the database. Once the data has been found, the server returns the user (JSON formatted) to the client along with a status of OK.*


**GET /user?student_id=0** - *Get the infomation of the user with the student_id of 0*
```
Response :
{
  message: "User not found",
  code: 404,
  current_at: 1443050798167,
  event_id: "9662ac5f-85bc-4820-8a2b-dd7f3e09defan"
}
```
*The client makes a GET request to the server with the data of student_id of 0. The server takes the student_id=0 from that request and does a lookup in the database. The data couldn't find the data, then the server returns an error with the status of NOT FOUND.*


**POST /user** - *Attempt to create an user with the student id that has already been used*
```
Request :
{
    "student_id": "1234567",
    "first_name": "John",
    "last_name" : "Doe"
}

Response :
{
    "message": "User is exist",
    "code": 409,
    "current_at": 1443047547564,
    "event_id": "f73b7d0b-11e0-47ff-864e-024527e43804"
}
```
*The client makes a POST request with data in request body. The server validates the request body, then takes the student_id from the request body and does a lookup for that user in the database. After the database lookup, if the server successfully found a user with that student_id that is provided in the request, the server returns an error with the status of CONFLICT.*


**POST /user** - *Create an user and store it in the database*
```
Request:
{
    "student_id": "<STUDENT_ID>",
    "first_name": "<FIRST_NAME>",
    "last_name" : "<LAST_NAME>"
}

Response:
{
    "student_id": "<STUDENT_ID>",
    "first_name": "<FIRST_NAME>",
    "last_name": "<LAST_NAME>",
    "code": 200,
    "current_at": 1443047819830,
    "event_id": "98f9b8df-e1c6-40a3-ab39-a99e88e87a49"
}
```
*The client makes a POST request with data in request body. The server validates the request body, then takes the student_id from the request body and does an user lookup in the database. The server fails to find any data with that student_id, then the server converts the data in request body into an user object, then saves it into to the database. Once it is successfully saved, the server returns the user object that has been saved to the client.*


**GET /user?student_id={student_id}** - *Get the infomation of the user with the student_id of {student_id}*
```
Response :
{
    "student_id": "<STUDENT_ID>",
    "first_name": "<FIRST_NAME>",
    "last_name": "<LAST_NAME>",
    "code": 200,
    "current_at": 1443047644053,
    "event_id": "d70d3abd-1dea-4589-8231-e7589ba34267"
}
```
*The client makes a GET request to the server with the data of student_id of 1234567. The server takes the student_id=1234567 from that request and does a lookup in the database. After the data has been found, the server returns the user (JSON formatted) to the client with an OK.*


**GET /github/{studentId}** - *Attempt to redirect to user's github account, but the user doesn't have github information in the profile* 
```
Path Param : {studentId} = Your student ID. Example : 1000000 

Response :
{
  message: "No github url associated with the account",
  code: 403,
  current_at: 1443048083243,
  event_id: "288881ae-410a-41d8-8a3b-298e0c9264d6"
}
```
*The client makes a GET request to the server with the path param of studentId of 1000000. The server takes the student_id=1000000 from that request and does a lookup in the database. The data has been found, then the server checks if there's any github_url store in the user object. If not then the user returns Forbidden error to prevent the client redirect to empty url.*


**PUT /user** - *Update the user information*
```
Request:
{
  "student_id": "<STUDENT_ID>",
  "github_url": "<GITHUB_URL>"
}

Response:
{
    "student_id": "<STUDENT_ID>",
    "github_url": "<GITHUB_URL>",
    "first_name": "<FIRST_NAME>",
    "last_name": "<LAST_NAME>",
    "code": 200,
    "current_at": 1443048159669,
    "event_id": "02922c34-b2b7-421a-b7b5-813d8672318f"
}
```
*The client makes a PUT request with the data above. The server validates the request body, then takes the student_id from that request body and does a lookup for the user in the database. The server found the user data, then updates the old user data with the new data given in the request body. Finally, save the updated user data into the database and return the data that has been saved along with status of OK to the client.*


**GET /github/{studentId}** - *Redirect to user's github profile*
```
magics.
```
*The client makes a GET request to the server with the path param of studentId of {student_id}. The server takes the {student_id} from the path param and does a lookup in the database. Then the server gets github_url that is stored in the user object then redirect the client to the github_url that is stored in the user.*


**DELETE  /user** - *Delete a user from database*
```
Request :
{
  "student_id": "<STUDENT_ID>"
}

Response :
{
    "message": "You do not have the privilege",
    "code": 401,
    "current_at": 1443048277224,
    "event_id": "3356e3e6-7027-4f2a-a9c2-2da92a024c6a"
}
```
*The client makes a DELETE request to the server with the student_id in the body request. The server returns Unauthorized because your request is not authorized. Thus, the server assumes that you do not have permission to do it.*


**GET /user/null** - *Internal Server Error* 
```
Response :
{
    "message": "/ by zero",
    "code": 500,
    "current_at": 1443048317065,
    "event_id": "59a3eece-a975-4cf5-ae9d-d39a2e7f5f02"
}
```
*The clients makes a GET request to the server. The server returns Internal Server Errors because there are some exceptions/error while processing the request*


## Other than dvcoders API
  * Google Maps API - https://maps.googleapis.com/maps/api/geocode/json?address=chicago
  * Starbucks API - https://testhost.openapi.starbucks.com/location/v2/stores
  * Twitter API - https://dev.twitter.com/rest/tools/console
  * Facebook API - https://developers.facebook.com/tools/explorer

