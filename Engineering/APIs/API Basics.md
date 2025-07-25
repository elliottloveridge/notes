# 🔌 API Basics
## What is an API?
- An Application Programming Interface is a set of rules and tools that allow software to interact with other software or hardware
- REST APIs expose resources via URIs and allow interaction using HTTP verbs
## Example Interactions
- `GET /articles` → Retrieve a list of articles
- `DELETE /documents/123` → Remove a document
## 🔗 URI vs URL vs URN
### URI (Uniform Resource Identifier)
- A generic identifier for a resource
- Can be a URL, URN, or other scheme
- Examples:
    - `https://restful.dev/posts/5`
    - `mailto:morten@example.com`
    - `tel:+1-888-555-1212`
### URL (Uniform Resource Locator)
- A type of URI that includes the method of access
- Examples:
    - `https://example.com` → uses HTTPS protocol
    - `ftp://files.example.com` → uses FTP protocol
### URN (Uniform Resource Name)
- A name-based identifier for a resource
- Doesn’t specify how to access it
- Example: `urn:isbn:0451450523`
___
## 🔐 Authorisation and Authentication
- Most REST APIs provide levelled access
    - Most users can submit GET requests
    - Fewer users can submit PUT, PATCH, and DELETE requests