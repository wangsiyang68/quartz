# TCP
---
acts like a pipe
connection oriented service
uses the same port to connect with client?
- multiplexing thing
- what is the difference between the welcoming socket and the client socket?

Some terminology: passive open = server open first to wait for input
its a full duplex communiation, two way information flow AT the same time
- However, it is TCP connection forming is like a race

serverSocket.accept() will return a new socket for communication from server to client
- is it on the same socket as the previous one? or nah #todo  

Widely used in the real world
However, the HTTP/3 is a protocol by Google that builds on [[UDP]] 

#networks 