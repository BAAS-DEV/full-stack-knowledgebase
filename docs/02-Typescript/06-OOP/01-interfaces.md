# Interfaces 

An interface in TypeScript is a way to define a contract for the shape of an object. It specifies the types of properties that an object should have, and allows you to enforce that structure in your code.

Here's an example of how you might define an interface in TypeScript:

```Typescript
interface Person {
  name: string;
  age: number;
}
```

This interface defines a Person object with two properties: a name of type string, and an age of type number.

You can use an interface to create a new object like this:

```Typescript
const person: Person = {
  name: 'John',
  age: 30
};
```

If you try to create an object that doesn't match the shape defined in the interface, you'll get a TypeScript error:

```Typescript
const person: Person = {
  name: 'John'
};

// Error: Property 'age' is missing in type '{ name: string; }' but required in type 'Person'.
```

You can also use interfaces to define the type of function arguments and return values. For example:

```Typescript
interface Calculator {
  (a: number, b: number): number;
}
const add: Calculator = (a, b) => a + b;

console.log(add(1, 2)); // 3
```

In this example, the Calculator interface defines a function that takes two number arguments and returns a number. The add function is declared with the Calculator type, so it must match the contract defined in the interface.

You can also use interfaces to define the shape of a class. For example:

```Typescript
interface Animal {
  name: string;
  makeSound(): void;
}

class Dog implements Animal {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
  makeSound() {
    console.log('Woof!');
  }
}

const dog = new Dog('Fido');
console.log(dog.name); // 'Fido'
dog.makeSound(); // 'Woof!'
```

In this example, the Animal interface defines a class with a name property of type string and a makeSound method that returns void. The Dog class implements the Animal interface, which means it must have a name property and a makeSound method with the correct types.