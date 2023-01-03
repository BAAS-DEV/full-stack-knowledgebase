# Services

In a TypeScript API project, a "service" file typically refers to a module that contains business logic for a specific feature or set of related features. Service files are often used to encapsulate logic that would otherwise be duplicated across multiple routes or controllers in the API.

Here's an example of how you might structure a service file in a TypeScript API project:

```Typescript
import { User } from '../models/user';
import { UserRepository } from '../repositories/userRepository';

export class UserService {
  private userRepository: UserRepository;

  constructor(userRepository: UserRepository) {
    this.userRepository = userRepository;
  }

  async createUser(user: User): Promise<User> {
    // Validate the user data
    // ...

    // Save the user to the database
    const savedUser = await this.userRepository.save(user);

    return savedUser;
  }

  async getUserById(id: string): Promise<User | undefined> {
    // Find the user in the database
    const user = await this.userRepository.findById(id);

    return user;
  }
}
```

In this example, the UserService class is a service that handles user-related operations. It has a createUser method that creates a new user and a getUserById method that retrieves a user by their ID. The service depends on a UserRepository to handle the database operations, which is injected into the service through the constructor.

You can then use the service in a route or controller like this:

```Typescript
import { UserService } from '../services/userService';

const userService = new UserService(new UserRepository());

router.post('/users', async (req, res) => {
  const user = req.body as User;
  const createdUser = await userService.createUser(user);
  res.send(createdUser);
});

router.get('/users/:id', async (req, res) => {
  const id = req.params.id;
  const user = await userService.getUserById(id);
  if (user) {
    res.send(user);
  } else {
    res.status(404).send({ message: 'User not found' });
  }
});
```

In this example, the service is used in the POST /users route to create a new user and in the GET /users/:id route to retrieve a user by their ID.

