# Managing Auth State With Context State

1. First, create a new file for your authentication context. In this file, import the createContext function from the react package and use it to create a new context object. You will also need to create a context provider component that will hold the authentication state and provide it to the rest of the app.

```Typescript
import { createContext } from 'react';

const AuthContext = createContext();

const AuthProvider = (props) => {
  // ...
};

export { AuthContext, AuthProvider };
```

2. In the provider component, define the authentication state and any necessary functions for updating the state. For example, you might want to include a loggedIn boolean, a user object, and functions for logging in and out. You will also need to wrap the provider component with the AuthContext.Provider component and pass the state and functions as values to the value prop.
```Typescript
const AuthProvider = (props) => {
  const [loggedIn, setLoggedIn] = useState(false);
  const [user, setUser] = useState(null);

  const login = (user) => {
    setLoggedIn(true);
    setUser(user);
  };

  const logout = () => {
    setLoggedIn(false);
    setUser(null);
  };

  return (
    <AuthContext.Provider value={{ loggedIn, user, login, logout }}>
      {props.children}
    </AuthContext.Provider>
  );
};
```

3. In your root component, import the AuthProvider component and wrap your app in it. This will make the authentication state and functions available to the rest of the app.

```Typescript
import { AuthProvider } from './auth-context';

const App = () => (
  <AuthProvider>
    <div>
      {/* rest of your app goes here */}
    </div>
  </AuthProvider>
);
```
4. To access the authentication state and functions in a child component, you will need to wrap the component with the AuthContext.Consumer component and pass a render prop function that receives the value from the context as an argument.
```Typescript
import { AuthContext } from './auth-context';

const MyComponent = () => (
  <AuthContext.Consumer>
    {(value) => {
      const { loggedIn, user, login, logout } = value;
      // use the loggedIn, user, login, and logout values here
    }}
  </AuthContext.Consumer>
);
```