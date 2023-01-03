# Controllers

In Express, a "controller" is a function that handles a request to an API route. The controller function receives the request object, the response object, and any other arguments that are needed to fulfill the request. It then performs any necessary logic, such as querying a database or calling an external API, and sends a response back to the client using the response object.

Here is an example of an API route with a controller function in Express:

```Typescript 
app.get('/api/users', (req, res) => {
  const users = getUsersFromDatabase();
  res.json(users);
});
```
In this example, the controller function is an anonymous function that is passed to the app.get() method as the second argument. It receives the request object (req) and the response object (res) as arguments. The function queries a database for a list of users and sends the list back to the client as a JSON response using the res.json() method.

You can also define controller functions as named functions and pass them to the API routes as follows:

Copy code
function getUsers(req, res) {
  const users = getUsersFromDatabase();
  res.json(users);
}

app.get('/api/users', getUsers);
This can be useful if you want to reuse the same controller function for multiple routes or if you want to test the controller function separately from the route.