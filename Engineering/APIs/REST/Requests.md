# 📤 Requests

## 🧬 Anatomy of a REST Request
- In its most basic form, a REST request has two parts
    - Method
        - One of the standard HTTP operators
            - GET, POST, PUT, PATCH, DELETE, OPTIONS, HEAD
            - See section below for definitions of each method
            - Whether these work depends on the API configuration and the current user's permissions
    - Resource URI
- When you submit a request you can also send along metadata in the request header as seen below

```http
GET /wp-json/wp/v2/posts HTTP/1.1  %% Example WordPress Request URI %%
Host: appsite.dev
Content-Type: application/json
Authorization: Basic dG9t0nBhc3N3b3Jk
Cache-Control: no-cache
```

- For an update request the format becomes more complex as you need to send the data as well
    - This has to match the defined content-type format (e.g. JSON in the example below)
```http
POST /wp-json/wp/v2/posts
Host: appsite.dev
Content-Type: application/json
Authorization: Basic dG9t0nBhc3N3b3Jk
Cache-Control: no-cache

%% Data to match Content-Type defined above %%
{
    "title": "Angela creates a new task generated from the REST API",
    "content": "This is the content for the new post.",
    "author": 10
}

```
## 🔍 Discovery
- `OPTIONS` lets us figure out what resources and methods are available and what we can do with them
    - A good REST API will have this documentation in a human-readable format
## 📦 Resource
- Any information that can be named can be a resource
    - A document or image, a collection of other resources, a non-virtual object (person), etc
- A conceptual mapping to a set of entities, not the entity itself
- Resources can be collections or singletons
    - Does it point at a single item?
## 🪞 Representation
- REST components perform actions on a resource by using a representation to capture the current or intended state of that resource and transferring that representation between components
    - We are referencing a unique copy of that resource and modifying it to suit your specification
    - Not returning the actual data
## 🧾 Methods
- Methods are also known as verbs
- On a web browser we use [📚 HTTP Methods](HTTP.md#📚%20HTTP%20Methods) to tell the server at the other end of the URL what type of request is being sent
    - The most common method is `GET`