# How Does A RESTAPI Work?

The architecture of a REST API (Representational State Transfer API) typically consists of the following components:

### Client:

This is the entity that makes requests to the API. It can be a web browser, a mobile app, a desktop app, or any other type of client.

### Server:

This is the entity that receives requests from the client and returns responses. It typically consists of a web server, a backend server, and a database.

### Resources:

These are the abstract representations of real-world objects or concepts that the API exposes. Each resource has a unique identifier (such as a URL) and can be accessed using a standard set of operations (such as GET, POST, PUT, DELETE).

### Endpoints:

These are the specific URLs that clients use to access resources. For example, an endpoint for a "users" resource might be /users.

### Operations:

These are the standard actions that clients can perform on resources, such as reading, creating, updating, or deleting them. In REST APIs, these actions are typically mapped to HTTP methods, such as GET, POST, PUT, and DELETE.

### Representations:

These are the formats in which resources are presented to clients. In REST APIs, representations are typically sent in the body of an HTTP response or request and use a standard format such as JSON or XML.

Overall, the architecture of a REST API follows a logical hierarchy, with resources organized into collections and subcollections and accessible using a standard set of operations. This makes it easy for clients to understand and interact with the API.