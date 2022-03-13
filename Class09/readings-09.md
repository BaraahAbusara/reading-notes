# Class-09 : WRRC and Java
***

In this file I will be summarizing what I have learnt in class-09 reading notes which included the following resources : 
- [Review: High-level HTTP](https://dev.to/dangolant/things-i-brushed-up-on-this-week-the-http-request-lifecycle-).
- [Java HTTP Request example](https://www.baeldung.com/java-http-request).

## Review: High-level HTTP 
***
### Step 1: Local Processing
1. The broswer extracts the protocol of our URL.
![browser ectracting the protocol from the URL](./9hs9qfv7srg4t4swiw7o.gif)
2.  The browser looks for the IP adress  through its own cache of recently requested URLs, the operating system’s cache of recent queries, the router’s cache, and the DNS cache.

### Step 2: Resolve an IP
resolving an IP address from a DNS server includes many plans if a plan has failed : 
- looking up in the cash memory, if it was not found the server will stop the DNS request using UDP3. 
- the request will travel many network devices to reach its target DNS server, which is probably going to reach along the shortest path.
- once the server recieves the request it starts looking for the address included in the request hostname to send as a response ,but if it wasn't found it passes the request to another DNS server until one of them finds an address and send it in the response , other wise the server will return a failure and the browser will return an error. 
### Step 3: Establish a TCP Connection
Now the client has the IP address but it needs to open a TCP connection to send an HTTP request as follows in the picture:
![TCP Three way handshake](https://packetsdontlie.gonzalomurillo.com/wp-content/uploads/2018/10/3-wayhandshake.png)
This data should be exchanged before exchanging actual data so we insure that it is a safe exchange. 

### Step 4: Send an HTTP Request
The request consists of :
- request line : a line that indicates the HTTP method, the resource being requested, and the protocol version.
- request header : is made up of pairs in the form name:value and which is the only mandatory field in an HTTP request, the Host which contains the domain and port that the request is being sent to (domain.com:8080).

- request body : it is an optional field, but it sometimes contains form data or JSON.

Once the server receives the request, processes it, and finds the resource being requested, it generates an HTTP response which also contains a request line, request headerand a body .The status line contains an HTTP status code indicating the success, failure, or error-state of the request along with a "reason message" that provides detail.

Once the response is generated, the server responds to the request and data starts loading packet by packet. 

### Step 5: Tearing Down and Cleaning Up
![ Four Way Handshake process](https://2.bp.blogspot.com/_AamnZyf3C_A/TBvQMRNz1GI/AAAAAAAAAYs/fvkbAkc1LOY/s1600/tcp+4+way+handshake.png) 

after processing the four way handshake the browser starts proccessing the recieved data accourding to its type and render it.
which means that we finally see what we are looking for in our browser. 

## Java HTTP Request example
***
Using the built-in `HttpUrlConnection` class we will know **how to present HTTP requests in Java**.
in the resources [link](https://www.baeldung.com/java-http-request) you can find how to create a request , set its parameters and headers , configure timeouts , handel cookies and redirects , read the response for a successful and failed requests and how to build a full response.

but for me in this level I will focude on how to create a request . 

### Create a request : 

```
URL url = new URL("http://example.com");


//this method creats a connection object but does not establesh it yet.  
HttpURLConnection con = (HttpURLConnection) url.openConnection();  

// we can use GET, POST, HEAD, OPTIONS, PUT, DELETE, TRACE methods   
con.setRequestMethod("GET"); 

```
