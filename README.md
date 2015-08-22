## Web Technology Guide

> The internet is NOT a ["series of tubes"](https://www.youtube.com/watch?v=f99PcP0aFNE)! 

This intro-web guide will broadly cover important concepts in how the web works, how people interact with it, and the tools used to create and maintain web pages, APIs, databases, etc.

### What is the internet?

The internet is simply a global connection of computer networks.

Your home network connects to a network in your city, which connect to a larger network in your region, then to other networks in the country, which connect to networks around the world.

Through these connections your computer has connection to other computers. 

Some of these computers are called "servers". Servers are the backbone of the internet, they store content and "serve" them to users around the world. Servers need to more powerful than the average computer in order to handle up hundreds or millions of requests.

### What is a "client"? What is a "server"?

- A "client" is what the user uses on their machine to request information from servers (websites really).

- A "server" is a computer which stores data in order server when someone requests it (web page, file, video, etc.)

The web browser you're using right now is the "client" on your computer which helps you request web pages like Youtube, Facebook, or Reddit.

The client can be thought of as a customer at a restaurant. They look a menu, decide what they want, and make a request to the waiter (server) who places that order. Some time later the waiter comes back with the meal. The waiter is able to create the meal through the kitchen; when the meal was done the waiter responded to the customer's request with a completed meal.

**Note**: The customer did not go into the kitchen to make their own meal. They trusted that waiter would fulfill their request.

This request/response model makes the basis for how the client and server interact, called *HTTP* (Hyper Text Transfer Protocol) which will be explained shortly.

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

**192.235.5.154**

An IP address is a unique number assigned to computer while you're connected to a computer network.

It is assigned by following protocols, *TCP * and *IP*. This protocol is responsible for addressing, routing, and transferring information. You can read more about TCP/IP [here](http://www.thegeekstuff.com/2011/11/tcp-ip-fundamentals/).

That is an example of a IPv4 (32 bit) address, which was an early addresses protocol. There have been so many devices connecting to the internet, that IPv6 (128 bit) needed to be invented to accommodate new devices.

Just to put it into perspective, IPv4 can hold 4.2 x 10^9 unique addresses. IPv6 can hold 3.4 * 10^38 addresses!

### What are DNS servers?

When a user accesses a website like [twitter.com](https://twitter.com), the **Domain Name System** translates the human-readable url twitter.com into an IP Address by doing a **lookup**.

The Domain Name System is maintained by a distributed database system, which uses the client–server model. The nodes of this database are the name servers. 

Each domain has at least one authoritative DNS server that publishes information about that domain and the name servers of any domains subordinate to it. The top of the hierarchy is served by the root name servers, the servers to query when looking up (resolving) a TLD. 

[Source: [Wikipedia](https://en.wikipedia.org/wiki/Domain_Name_System#Name_servers)]

### What is an HTTP Request?


**Todo**

> What is HTML and how is it used?

> What is CSS and how is it used?

> What's the difference between static and dynamic web pages?

> What is your browser's Web Inspector (aka Developer Tools) and how can you use it to poke around in a page's HTML?


### What happens when you click "search" on google.com?

Some amazing people detailed and described **every single step** from pressing `Enter/Return ⏎` on your keyboard to accessing a server on a CDN.

It's amazing and it's called [what happens when?](https://github.com/what-happens-when) - you should read the entire thing, it's absolutely fascinating!

