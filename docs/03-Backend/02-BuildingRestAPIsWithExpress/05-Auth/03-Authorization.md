# Authorization

## RBAC (Example)

In this example, the checkRole function is a middleware that checks the user's role and attaches it to the request object. The router.use middleware attaches the user's role to the request object by verifying the JWT sent in the Authorization header. Then, the routes use the checkRole middleware to allow or deny the request based on the user's role. The admin role has access to all routes, while other roles are not allowed to access any routes.

```Typescript
import { Router } from 'express';

const router = Router();

// Define the roles and permissions
const roles = {
  admin: ['read', 'write'],
  user: ['read']
};

// Check the user's role
const checkRole = (role: string) => {
  return (req, res, next) => {
    if (roles[role]) {
      req.role = role;
      next();
    } else {
      res.status(401).send({ message: 'Unauthorized' });
    }
  };
};

// Attach the user's role to the request object
router.use((req, res, next) => {
  const token = req.headers.authorization;
  try {
    const decoded = jwt.verify(token, 'secret');
    const { role } = decoded;
    req.role = role;
    next();
  } catch (error) {
    res.status(401).send({ message: 'Invalid token' });
  }
});

// Allow or deny the request based on the user's role
router.get('/users', checkRole('admin'), (req, res) => {
  // Allow the request to proceed
});


router.post('/users', checkRole('admin'), (req, res) => {
  // Allow the request to proceed
});

router.get('/users/:id', checkRole('admin'), (req, res) => {
  // Allow the request to proceed
});

router.put('/users/:id', checkRole('admin'), (req, res) => {
  // Allow the request to proceed
});

router.delete('/users/:id', checkRole('admin'), (req, res) => {
  // Allow the request to proceed
});
```

## PBAC (Example)
Policy-based access control (PBAC) is a fine-grained approach to authorization in which policies specify which users or groups are allowed to access which resources. In a TypeScript API project, you can use PBAC to control access to resources based on the policies.

To implement PBAC in a TypeScript API project, you can follow these steps:

Define the policies. First, you need to define the policies that specify which users or groups are allowed to access which resources. For example, you might have a policy that allows users in the "admin" group to access all resources, and a policy that allows users in the "user" group to access only their own resources. You can define the policies in a configuration file or in a database.

Assign users to groups. Next, you need to assign users to groups. You can do this when the user registers for your API or when they log in. You can store the user's group in a database or in a JWT.

Check the policies when a user makes a request. When a user makes a request to your API, you need to check the policies and allow or deny the request based on the policies. You can use middleware to check the policies and attach them to the request object. Then, you can use the policies in your route handlers to allow or deny the request.

Here's an example of how you might implement PBAC in a TypeScript API project:

```Typescript
import { Router } from 'express';

const router = Router();

// Define the policies
const policies = {
  '/users': ['admin'],
  '/users/:id': ['admin', 'user']
};

// Check the policies
const checkPolicies = (policies: string[]) => {
  return (req, res, next) => {
    const { group } = req;
    if (policies.includes(group)) {
      next();
    } else {
      res.status(401).send({ message: 'Unauthorized' });
    }
  };
};

// Attach the policies to the request object
router.use((req, res, next) => {
  const token = req.headers.authorization;
  try {
    const decoded = jwt.verify(token, 'secret');
    const { group } = decoded;
    req.group = group;
    next();
  } catch (error) {
    res.status(401).send({ message: 'Invalid token' });
  }
});

// Allow or deny the request based on the policies
router.get('/users', checkPolicies(policies['/users']), (req, res) => {
  // Allow the request to proceed
});


router.post('/users', checkPolicies(policies['/users']), (req, res) => {
  // Allow the request to proceed
});

router.get('/users/:id', checkPolicies(policies['/users/:id']), (req, res) => {
  // Allow the request to proceed
});

router.put('/users/:id', checkPolicies(policies['/users/:id']), (req, res) => {
  // Allow the request to proceed
});

router.delete('/users/:id', checkPolicies(policies['/users/:id']), (req, res) => {
  // Allow the request to proceed
});
```
