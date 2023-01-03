# Basic REST Server

1.  Install Node.js and create a new project. You will need to install Node.js on your computer to be able to use it. Then, create a new directory for your project and run the following to initialize a new Node.js project.

    ```
    npm init 
    ```

2. Next, Install Express. To use Express, you will need to install it as a dependency for your project. Run the following command to install it:

    ```Typescript
    npm install express
    // Create an Express app in your project's entry point (e.g., index.js)
    ```
3. Import the express package and create a new instance of the Express class:

    ```Typescript
    import express from 'express';
    const app = express();
    ```

4. To define a route, you can use one of the routing methods provided by the framework, such as 

```Typescript 
app.get()
app.post() 
app.put()
app.delete() 
```
    etc. These methods take two arguments: a path and a callback function. The callback function will be executed when the specified path is requested using the corresponding HTTP method.
    For example, the following code defines a route that responds to a GET request to the / path with a "Hello World" message:

```Typescript
app.get('/', (req, res) => {
  res.send('Hello World');
});
```

5. To start the server, you can call the app.listen() method and pass in the port number to listen on. For example:

```Typescript
app.listen(3000, () => {
  console.log('Server is listening on port 3000');
});
```

Then, in your package.json file, under the area ```scripts``` add 
```JSON
"dev":"nodemon"
```

6. Start your server in development mode by entering in your terminal:
 <br />
```Bash
npm run dev
```

That's it! These are the basic steps for building a REST API server using Node.js and Express. Of course, you can add more routes, middleware, and other functionality as needed to build a fully-featured API.

----

Full Code: 

```Typescript
import express from 'express';

const app = express();

app.get('/', (req, res) => {
  res.send('Hello World');
});

app.listen(3000, () => {
  console.log('Server is listening on port 3000');
});
```
