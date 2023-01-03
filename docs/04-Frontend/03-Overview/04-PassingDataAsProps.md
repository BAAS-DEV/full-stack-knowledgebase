# Props for Passing Data

Step 1: Define the props type
First, you will need to define the type of the props that you want to pass to the child component. You can do this by creating an interface for the props.

For example, let's say you want to pass a message prop from the parent component to the child component. You can define the props type as follows:

```Typescript
interface ChildProps {
  message: string;
}
```

Step 2: Create the child component
Next, you will need to create the child component and specify the props type using the interface that you defined.

Here is an example of a child component that accepts a message prop:

```Typescript
import React from 'react';

interface ChildProps {
  message: string;
}

const Child: React.FC<ChildProps> = (props) => {
  return (
    <div>
      <p>{props.message}</p>
    </div>
  );
};

export default Child;
```

Note that the Child component is a functional component and it uses the React.FC generic type to specify the props type. The props are passed to the component as an argument and can be accessed using the props object.

Step 3: Pass the props to the child component
Now that you have defined the props type and created the child component, you can pass the props from the parent component to the child component.

Here is an example of a parent component that passes a message prop to the Child component:

```Typescript
import React from 'react';
import Child from './Child';

const Parent: React.FC = () => {
  return (
    <div>
      <Child message="Hello from the parent!" />
    </div>
  );
};

export default Parent;
```

To pass the props, you can simply include the props as attributes of the child component element. In this example, the message prop is passed to the Child component as an attribute with the value "Hello from the parent!".