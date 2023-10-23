## HTTP 1.1
### Origins
HTTP — Hyper Text Transfer Protocol — is the protocol for almost all data transfer over the internet. Originally developed by Tim Berners-Lee at CERN in 1989, the first usable version of the protocol was created in 1997 and is known as HTTP/1.0. Since then, three subsequent versions of HTTP have been developed: HTTP/1.1 IN 1997, HTTP/2 in 2015, and HTTP/3 in 2022. All three of these versions remain in use, while older versions are obsolete.

### HTTP 1.1 vs HTTP 1.0
- Host header
	- A host header specifies the hostname of the HTTP server the request is being sent to. It's important when routing a message through proxy servers.
	- While HTTP 1.0 did not require a host header, HTPP 1.1 did require it.
- Persistent connections
	- HTTP 1.0 required that each request and response open its own connection. HTTP 1.1 allows for multiple requests and responses over a single connection.
	- Known as a "keep-alive mechanism".
		- Advantages: reduced latency, reduced CPU usage, reduced network congestion
		- Disadvantages: The client must close the connection, or the resources won't be available to other users.
- Continue status
	- HTTP includes a status code `100` "Continue".
	- It allows a client to check if a server can accept a request by sending only the request header
	- Advantages
		- Large requests: For requests like a file upload, the client may want to check if the server can handle the request before transmitting the data
		- Limited bandwidth: Similar to the previous case, but for smaller requests if bandwidth is a concern
		- Server-pre-conditions: The server may rely on the continue mechanism to filter out unwanted requests based on the header alone
		- Streamlining in persistent connections: a client can use "expect: 100-continue" to avoid having to reset a persistent connection.
- New methods
	- Six new methods were added to HTTP 1.1
		- PUT
			- A request to a specific target location on a server that it create or update its state
		- PATCH
			- A request that a target be modified according to the specifications in the request. This allows a partial update and avoids having to transfer a resource in its entirety.
		- DELETE
			- A request for deletion
		- CONNECT
			- A request to initiate a TCP/IP tunnel. 
		- TRACE
			- A request that the target transfer the request that they received in the body of their response, to see if any changes have been made in transport.
		- OPTIONS
			- A request that the target respond with its supported HTTP methods.