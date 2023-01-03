# Getting and Saving JWTs for Requests

To log in, you will need to create a login form that sends the user's credentials to the server. When the server receives the credentials, it should verify them and send a JWT back to the client if they are correct. You can store the JWT in the browser's local storage using the localStorage API.

### Get JWT from API, and Set to Local Storage
Here is an example of a login function that sends a POST request to the server with the user's credentials and stores the JWT in the browser's local storage:

```Typescript
import axios from 'axios';

async function login(email: string, password: string) {
  const response = await axios.post('https://my-api.com/login', {
    email,
    password,
  });
  const { token } = response.data;
  localStorage.setItem('jwt', token);
}
```

On the server, you will need to verify the JWT and allow access to the protected route or resource if it is valid. You can use the jsonwebtoken package to verify the JWT and retrieve the user's information from it.