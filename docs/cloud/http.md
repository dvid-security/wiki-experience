# HTTP

The **Hypertext Transfer Protocol** (HTTP) is a foundational protocol of the World Wide Web, enabling communication between clients (such as web browsers) and servers. It is an application-layer protocol designed for transmitting hypermedia documents, such as HTML, images, and videos. HTTP follows a request-response model, where clients send requests, and servers return responses.

HTTP is stateless, meaning that each request from a client to a server is processed independently, with no memory of previous interactions unless explicitly managed using mechanisms like cookies or session storage.

## HTTP versions

Here are the different HTTP versions with their release dates:

- HTTP/0.9 (1991): The first version, focused on transferring raw HTML content. Supported only GET requests and lacked headers or metadata.
- HTTP/1.0 (1996): Introduced metadata (headers), support for POST and HEAD methods, and status codes. Each request required a separate TCP connection.
- HTTP/1.1 (1997): Introduced persistent connections (keep-alive), chunked transfer encoding, and pipelining. Became the most widely used version for decades.
- HTTP/2 (2015): Focused on performance improvements, such as multiplexing (sending multiple requests over a single connection), header compression, and prioritization.
- HTTP/3 (2020): Builds upon HTTP/2 but replaces TCP with QUIC, a protocol based on UDP, to reduce latency and improve connection resilience.

## How HTTP Works

HTTP operates on a client-server model:

- Client: Initiates the communication by sending an HTTP request. Examples: Web browsers (e.g., Chrome, Firefox), mobile apps, or API clients.
- Server: Processes the request and sends back an HTTP response containing the requested resource or an error message.

### Key Components of an HTTP Request

An **HTTP request** consists of:

- Request Line: Specifies the HTTP method, target resource (URL), and protocol version (e.g., `GET /index.html HTTP/1.1`).
- Headers: Metadata about the request (e.g., `User-Agent, Host, Accept`).
- Body: (Optional) Contains data sent with the request, such as form submissions or JSON payloads.

### Key Components of an HTTP Response

An **HTTP response** consists of:

- Status Line: Indicates the protocol version, status code, and status message (e.g., `HTTP/1.1 200 OK`).
- Headers: Metadata about the response (e.g., `Content-Type, Content-Length, Server`).
- Body: The content being returned (e.g., HTML, JSON, or images).

### HTTP Methods

HTTP defines several methods for different types of actions:

- `GET`: Retrieves data from a server.
- `POST`: Submits data to a server for processing (e.g., form data).
- `PUT`: Updates or replaces a resource on the server.
- `DELETE`: Deletes a resource on the server.
- `HEAD`: Similar to `GET` but retrieves only headers, not the body.
- `OPTIONS`: Describes the communication options for the target resource.
- `PATCH`: Partially updates a resource on the server.
- `TRACE`: Echoes the received request for diagnostic purposes.
- `CONNECT`: Establishes a tunnel for communication, often used with HTTPS.

### HTTP Status Codes

HTTP uses standardized status codes to indicate the outcome of a request:

- 1xx: **Informational**
	- 100 Continue: Request received, continue to send.
	- 101 Switching Protocols: Server is switching to a new protocol.

- 2xx: **Success**
	- 200 OK: Request succeeded.
	- 201 Created: Resource successfully created.
	- 204 No Content: Request succeeded, no content returned.

- 3xx: **Redirection**
	- 301 Moved Permanently: Resource has a new permanent URL.
	- 302 Found: Temporary redirection.
	- 304 Not Modified: Resource not modified since last requested.

- 4xx: **Client Errors**
	- 400 Bad Request: Invalid request syntax.
	- 401 Unauthorized: Authentication required.
	- 403 Forbidden: Access to the resource is denied.
	- 404 Not Found: Resource not found.

- 5xx: **Server Errors**
	- 500 Internal Server Error: Server encountered an error.
	- 502 Bad Gateway: Invalid response from an upstream server.
	- 503 Service Unavailable: Server is temporarily unavailable.

### Features of HTTP

Here are the main features and "charcteristics" of HTTP:

- **Statelessness**: HTTP does not retain session information, simplifying protocol design. However, this requires mechanisms like cookies or tokens for session management.
- **Flexible Content Handling**: HTTP supports various content types (e.g., HTML, JSON, XML, images, videos) via the Content-Type header.
- **Extensibility**: Custom headers and methods can be added to support new functionalities.
- **Security (HTTPS)**: HTTPS is the secure version of HTTP that uses SSL/TLS to encrypt communication, ensuring confidentiality, integrity, and authentication.

## HTTP in everyday use

As aleady said, the HTTP protocol is widely used on the web. Here are some examples of usage:

- **Web Browsing**: Browsers use HTTP to fetch and render web pages.
- **APIs**: RESTful APIs rely on HTTP for communication between clients and servers. **This will be particularly explored in the cloud trainings**.
- **File Downloads**: Many file transfer services use HTTP as the underlying protocol.
- **IoT Devices**: Internet-connected devices often use HTTP to send and receive data. **This will be particularly explored in the trainings**.