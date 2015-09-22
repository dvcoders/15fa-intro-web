#Intro-Web Reference

## What is the internet?

The internet is simply a global connection of computer networks.

Your home network connects to a network in your city, which connect to a larger network in your region, then to other networks in the country, which connect to networks around the world.

Through these connections your computer has connection to other computers. 

Some of these computers are called "servers". Servers are the backbone of the internet, they store content and "serve" them to users around the world. Servers need to more powerful than the average computer in order to handle up hundreds or millions of requests.

## Client

### HTML

HyperText Markup Language is a markup language used to add structure and content to webpages.


HTML is composed of a series of tags such as `<p>` (paragraph) and `<img>` (image) to indicate different types of content. The `<div>` tag is used to break up groups of content.
  

Your browser interprets the tags and uses them to display the content how it is specified.


HTML follows the Document Object Model (DOM) convention. The DOM is a "tree" or "hierarchy" composed of objects. HTML elements are objects in the tree. Tags such as `<p>` and `<img>` specify elements. The DOM is called a "tree" because elements can be "children" of an element, or "parents" of elements as well.

![DOM Tree](http://www.w3schools.com/js/pic_htmltree.gif)


(Image courtesty of w3schools.com)

### CSS

Cascading Style Sheets is a language used to design the appearance and formatting of a webpage.

### Client (Browser)

#### How the browser works

#### How the browser gets HTML/CSS from the server

## Server


### How is information broken down and sent?

To serve or send a web page, file, picture, or video directly would be very hard! These files can be very large and sending them would take ages!

Sending data requires **three** key things:
  1. Rules for "packaging" data - (breaking into tiny pieces)
  2. An interconnected network to send over - (ex.the internet)
  3. A way to "route" the data to the computer which needs to receive it — (IP Address)

### What is a packet?

A packet is a tiny piece of the original file which is being sent — (either from the client or to the client).

It's very efficient to break a large file into smaller bits, send them to the their destination computer, and have that computer reassemble them into the original file.

Packaging a file can be thought of as cutting a glass into pieces and sending them to a friend with instructions on how to erasable the vase. One, you've just saved a lot space in mailing the glass for your friend to drink with. Two, your friend does all the work reassembling it. Three, it was efficient to send because it was precisely cut and sent with specific instructions.

We've covered how the the internet is structured, but how does the computer sending the data know *where* it needs to go? That's where IP Addresses come in!

### What is an IP Address?

An IP address is a unique number assigned to computer while you're connected to a computer network.

An IP address is assigned by following protocols, *TCP * and *IP*. This protocol is responsible for addressing, routing, and accessing information.

An IP address looks like this: **192.235.5.154**

That is an example of a IPv4 (32 bit) address, which was an early addresses protocol. There have been so many devices connecting to the internet, that IPv6 (128 bit) needed to be invented to accommodate new devices.

Just to put it into perspective, IPv4 can hold 4.2 billion unique addresses. IPv6 can hold 3.4 * 10^38 addresses!

### What happens when you click "search" on google.com?

Some amazing people detailed and described **every single step** from pressing `Enter/Return ⏎` on your keyboard to accessing a server on a CDN.

It's amazing and it's called [what happens when?](https://github.com/what-happens-when) - you should read the entire thing, it's absolutely fascinating!

#### What is REST API.
	
#### Incoming server requests (from client POST, GET, DELETE, PUT.)
	
#### Using HTTP to respond to requests

		- Status Code (https://http.cat)

#### What are the differences between Client and Server?

- A "client" is what the user uses on their machine to request information from servers (websites really).

- A "server" is a computer which stores data in order server when someone requests it (web page, file, video, etc.)

The web browser you're using right now is the "client" on your computer which helps you request web pages like Youtube, Facebook, or Reddit.

The client can be thought of as a customer at a restaurant. They look a menu, decide what they want, and make a request to the waiter (server) who places that order. Some time later the waiter comes back with the meal. The waiter is able to create the meal through the kitchen; when the meal was done the waiter responded to the customer's request with a completed meal.

**Note**: The customer did not go into the kitchen to make their own meal. They trusted that waiter would fulfill their request.

This request/response model makes the basis for how the client and server interact, called *HTTP* (Hyper Text Transfer Protocol) which will be explained shortly.

#### Some common, but important tools for server
		- Database
		- Load balancer
		- Message Queue

## Hypertext Transfer Protocol

### What is SSL

### Why is SSL important

### Basic architecture of SSL

## What comes after HTTP?

### Websocket

### Long-Polling technique