# HTTP
---
## HTTP 1.0 (Non persistent HTTP)
- Characteristics
	- At most one object sent over [[TCP]] connection
		- Connection then closed
	- Downloading **multiple objects** required **multiple connections**
		- Because "one at a time"
		- Results in performace problems (i.e. takes too damn long to send an item)

- Initial sequence to establish connection:
	- SYN packet = knock knock by client
	- Server sends back a SYN+ACK
	- browsers often open multiple TCP connections to fetch referenced objects
	- as a result, can send multiple requests in a parallel manner, can INTERLEAVE (different from 1.1)

Concerns:
- RTT
	- 2 RTT + file transfer time for non persistent http
	- 1st RTT: client syn + server syn & ack
	- 2nd RTT: client ack + get & server reply

## HTTP 1.1 (Persistent)
- Characteristics
	- Server leaves connection open after sending response
	- **Multiple objects** can be sent over **single TCP connection** between client and server
	- Multiple GET requests sent over the same connection
	- no interleaving, server will handle the requests synchronously
		- #todo but isnt this full duplex?
	- 

Both 1.0 and 1.1 are pull protocols, 
- means client initiates transfer of data
- URL contents sent by server only when requested by browser
	- Eg client receives the html file, and find an embedded image inside
	- client gotta send another request to server for the embedded image

## Requests and response messages
Know header section ends by entering another newline (clrf)
- proxy/intermediate so need to send who to contact in the host

1.0
- GET, POST, **HEAD**
	- The HTTP **HEAD** method requests the **headers** that would be returned if the HEAD request's URL was instead requested with the HTTP GET method.

1.1 
- have 1.0 methods and **PUT** and **DELETE**
	- The HTTP **PUT** request method **creates a new resource** or **replaces a representation of the target resource** with the request payload.
		- The difference between **PUT** and **POST** is that PUT is idempotent: **calling it once or several times successively has the same effect** (that is no side effect), whereas successive identical POST requests may have additional effects, akin to placing an order several times.
	- The HTTP **DELETE** request method deletes the specified resource. 

Another HTTP request, **Conditional GET**, is commonly used in conjunction with [[Web Caching]]

## HTTP 2
- Transmission order of requested objects based on client-specified object priority
- Objects are divided into frames, and frame transmission is interleaved
	- Allows for mitigation of Header-Of-Line (HOL) blocking

## HTTP 3
Problem in 2: 
- packet loss still stalls all object transmissions
- no security over vanilla TCP connection
What it adds:
- Security
- per object error-and congestion-control (more pipelining) over QUIC/**UDP**
	- QUIC is an application layer protocol on top of UDP
	- Allows for more parallelism for app streams multiplexed on the same connection #todo what does that mean?
#networks 