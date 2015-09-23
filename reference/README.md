## Intro Web Guide

### What is the internet?

The internet is simply a global connection of computer networks.

Your home network connects to a network in your city, which connect to a larger network in your region, then to other networks in the country, which connect to networks around the world.

Through these connections your computer has connection to other computers. 

Some of these computers are called "servers". Servers are the backbone of the internet, they store content and "serve" them to users around the world. Servers need to more powerful than the average computer in order to handle up hundreds or millions of requests.

## Client

A client can be a computer's browser, a phone, a tablet, or anything else which accepts interactions with the user.

### What is HTML?

HyperText Markup Language is a markup language used to add structure and content to webpages.


HTML is composed of a series of tags such as `<p>` (paragraph) and `<img>` (image) to indicate different types of content. The `<div>` tag is used to break up groups of content.
  

Your browser interprets the tags and uses them to display the content how it is specified.


HTML follows the Document Object Model (DOM) convention. The DOM is a "tree" or "hierarchy" composed of objects. HTML elements are objects in the tree. Tags such as `<p>` and `<img>` specify elements. The DOM is called a "tree" because elements can be "children" of an element, or "parents" of elements as well.

![DOM Tree](http://www.w3schools.com/js/pic_htmltree.gif)

(Image courtesty of w3schools.com)

### What is CSS

Cascading Style Sheets is a language used to design the appearance and formatting of a webpage.

### How does the browser work?

![Trees](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/images/render-tree-construction.png)

(Image courtesy of develpers.google.com)

Browsers use a rendering engine to interpret the HTML and create what is called a content tree. The content tree follows the DOM structure in creating nodes of connected elements like `<p>` and `<img>`.

The rendering engine also reads the styling of the elements in the HTML and related CSS files. Then, the CSSOM -- CSS Object Model -- is constructed by the rendering engine with information about each node's style.

Using the content tree and CSSOM, the render tree is also constructed, which only contains elements that will be displayed. The render tree will not contain elements such as `head` which contain no visible content.

In a process called "layout", the rendering engine uses the render tree to calculate the position and size of each element. Then, the elements are placed in the browser screen in a process called "painting."

Browsers such as Chrome and Firefox use a method known as sandboxing as a security feature. Malicious code from a website will be prevented from causing damage and accessing the system's files.

## Server

### What is an IP Address?

An IP address is a unique number assigned to computer while you're connected to a computer network (using TCP/IP - there are protocols).

Servers usually have their own IP address and can be accessed through that address. However most people just type in the website they want to go to (ex. [Twitter.com](https://twitter.com)) and DNS does the rest

<small>If you'd like to read more about IP and DNS look at the [extra-reference](./extra-reference/README.md) section</small>

An IP address looks like this: **192.235.5.154**

Just to put it into perspective, IPv4 can hold 4.2 billion unique addresses (2^32). IPv6 can hold 3.4 * 10^38 addresses (2^128).

### What are the differences between Client and Server?

- A "client" is what the user uses on their machine to request information from servers (websites usually).

- A "server" is a computer which handles a client's request (web page, file, video, etc.)

The web browser you're using right now is the "client" on your computer which helps you request web pages like Youtube, Facebook, or Reddit.

The client can be thought of as a customer at a restaurant. They look a menu, decide what they want, and make a request to the waiter (server) who places that order. Some time later the waiter comes back with the meal. The waiter is able to create the meal through the kitchen; when the meal was done the waiter responded to the customer's request with a completed meal.

**Note**: The customer did not go into the kitchen to make their own meal. They trusted that waiter would fulfill their request.

### How the browser gets HTML/CSS from a server?
- Browsers and servers need to interact in a  **fixed** and agreed upon manner
- We can call this a protocol


## HTTP: Hypertext Transfer Protocol

Earlier we talked about [clients and servers](https://github.com/dvcoders/intro-web#what-is-a-client-what-is-a-server). Now, we're going to talk about a *protocol* which is simply a standard for enabling the connection, communication, and data transfer between two places on a network.

To double back to our restaurant example from earlier, there are **four primary actions** in an HTTP request which describe what interactions the client and server are able to have.

| METHOD | MEANING                                                                                                          | RESPONSE                                                                                                                                                                                                  |
|--------|------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| GET    | **Read** some specific data from the server <br>Ex. "Could I have another spoon?"                                     | The server gives the client back the requested data (if it exists). Could be an HTML file, a PDF, or [JSON data](http://learnxinyminutes.com/docs/json/).<br>Ex. "Here is your spoon" Success!     |
| POST   | **Create** some data on the server <br>Ex. "I would like to order the spaghetti"                                       | The client gives the server the data you wish to insert. Usually, this would be in JSON form. <br>Ex. "Your order has been placed" Success!                                                         |
| PUT    | **Update** an existing piece of data <br>Ex. "Could you tell the chef no anchovies in my pasta?"  | The client tells the server **what** needs to be **updated**  Usually with some ID or name, as well as the data. <br>Ex. "Just in time, the chef made your meal extra spicy" Success!          |
| DELETE | **Delete** an existing piece of data <br>Ex. "I would like to cancel my order, you restaurant sucks!" | The client tells the server **what** needs to be **deleted**. This time you only need to give the ID, the server will handle the actual deleting. <br>Ex. "Alright, your order has been canceled" Success! |

### What is JSON

**JSON** stands for *Javascript Object Notation*. It a Data type for OOP in JavaScript.

JSON is the most common **response** from a server. The server will send the information back in JSON format!

Here's some sample JSON - it is based on a `"key"`:`value` pair, which means you access the value by asking for the key!

<small>This is a lot like arrays, except their keys are indexes 0,1,3,etc. And you can have arrays inside of arrays!</small>

``` js
{
  "key": "value",

  "keys": "must always be enclosed in double quotes",
  "numbers": 0,
  "strings": "Hellø, wørld. All unicode is allowed, along with \"escaping\".",
  "has bools?": true,
  "nothingness": null,

  "big number": 1.2e+100,

  "objects": {
    "comment": "Most of your structure will come from objects.",

    "array": [0, 1, 2, 3, "Arrays can have anything in them.", 5],

    "another object": {
      "comment": "These things can be nested inside one another, very useful."
    }
  },
}
```

### What is TLS and HTTPS?

Transport Layer Securtiy - TLS, previously known as SSL, is a method to provide secure, encrypted communications between computers.

Once a secured connection is established between a server and client using TLS, HTTPS is the protocol used for sending and recieving information. HTTPS prevents the interception of data. Initially used for banking and purchases, it is now adopted on many web services (including [dvcoders.com](dvcoders.com).)

#### What is a REST (API)?
A RESTful API is an *architectural style* - no code involved. It simply described how an API should function.

Guess what? HTTP already does the work for us, so we can make a request to an REST API like this:

`http://maps.google.com/api/maps/geocode/json?location=chicago`

REST APIs have **endpoints** which are different parts of the API you can access.

- `/maps`: The Google Maps API
- `/geocode`: The part that deal with Latitude and Longitude (47.54, -86.43)
- `/json`: We would like our data to be in JSON format (vs. XML or Plain Text)
- `?location=chicago`: We're giving the `/geocode` end point a **query parameter**, think of this as giving a function in C++ an argument. We're asking for the geolocation information for Chicago.

REST APIs work in this way, you navigate to different endpoints and ask values and get a response back.
	
#### Responding to request with HTTP

Once a request is recieved and processed by the server, a response is sent back. The response includes a "status code" which is three digit identifier to give information about the response. The server developers decide which status code is appropriate for the situation.

- Codes starting with 1 are informational
- Codes beginning with 2 refer to requested actions have been recieved and are successfully processed
- Codes beginning with 3 mean more action must be taken by the client to continue
- Codes beginning with 4 are client errors
- Codes beginning with 5 are server errors

[http.cat](https://http.cat) hosts cat images corresponding with each status code

If the HTTP request was GET, some data will be returned by the server. This may be:

- HTML
- JSON (a standard for holding data -- often used in API requests)
- XML (another type of data representation)
- Plain text
- Binary data (such as an image file)

Communication with the server allows web pages to serve different content without loading a whole new page. For example, imgur.com scrolls continually. Every time your browser reaches the bottom of the page, a GET request is made and the server returns a new set of images. Sometime this is referred to as "pagination" when content is broken into pages, such as a google search.

#### Some common, but important tools for servers
- Database
- Load balancer
- Message Queue

## What comes after HTTP?

### WebSockets

### Long-Polling technique

## What happens when you click "search" on google.com?

> Check this out on your own time

Some amazing people detailed and described **every single step** from pressing `Enter/Return ⏎` on your keyboard to accessing a server on a CDN.

It's amazing and it's called [what happens when?](https://github.com/what-happens-when) - it's a long read but you should read the entire thing, it's absolutely fascinating!


