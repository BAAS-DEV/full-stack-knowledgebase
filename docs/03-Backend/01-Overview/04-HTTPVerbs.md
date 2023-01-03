# HTTP Verbs

In HTTP (Hypertext Transfer Protocol), there are several verbs, or methods, that can be used to specify the desired action for a request. Here is a brief overview of each of the HTTP verbs:

⭐ GET: The GET verb is used to retrieve a resource from the server. It should not have any side effects (such as modifying data on the server) and is idempotent, meaning that it can be safely repeated without changing the result.

HEAD: The HEAD verb is similar to GET, but it only retrieves the HTTP headers of a response, not the response body.

⭐ POST: The POST verb is used to create a new resource on the server. It typically includes data in the request body that is used to create the resource.

⭐ PUT: The PUT verb is used to update an existing resource on the server. It typically includes data in the request body that is used to update the resource.

⭐ DELETE: The DELETE verb is used to delete a resource from the server.

CONNECT: The CONNECT verb is used to establish a tunnel to the server for the purpose of SSL (Secure Sockets Layer) encryption.

OPTIONS: The OPTIONS verb is used to describe the communication options for the target resource. It can be used to determine which HTTP methods are supported by the server.