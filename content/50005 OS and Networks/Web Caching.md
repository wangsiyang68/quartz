# Web Caching
---
Also known as Proxy Server
Goal: satisfy client request without involving origin server
This is a similar concept to [[DNS caching]] -- save time by caching stuff that has been requested before.

Steps:
- Instead of requesting the origin server, contact the **proxy server** first
- If it proxy server has seen this request before, then proxy server can serve up that request instead of spending more RTTs going to the origin server

Consequences:
- helps to reduce the utilization of network link by sending less requests through the access link into the public internet, instead just resolving them internally within the LAN
- Might need to do some calculations #todo

## Stale data concern
Problem: What if the content was modified on the original server, rendering the copy on the proxy server to be an outdated one?

Solution: When a Proxy server receives an [[HTTP]] request, and it has the result stored locally, it still queries the original server, asking if that particular object was modified since the last time it was requested by the proxy server.

The “Conditional GET” statement has an additional field than a normal GET statement, called the “If-modified-since” field, which specifies the last time when the same request was made.

If the Proxy server gets a 304 – “No Modification” message, it forwards its local copy to the client. A HTTP 304 message does not contain a message body, this is to make it more efficient than to transmit the whole resource/extra material over the wire.
![[httpcache2.png]]
If modification had been there, the Cache forwards the new object, whilst storing it locally along with the date and time it received the new object (so that it can ask the original server later for modifications).
![[httpcache3.png]]


#networks 