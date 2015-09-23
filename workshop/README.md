# Intro Web Workshop

##Clients
* Postman
  * https://chrome.google.com/webstore/detail/postman-rest-client-short/mkhojklkhkdaghjjfdnphfphiaiohkef?hl=en

* CURL
  * http://bagder.github.io/curl-cheat-sheet/http-sheet.html


##dvcoders home brewed API 
* Talk about this API stack 
  * Java 8
  * Dropwizard framework [Jetty (HTTP), Jersey (REST), Jackson (JSON)] 
     * http://www.dropwizard.io/getting-started.html
  * MongoDB 
     * http://docs.mongodb.org/manual/

* REST API (Ref : https://github.com/dvcoders/intro-web/tree/master/reference#http-hypertext-transfer-protocol)
  * GET - Read a record, NO body, OPTIONAL query param OR path param
  * POST - Create a record, body
  * PUT - Update a record, body
  * DELETE - Delete a record

* HTTP Status Code 
  * 200 - OK, everything is good
  * 307 - Temporary Redirect, im temporarily sending you to abc.xyz
  * 400 - Bad Request, not giving me what i expected
  * 401 - Unauthorized, need to identify yourself first
  * 403 - Forbidden, i am refuse to respond to you, i don’t care who are you
  * 404 - Not Found, what you requested is not found
  * 409 - Conflict, about to make a changes that cause conflict
  * 500 - Internal Server Error, my bad, failed to process the data

##Working with REST Endpoint
*Request* - Client sends to a Server
*Response* - Server sends to a Client


GET     /user/list - *Get all of the users in database*
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

GET     /user?student_id={studentId} - *Get a specific user information*
```
Query Param : {studentId} = Your student ID. Example : 1234567

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

POST    /user - *Creating a user*
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

POST    /user - *Create an user and store it in the database*
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

GET     /github/{studentId} - *Failure case* 
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

PUT     /user - *Update the user information*
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

GET     /github/{studentId} - *Redirect to user's github profile*
```
magics.
```

DELETE  /user - *Delete a user from database*
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


GET     /user/null - *Demostrate an Internal Server Error* 
```
Response :
{
    "message": "/ by zero",
    "code": 500,
    "current_at": 1443048317065,
    "event_id": "59a3eece-a975-4cf5-ae9d-d39a2e7f5f02"
}
```
