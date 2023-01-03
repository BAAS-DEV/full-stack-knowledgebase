# External State (Using React-Redux)

## External State Management - Overview

External state management libraries are commonly used in React projects to help manage the state of the application. These libraries provide a way to centralize the management of state, and make it easier to reason about how the state is being modified and used in the application.

There are several reasons why you might consider using an external state management library in a React project:

- Your application has a lot of state that needs to be shared between components, and you want a centralized way to manage it.
- You want to enforce a unidirectional data flow in your application, to make it easier to understand how the state is being modified.
- You want to be able to easily track changes to the state, and undo/redo state changes.
- You want to be able to easily test your application, by being able to manipulate the state in a controlled way.
- It is generally a good idea to use an external state management library if your application is growing in complexity, and you need a way to better manage the state of your application.

There are several factors to consider when deciding which state management library to use:

- Does the library fit the needs of your application? Each library has its own set of features and trade-offs, so you should choose the one that best fits your needs.
- Is the library well-maintained and widely used? A library that is well-maintained and has a large user base is more likely to be reliable and have good documentation and support.
- Is the library easy to learn and use? If you are new to state management libraries, you may want to choose a library that has a simpler API and is easier to learn.

Ultimately, the choice of which state management library to use will depend on the specific needs of your application, and the trade-offs that you are willing to make.

## React-Redux

React-Redux is a library that integrates Redux, a popular state management library, with React. It provides a set of APIs for managing state in a React application using Redux.

Redux is a state management library that allows you to store all of your application's state in a single, immutable object, and provides a set of functions for updating the state in a predictable way. This makes it easy to manage complex state updates, and helps ensure that your application's state is consistent and easy to understand.

To use Redux with React, you will need to install the react-redux library. You can do this using npm or yarn:

```Typescript
npm install react-redux
or
yarn add react-redux
```

Once you have installed react-redux, you can start using it in your React application.

To use react-redux in a React application, you will need to create a Redux store and a root reducer. The store is an object that holds the application's state, and the reducer is a function that takes in the current state and an action, and returns the next state.

Here's an example of how to create a store and a root reducer in a React application:

```Typescript
import { createStore } from 'redux';

const initialState = {
  count: 0,
};

const rootReducer = (state = initialState, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return {
        count: state.count + 1,
      };
    case 'DECREMENT':
      return {
        count: state.count - 1,
      };
    default:
      return state;
  }
};

const store = createStore(rootReducer);
```

In this example, the createStore function is called with the root reducer as an argument to create a store. The root reducer is a function that takes in the current state and an action, and returns the next state based on the action type.

Once you have created the store, you can use the Provider component from react-redux to provide the store to your React components. Here's an example of how to do this:

```Typescript
import React from 'react';
import { Provider } from 'react-redux';

const App = () => (
  <Provider store={store}>
    {/* your React components go here */}
  </Provider>
);
```

In this example, the Provider component is wrapped around the root component of the application, and takes a "store" prop with the Redux store as its value. This makes the store available to all of the components in the application.

To access the state from a React component, you can use the useSelector hook from react-redux. This hook takes a selector function as an argument, which is a function that takes in the state and returns the data that you want to access.

Here's an example of how to use the useSelector hook in a React component:

```Typescript
import React from 'react';
import { useSelector } from 'react-redux';

const Count = () => {
  const count = useSelector((state) => state.count);

  return <div>{count}</div>;
};
```

In this example, the useSelector hook is called with a selector function as an argument. The selector function takes in the state and returns the "count" value from the state. The hook returns the value of "count", which is then rendered by the component.

To update the state from a React component, you can use the useDispatch hook from react-redux. This hook returns a function that you can call to dispatch an action to the store.

Here's an example of how to use the useDispatch hook in a React component:

```Typescript
import React from 'react';
import { useDispatch } from 'react-redux';

const IncrementButton = () => {
  const dispatch = useDispatch();

  const handleClick = () => {
    dispatch({ type: 'INCREMENT' });
  };

  return <button onClick={handleClick}>Increment</button>;
};
```

In this example, the useDispatch hook is called to get the dispatch function from the store. The component renders a button with an onClick event handler that calls the dispatch function when clicked. The dispatch function is called with an action object that has a "type" property of "INCREMENT", which will cause the root reducer to increment the "count" value in the state.

Overall, React-Redux is a powerful tool for managing state in a React application using Redux. It provides a set of APIs for accessing and updating the state, and helps ensure that your application's state is consistent and easy to understand.