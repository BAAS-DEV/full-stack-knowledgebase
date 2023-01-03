# Create Your First React Component

1: Create the component
First, you will need to create a new file for your component. You can create a new file by right-clicking on the src folder in your project and selecting "New File". Name the file MyComponent.tsx.

Next, open the MyComponent.tsx file in your code editor and add the following code:

```Typescript
import React from 'react';

const MyComponent: React.FC = () => {
  return (
    <div>
      <h1>My First React Component</h1>
      <p>Hello World!</p>
    </div>
  );
};

export default MyComponent;
```

This code creates a new React functional component called MyComponent that returns a simple HTML element with a heading and a paragraph.

2: Import and use the component
Next, open the app.tsx file and import the MyComponent component by adding the following line at the top of the file:

```Typescript
import MyComponent from './MyComponent';
```

Then, you can use the MyComponent component in the app.tsx file by adding the following code:

```Typescript
<MyComponent />
```

This will render the MyComponent component in the app.tsx file.

Example app.tsx file:
```Typescript
import React from 'react';
import MyComponent from './MyComponent';

const App: React.FC = () => {
  return (
    <div>
      <MyComponent />
    </div>
  );
};

export default App;
```

That's it! You have now created your first React app component and rendered it in the app.tsx file.