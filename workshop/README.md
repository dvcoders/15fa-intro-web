# Intro Web Workshop

##Clients
Postman https://chrome.google.com/webstore/detail/postman-rest-client-short/mkhojklkhkdaghjjfdnphfphiaiohkef?hl=en
curl http://bagder.github.io/curl-cheat-sheet/http-sheet.html


##Jake’s awesome + wonderful + wat + ???? api
* Talk about this API stack (setup server bts)
  * Java 8
  * Dropwizard framework -> Jetty (HTTP), Jersey (REST), Jackson (JSON), http://www.dropwizard.io/getting-started.html
  * MongoDB http://docs.mongodb.org/manual/ just saying were using

* REST API 
  * GET - Read a record, NO body, OPTIONAL query param OR path param
  * POST - Create a record, body
  * PUT - Update a record, body
  * DELETE - Delete a record

##Status Codes - just so you know
  * 200 - OK, everything is good
  * 307 - Temporary Redirect, im temporarily sending you to abc.xyz
  * 400 - Bad Request, not giving me what i expected
  * 401 - Unauthorized, need to identify yourself first
  * 403 - Forbidden, i am refuse to respond to you, i don’t care who are you
  * 404 - Not Found, what you requested is not found
  * 409 - Conflict, about to make a changes that cause conflict
  * 500 - Internal Server Error, my bad, failed to process the data

##rest Endpoint
 GET /users
 GET all of the registered users
 Response:
  ```
{
  “code”: 200,
    “results”: [{
      “student_id”:”...”
    },
    {
      “student_id”:”...”
    }]
}
```

GET /user?student_id={student_id}
GET a specific user by student id
Response:
```
{
  “code”: 200,
    “event”: “”,
    “student_id”:”...”
}
```

POST /user
CREATE a user
Request:
```
{
  “student_id”: “”
    “github_url”: “”
    “first_name”: “”
    “last_name”: “”
}
```

PUT /user
UPDATE a user

DELETE /user?student_id={student_id}
DELETE a user with given student id

GET /github/{student_id}
307 redirects to user.github_url

Stage
Alpha draft
Beta draft
Production draft
