# REST APIs
## 🧠 Understanding REST APIs
### What is a REST API?
**REST** stands for **Representational State Transfer** — it's not a technology, but an **architectural style** for designing networked applications
- REST APIs allow clients (like web or mobile apps) to interact with servers using **standard HTTP methods**
- They return **structured data** (usually JSON or XML) representing resources
- REST promotes **predictable and consistent behaviour** through:
    - Standard methods: `GET`, `POST`, `PUT`, `DELETE`
    - Standard data formats: JSON, XML
- Refers to a group of software architecture design constraints that bring about efficient, reliable, and scalable systems
## 🌐 REST Architecture Overview
### Key Components
- **Client**: The interface used to access data (e.g., web app, mobile app, smartwatch)
- **Datastore**: Where the actual data resides
- **REST API ("Librarian")**: Acts as the intermediary, processing requests and returning responses
### How It Works
- Client sends a request to the REST API
- API processes the request, gathers the necessary data, and formats it
- Response includes:
    - Representation of the data (e.g., JSON)
	    - Returns a unique copy, not the data itself
    - Metadata in the header (e.g., resource ID, timestamp)
- Client parses the response and renders it meaningfully
### Updating Resources
- Clients can modify data using methods like `PUT` or `PATCH`
- The API returns the updated resource and a success message
## 🧩 REST vs Traditional Websites
### Traditional Website
- Each page is a static HTML document
- Navigation involves downloading a new page from the server
- Resource-intensive: every page must be manually created
### RESTful Web Application
- The app is downloaded once and runs in the browser
- Each view represents a state of the application
- Navigation involves sending URI requests for data representing the next state
- The app updates the view without reloading the entire page

___
## 🔒 Six Constraints of REST
- Has to meet these constraints to be considered a RESTful API
### 🧭 Client-Server Architecture
- Constraint ensures proper separation of concerns
- Client manages user interface concerns while the server manages data storage concerns
    - Highly portable system
    - One REST service (server) can serve many different clients and interfaces without caring about their implementation
        - What they look like or what they're doing with the data
### 🧠 Statelessness
- No client context or information, aka 'state', can be stored on the server between requests
- Client is responsible for keeping track of its own session state
- All requests must be self-contained and complete
- If session state is relevant, it must be sent along with the request
    - If it needs to store that state, it must pass it along to a datastore for a specific time
    - Server can pass on an authentication token for a set time as an example
### ⚡ Cacheability
- Storing responses for a set period of time is integral to performance optimisation
- All REST responses must be clearly marked as cacheable or non-cacheable to ensure it works as expected on the client end
    - The REST server would say something like "keep this for 5 days and then forget about it"
### 🏗️ Layered System
- The system must be designed so that the client can't know, and doesn't care, whether it's connected directly to the server or an intermediary like a CDN or mirror
    - Helps with scalability and security
- **CDN (Content Delivery Network)**: A geographically distributed network of servers that deliver content (e.g. images, scripts, HTML) to users based on their location, improving speed and reducing load on the origin server
- **Mirror Server**: A replica of the original server that serves the same content, often used for load balancing, redundancy, or geographic distribution
### 🧬 Code on Demand
- Servers are allowed to transfer executable code like client-side JavaScript and compiled components to the client
- Extends and customises functionality
- Less commonly used
### 🔗 Uniform Interface
- This constraint is broken down into four sub-constraints
#### 🆔 Resource Identification in Requests
- In REST systems on the web, a URI request must specify what resource it is looking for and what format the response should use
    - Show me this in JSON format
    - The datastore can be tabular
        - REST returns a representation of this data (resource) in a different format
#### ✏️ Resource Manipulation Through Representations
- Once a client has a representation of a resource, it can modify or delete the resource
    - Given the right level of access
#### 🧾 Self-Descriptive Messages
- Response message would have media type (e.g. JSON) so it can be reliably parsed etc
#### 🌐 Hypermedia as the Engine of the Application State (HATEOAS)
- Once the client has access to a REST service, it should be able to discover all available resources and methods through the hyperlinks provided
- For example, request a page resource and along with page contents, the returned representation should include hyperlinks to all resources and methods available
    - e.g. you can GET, PUT, PATCH
    - You can access next post (#5), previous post (#3)
- *The REST service describes its own use with every returned resource*

___
## 🌐 How REST Relates to HTTP
- Working with REST APIs you'll most likely send your requests via HTTP
- Not all REST APIs use HTTP protocols, but RESTful ones do

- Nothing says REST must run on HTTP and the web
    - It could run on FTP
- They are just a convenient pairing
- The web platform is what makes it RESTful
## 👥 Who or What Interacts with REST APIs
- Who are the clients and what are they consuming
- A client isn't the human but the website or app itself
- We are the operators of these REST clients
    - Creating and sending requests
    - Receiving and parsing responses
- *Doesn't care who the client is as long as they follow the rules*
- Not all REST APIs are completely open
    - There are limits on who can access what and how many requests can be made in a time period
        - Rate limits
## ⚙️ REST APIs in Action
- www.reqres.in
    - Free example
    - Uses HTTP protocol
        - So any client that uses this protocol can make requests
        - Web browser is one of these so we can type in requests and get a response in the browser
            - `https://reqres.in/api/users`
                - Just displays the data in JSON format
                - No header data and not properly formatted
            - We need a REST client designed for this purpose to make it more readable
                - Postman, VS Code extension, etc.
                    - `Ctrl + Alt + R` to send request from VS Code extension
                    - Contains formatted data with all header data
    - Has documentation on how to use them
        - Requests you can send
        - Example responses also modelled
