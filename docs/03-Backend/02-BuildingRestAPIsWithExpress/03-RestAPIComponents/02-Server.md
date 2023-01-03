 Here is an example of a simple REST API server using Node.js and Express in a single file:

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

To run this server, you will need to have Node.js and the Express package installed on your system. Then, you can save the file (e.g., as index.js) and run it using the node command:

```
node index.js
```

This will start the server and listen for requests on port 3000. You can then send requests to the server using a tool such as curl or a web browser. For example, you can send a GET request to the / path to see the "Hello World" message:

```curl http://localhost:3000/```
