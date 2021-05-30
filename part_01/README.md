# Web development fundamentals

[Languages and tools of web development](#languages-and-tools-of-web-development)  
[How the web works](#how-the-web-works)  

## Languages and tools of web development

Every web site has two parts: a **front-end** and **back-end**. The front-end is what the user sees in the browser and interacts with. The back-end is everything that happens behind the scenes so that the web page can do what it does. Developers who build both front and back-end systems are called **full-stack** developers.

To build front-end we use HTML, CSS, and JavaScript. **HTML** stands for *Hypertext Markup Language* and is used to defined the building blocks of the webpage. HTML is not a programming language, but a mark-up language. **CSS** stands for *Cascading Stylesheet* and is used to style the web page. It controls the aesthetics of the page. CSS is not a programming language either, but a styling language. **JavaScript** is used to control the behavior of the webpage and add functionality to it.

In order to build webpages faster, front-end developers use a variety of frameworks and libraries. Currently, the most popular ones are **React** (library), **Angular** (framework), and **Vue** (framework).

To build the back-end services that websites use, developers use a wide variety of tools. Some of the most popular programming languages are Java, Python, Go, C#, and much more.

## How the web works

The address that you type in the browser's address-bar is called a **URL** (*Uniform Resource Location*). A resource can be anything that is stored and accessible through the web like web pages (called HTML documents), images, video and audio files, fonts, etc. One you type an address in the address-bar and hit enter two actors start interacting. One the one side it's the **client** (your browser), on the other side is the **web server** (or server for short). This is why it's called the client-server model.

In this model, the client will request a service, and the server will provide that service. Requests for services are standardize and the clients use a format (or protocol) called **HTTP** (*Hypertext Transfer Protocol*). You can think of HTTP as the language that clients and servers use to talk to each other. Another version of this protocol is called **HTTPS** (*Hypertext Transfer Protocol Secure*). It's just like HTTP, but with encryption.

For example, here is the message that a browser would send to a server to request a webpage:

``` text
GET /index.html HTTP/1.1
Host: www.codewithmosh.com
Accept-Language: en-us
```

The first line is just telling the server that it wants to `GET` a file called `index.html` using `HTTP` version `1.1`. `index.html` usually represent the homepage of websites. The second line displays the `host`. And the third line tells the server that language that the client can accept.

Once the server receives the message, it will fetch the requested document and send it back to the client.

The message that the client sends to the server is called a **REQUEST**, and the message that the server sends to the client in called a **RESPONSE**. The response to our example request could look something like this:

``` text
HTTP/1.1 200 OK
Date: 1 Jan 2021 09:00
Content-Type: text/html

<!DOCTYPE html>
<html>
  ...
</html>
```

The first line shows the version of HTTP used followed by a status code. `200 OK` means that the message was successfully received. Then in the second line comes the date and time of the response. The third line tells the client what type of content it's sending. After that comes the actual content.

Once the browser gets the content of the message, it will construct a **DOM** (*Document Object Model*). This is just a tree that represent the elements in the HTML document. As the browser is reading the document and building the DOM, it will discover references to other resources (like images, videos, etc). For each resource that it discovers, it will send an HTTP request to the server asking for the resource to be fetched. Many of the requests are sent in parallel so that the page loads faster.

Once the client has all the necessary resources, it will **Render** (display) the HTML document to the user.
