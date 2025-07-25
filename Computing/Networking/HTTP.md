# HTTP
## What is HTTP?
- HTTP is the protocol used to access hypertext documents on the internet
    - Sits alongside other protocols like SMTP for email, instant messaging (IM) services, etc
## 📚 HTTP Methods
- Below are the common types of HTTP methods
	- **GET**: Retrieve a resource without modifying it
	- **POST**: Create a new resource
	- **PUT**: Replace an existing resource entirely
	- **PATCH**: Partially update an existing resource
	- **DELETE**: Remove a resource
		- Can only be applied to singleton [📦 Resource](Requests.md#📦%20Resource)
	- **OPTIONS**: Discover what methods and operations are supported by the server for a given resource
	- **HEAD**: Same as `GET` but only retrieves the headers, not the body
## 📥 HTTP Response Types
- HTTP response codes indicate the outcome of a request made to a REST API
- They are grouped into categories based on the first digit of the code
### ℹ️ 1xx — Informational
	Rarely Used
- **100 Continue**: The initial part of the request has been received and the client should continue with the rest
- **101 Switching Protocols**: The server is switching to a different protocol as requested by the client
- **102 Processing**: The server has received and is processing the request, but no response is available yet (used in WebDAV)
### ✅ 2xx — Success
- **200 OK**: The request was successful and the server returned the requested data
- **201 Created**: The request was successful and a new resource was created
- **204 No Content**: The request was successful but there is no content to return
### 🔁 3xx — Redirection
- **301 Moved Permanently**: The resource has been moved to a new URL permanently
- **302 Found**: The resource is temporarily located at a different URL
- **303 See Other**: Similar to 302
- **304 Not Modified**: The resource has not changed since the last request
- **307 Temporary Redirect**
- **308 Resume Incomplete**
### ⚠️ 4xx — Client Errors
- **400 Bad Request**: The request was malformed or invalid
- **401 Unauthorized**: Authentication is required or has failed
- **403 Forbidden**: The server understood the request but refuses to authorise it
- **404 Not Found**: The requested resource could not be found
- **405 Method Not Allowed**: The HTTP method used is not supported for this resource
- **429 Too Many Requests**: The user has sent too many requests in a given time (rate limiting)
### ❌ 5xx — Server Errors
- **500 Internal Server Error**: A generic error occurred on the server
- **502 Bad Gateway**: The server received an invalid response from an upstream server
- **503 Service Unavailable**: The server is currently unavailable (e.g. overloaded or down for maintenance)
- **504 Gateway Timeout**: The server did not receive a timely response from an upstream server
