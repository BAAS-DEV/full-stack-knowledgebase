#  Tokens (JWT)

## How to Implement Tokens

JSON Web Tokens (JWTs) are a popular way to authenticate and authorize users in REST API projects. JWTs are cryptographically signed tokens that contain a payload of claims. Claims are pieces of information about the user, such as the user's ID, name, and role.

To use JWTs in a TypeScript REST API project, you can follow these steps:

1. Install the jsonwebtoken package.

First, you need to install the jsonwebtoken package, which provides functions for creating, signing, and verifying JWTs. You can install it using the following command: npm install jsonwebtoken.

Create a JWT. To create a JWT, you need to specify a payload of claims and a secret. The secret is a secret string that is used to sign the JWT. You can use the sign function from the jsonwebtoken package to create a JWT. Here's an example of how to create a JWT:

```Typescript
import jwt from 'jsonwebtoken';

const payload = {
  id: 1,
  name: 'John',
  role: 'admin'
};

const secret = 'secret';

const token = jwt.sign(payload, secret);
```


Send the JWT in the Authorization header. To authenticate a user, you need to send the JWT in the Authorization header of an HTTP request. The header should have the following format: Authorization: Bearer token. Here's an example of how to send the JWT in an HTTP request:

```Typescript
fetch('/api/users', {
  method: 'GET',
  headers: {
    'Authorization': `Bearer ${token}`
  }
});
```

Verify the JWT on the server. To verify the JWT on the server, you need to use the verify function from the jsonwebtoken package. The verify function takes the JWT and the secret as arguments and returns the payload of claims if the JWT is valid, or throws an error if the JWT is invalid. Here's an example of how to verify the JWT on the server:

```Typescript
import jwt from 'jsonwebtoken';

app.use((req, res, next) => {
  const token = req.headers.authorization;
  try {
    const decoded = jwt.verify(token, 'secret');
    req.user = decoded;
    next();
  } catch (error) {
    res.status(401).send({ message: 'Invalid token' });
  }
});
```
## Access VS Refresh Tokens

Access tokens and refresh tokens are two types of JWTs that are commonly used in REST API projects. Access tokens are short-lived tokens that are used to authenticate and authorize users for a specific period of time, such as 15 minutes or 1 hour. Refresh tokens are long-lived tokens that are used to obtain new access tokens when the current access token expires.

To use access tokens and refresh tokens in a TypeScript REST API project, you can follow these steps:

1. Install the jsonwebtoken package. 

First, you need to install the jsonwebtoken package, which provides functions for creating, signing, and verifying JWTs. You can install it using the following command: npm install jsonwebtoken.

2. Create an access token

To create an access token, you need to specify a payload of claims, a secret, and an expiration time. The secret is a secret string that is used to sign the JWT. The expiration time is the number of seconds after which the access token will expire. You can use the sign function from the jsonwebtoken package to create an access token. Here's an example of how to create an access token:

```Typescript
import jwt from 'jsonwebtoken';

const payload = {
  id: 1,
  name: 'John',
  role: 'admin'
};

const secret = 'secret';

const expiresIn = '1h';

const accessToken = jwt.sign(payload, secret, { expiresIn });
```

3. Create a refresh token

To create a refresh token, you need to specify a payload of claims and a secret. The refresh token does not have an expiration time, so it will not expire unless it is manually invalidated. Here's an example of how to create a refresh token:

```Typescript
import jwt from 'jsonwebtoken';

const payload = {
  id: 1,
  name: 'John',
  role: 'admin'
};

const secret = 'secret';

const refreshToken = jwt.sign(payload, secret);
```

4. Send Access Token to the server


```Typescript
Here's an example of how to send an access token in an HTTP request using the fetch function:

Copy code
import jwt from 'jsonwebtoken';

// ...

const getUsers = () => {
  const token = localStorage.getItem('access_token');
  const headers = {
    'Authorization': `Bearer ${token}`
  };
  return fetch('/api/users', { headers })
    .then(res => res.json());
};
```

In this example, the getUsers function sends a GET request to the /api/users route with the Authorization header set to the access token. The fetch function returns a Promise that resolves with the JSON response from the server.


5. Verify the access token on the server 

To verify the access token on the server, you need to use the verify function from the jsonwebtoken package. The verify function takes the access token and the secret as arguments and returns the payload of claims if the access token is valid, or throws an error if the access token is invalid. Here's an example of how to verify the access token on the server:

```Typescript
import jwt from 'jsonwebtoken';

app.use((req, res, next) => {
  const token = req.headers.authorization;
  try {
    const decoded = jwt.verify(token, 'secret');
    req.user = decoded;
    next();
  } catch (error) {
    res.status(401).send({ message: 'Invalid token' });
  }
});
```
6. Handle expired access tokens.

If the access token expires, the client can send a refresh token request to the server to obtain a new access token. The refresh token request should include the refresh token in the body of the request. The server should verify the refresh token and, if it is valid, create a new access token and send it to the client. Here's an example of how to handle refresh token requests:

```Typescript
import jwt from 'jsonwebtoken';

const refreshTokens: string[] = [];

app.post('/api/refresh', (req, res) => {
  // Get the refresh token from the request
  const { refreshToken } = req.body;

  // Check if the refresh token is valid
  if (!refreshTokens.includes(refreshToken)) {
    return res.status(401).send({ message: 'Invalid refresh token' });
  }

  // Create a new access token
  const payload = {
    id: 1,
    name: 'John',
    role: 'admin'
  };
  const secret = 'secret';
  const expiresIn = '1h';
  const accessToken = jwt.sign(payload, secret, { expiresIn });

  // Send the new access token to the client
  res.send({ accessToken });
});

```

## Full Example Code

```Typescript
import jwt from 'jsonwebtoken';

const refreshTokens: string[] = [];

app.post('/api/login', (req, res) => {
  // Verify the user's credentials
  const { username, password } = req.body;
  const user = users.find(u => u.username === username && u.password === password);
  if (!user) {
    return res.status(401).send({ message: 'Invalid username or password' });
  }

  // Create an access token
  const payload = {
    id: user.id,
    name: user.name,
    role: user.role
  };
  const secret = 'secret';
  const expiresIn = '1h';
  const accessToken = jwt.sign(payload, secret, { expiresIn });

  // Create a refresh token
  const refreshPayload = {
    id: user.id
  };
  const refreshToken = jwt.sign(refreshPayload, secret);

  // Save the refresh token to the database
  refreshTokens.push(refreshToken);

  // Send the access and refresh tokens to the client
  res.send({ accessToken, refreshToken });
});

app.post('/api/refresh', (req, res) => {
  // Get the refresh token from the request
  const { refreshToken } = req.body;

  // Check if the refresh token is valid
  if (!refreshTokens.includes(refreshToken)) {
    return res.status(401).send({ message: 'Invalid refresh token' });
  }

  // Create a new access token
  const payload = {
    id: 1,
    name: 'John',
    role: 'admin'
  };
  const secret = 'secret';
  const expiresIn = '1h';
  const accessToken = jwt.sign(payload, secret, { expiresIn });

  // Send the new access token to the client
  res.send({ accessToken });
});

app.use((req, res, next) => {
  const token = req.headers.authorization;
  try {
    const decoded = jwt.verify(token, 'secret');
    req.user = decoded;
    next();
  } catch (error) {
    res.status(401).send({ message: 'Invalid token' });
  }
});

const getUsers = () => {
  const token = localStorage.getItem('access_token');
  const headers = {
    'Authorization': `Bearer ${token}`
  };
  return fetch('/api/users', { headers })
    .then(res => res.json())
    .then(data => {
      console.log(data);
    })
    .catch(error => {
      console.error(error);
    });
};

getUsers();

const getUsers = () => {
  const token = localStorage.getItem('access_token');
  const headers = {
    'Authorization': `Bearer ${token}`
  };
  return fetch('/api/users', { headers })
    .then(res => res.json())
    .then(data => {
      console.log(data);
    })
    .catch(error => {
      console.error(error);
    });
};

```

In this example, the getUsers function sends a GET request to the /api/users route with the Authorization header set to the access token. The fetch function returns a Promise that resolves with the JSON response from the server. If the request is successful, the then function logs the data to the console. If the request fails, the catch function logs the error to the console.