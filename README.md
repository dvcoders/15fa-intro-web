## Web Technology Guide

> The internet is not a [series of tubes](https://www.youtube.com/watch?v=f99PcP0aFNE)! 

### What is the internet?

The internet is simply a global connection of computer networks.

Your home network connects to a network in your city, which connect to a larger network in your region, then to other networks in the country, which connect to networks around the world.

Through these connections your computer has connection to other computers. 

Some of these computers are called "servers". Servers are the backbone of the internet, they store content and "serve" them to users around the world. Servers need to more more powerful than the average computer in order to handle up hundreds or millions of requests.

### What is a "client"? What is a "server"?

- A "client" is the tool in which the user interacts with data from servers.

- A "server" is a computer which stores data in order server when someone requests it (web page, file, video, etc.)

The web browser you're using right now is the "client" on your computer which helps you request web pages like Youtube, Facebook, or Reddit.

The client can be thought of as a customer at a restaurant. They look a menu, decide what they want, and make a request to the waiter (server) who places that order. Some time later the waiter comes back with the meal. The waiter is able to create the meal through the kitchen; when the meal was done the waiter responded to the customer's request with a completed meal.

**Note**: The customer did not go into the kitchen to make their own meal. They trusted that waiter would fufill their request.

This request/response model makes the basis for how the client and server interact, called *HTTP* (Hyper Text Transfer Protocol) which will be explained shortly.

### How is information broken down and sent?

To serve or send a web page, file, picture, or video driectly would be very hard! These files can be very large and sending them would take ages!

Sending data requires **three** key things:
  1. Rules for "packaging" data - (breaking into tiny pieces)
  2. An interconnected network to send over - (ex.the internet)
  3. A way to "route" the data to the computer which needs to recieve it - (IP Address)

### What is a packet?

A packet is a tiny piece of the original file which is being sent - (either from the client or to the client).

It's very efficient to break a large file into smaller bits, send them to the their destination computer, and have that computer reassemble them into the orginial file.

Packaging a file can be thought of as cutting a flower vase into pieces and sending them to a friend with instructions on how to reassble the vase. One, you've just saved a lot space in mailing the vase. Two, your friend does all the work reassbling it. Three, it was efficient to send because it was precisely cut and sent with specific instructions.

We've covered how the the internet is structured, but how does the computer sendin the data know *where* it needs to go? That's where IP Addresses come in!

### What are IP Addresses

> What is an HTTP Request?

> What are DNS servers?

> What is HTML and how is it used?

> What is CSS and how is it used?

> What's the difference between static and dynamic web pages?

> What is your browser's Web Inspector (aka Developer Tools) and how can you use it to poke around in a page's HTML?

> What happens when you click "search" on google.com?



