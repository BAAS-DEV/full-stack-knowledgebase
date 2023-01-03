# Authentication

In a TypeScript API project, you can use JSON Web Tokens (JWTs) to implement authentication.

JWTs are a popular way to securely transmit information between parties. They consist of a header, a payload, and a signature, and are usually encoded as a string in the following format:

```Typescript
xxxxx.yyyyy.zzzzz
```

The header specifies the algorithm used to generate the signature and the type of the token. The payload contains the claims (i.e., statements about an entity) and the metadata. The signature is used to verify that the sender of the JWT is who it claims to be and to ensure that the message wasn't changed along the way.

To use JWTs for API auth in a TypeScript API project, you can follow these steps:

Generate a JWT when a user logs in. The JWT should contain information about the user, such as their ID and username, as well as an expiration time. You can use a library like jsonwebtoken to generate the JWT.

Send the JWT to the client. You can send the JWT in the Authorization header of the response, or in a cookie.

Verify the JWT on subsequent requests. On subsequent requests, the client should send the JWT in the Authorization header or in a cookie. The API can then verify the JWT using the same secret that was used to sign it. If the JWT is valid, the API can allow the request to proceed. If the JWT is invalid or has expired, the API can return an error.

Here's an example of how you might implement API auth with JWTs in a TypeScript API project:

```Typescript
import { Router } from 'express';
import jwt from 'jsonwebtoken';

const router = Router();

router.post('/login', (req, res) => {
  const { username, password } = req.body;
  // Check the username and password
  // ...
  const userId = 123;
  const token = jwt.sign({ userId, username }, 'secret', { expiresIn: '1h' });
  res.send({ token });
});

router.get('/profile', (req, res) => {
  const token = req.headers.authorization;
  try {
    const decoded = jwt.verify(token, 'secret');
    // Allow the request to proceed
  } catch (error) {
    res.status(401).send({ message: 'Invalid token' });
  }
});
```

In this example, the POST /login route generates a JWT when a user logs in and sends it to the client in the response. The GET /profile route verifies the JWT sent by the client in the Authorization header and returns an error if the JWT is invalid.