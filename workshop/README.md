# Workshop

##Clients
**NOTE** : every **GET** method request can be made with **browsers**
* Postman
  * https://chrome.google.com/webstore/detail/postman-rest-client-short/mkhojklkhkdaghjjfdnphfphiaiohkef?hl=en (Old version)
  * https://www.getpostman.com (New version)
* CURL
  * http://bagder.github.io/curl-cheat-sheet/http-sheet.html




##Server - dvcoders home brewed API 
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
  * **400 - Bad Request**. Client did not give me what Server am expecting 
  * **401 - Unauthorized**. Client needs to identify itself. Usually by including `Authorization` in header 
  * **403 - Forbidden**. Server refuses to respond to the Client 
  * **404 - Not Found**. Data or endpoint not found 
  * **409 - Conflict**. Request may conflict with existing data
  * **500 - Internal Server Error**. Server's error. Failed to process the request 




##Working with REST Endpoint
**NOTE** :
 * **Request** - Client to Server
 * **Response** - Server to Client


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
*The client makes a GET request to the server with the data of student_id of 1234567. The server takes the student_id=1234567 from that request and do a lookup in the database. The data has been found, then the server returns the user (JSON formatted) to the client with an OK.*


**GET /user?student_id=0** - *Get the infomation of the user with the student_id of 0*
```
Response :
{
  message: "User not found",
  code: 404,
  current_at: 1443050798167,
  event_id: "9662ac5f-85bc-4820-8a2b-dd7f3e09defa"
}
```
*The client makes a GET request to the server with the data of student_id of 0. The server takes the student_id=0 from that request and do a lookup in the database. The data couldn't find the data, then the server returns an error with the status of NOT FOUND.*


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
*The client makes a POST request with the data of ^. The server validates the request body, then takes the student_id that from that request and do a lookup in the database. The server found out that there is a data associated with the given student_id, then the server returns an error with the status of CONFLICT.*


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
*The client makes a POST request with the data of ^. The server validates the request body, then takes the student_id that from that request and do a lookup in the database. The server fails to find any data with that student_id, then the server save the user to the database and return what have been saved to the client with the status of OK.*


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

**GET /github/{studentId}** - *Attempt to redirect to user's github account, but the user doesn't have github information in the profile* 
```
Path Param : {studentId} = Your student ID. Example : 0000000 

Response :
{
  message: "No github url associated with the account",
  code: 403,
  current_at: 1443048083243,
  event_id: "288881ae-410a-41d8-8a3b-298e0c9264d6"
}
```

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

**GET /github/{studentId}** - *Redirect to user's github profile*
```
magics.
```

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


**GET /user/null** - *Internal Server Error request* 
```
Response :
{
    "message": "/ by zero",
    "code": 500,
    "current_at": 1443048317065,
    "event_id": "59a3eece-a975-4cf5-ae9d-d39a2e7f5f02"
}
```

## Other than dvcoders API
  * Google Maps API - https://maps.googleapis.com/maps/api/geocode/json?address=chicago
  * Starbucks API - https://testhost.openapi.starbucks.com/location/v2/stores
  * Twitter API - https://dev.twitter.com/rest/tools/console
  * Facebook API - https://developers.facebook.com/tools/explorer



