# Classes

A class in TypeScript is a blueprint for creating objects. It defines the properties and methods that objects created from the class will have.

Here's an example of how you might define a class in TypeScript:

```Typescript
class Person {
  name: string;
  age: number;
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
  sayHello() {
    console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
  }
}
```

This class defines a Person with a name property of type string and an age property of type number. It also has a constructor function that sets the values of these properties when a new Person object is created. Finally, it has a sayHello method that logs a greeting to the console.

To create a new object from this class, you can use the new keyword followed by the class name and passing in the required arguments:

```Typescript
const person = new Person('John', 30);
person.sayHello(); // 'Hello, my name is John and I am 30 years old.'
```

You can also define class properties and methods as public, private, or protected.

- public: These properties and methods can be accessed from outside the class. This is the default visibility if you don't specify a modifier.
- private: These properties and methods can only be accessed from within the class.
- protected: These properties and methods can be accessed from within the class and any subclasses (inherited classes).

For example:

```Typescript
class Person {
  public name: string;
  private age: number;
  protected country: string;
  constructor(name: string, age: number, country: string) {
    this.name = name;
    this.age = age;
    this.country = country;
  }
  sayHello() {
    console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
  }
}

const person = new Person('John', 30, 'USA');
console.log(person.name); // 'John'
console.log(person.age); // Error: Property 'age' is private and only accessible within class 'Person'.
console.log(person.country); // Error: Property 'country' is protected and only accessible within class 'Person' and its subclasses.
```
In this example, the name property is public, so it can be accessed from outside the class. The age property is private, so it can only be accessed from within the class. And the country property is protected, so it can be accessed from within the class and any subclasses.

You can also use inheritance to create a subclass that extends a superclass. For example:

```Typescript
class Animal {
  protected name: string;
  constructor(name: string) {
    this.name = name;
  }
  makeSound() {
    console.log('Some generic animal sound');
  }
}

class Dog extends Animal {
  constructor(name: string) {
    super(name);
  }
  makeSound() {
  console.log('Woof!');
  }
}

const dog = new Dog('Fido');
dog.makeSound(); // 'Woof!'

```

In this example, the Dog class extends the Animal class and has a makeSound method that overrides the one in the superclass. When you call the makeSound method on a Dog object, it will use the implementation in the subclass.

You can also use the super keyword to call the method from the superclass. For example:

```Typescript
class Animal {
  protected name: string;
  constructor(name: string) {
    this.name = name;
  }
  makeSound() {
    console.log('Some generic animal sound');
  }
}

class Dog extends Animal {
  constructor(name: string) {
    super(name);
  }
  makeSound() {
    super.makeSound();
    console.log('Woof!');
  }
}

const dog = new Dog('Fido');
dog.makeSound(); // 'Some generic animal sound' and then 'Woof!'

```
In this example, the makeSound method in the Dog class calls the makeSound method in the superclass using the super keyword, and then logs an additional message.