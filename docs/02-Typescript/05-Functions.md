
# Functions

## What are functions?
In programming, a function is a block of code that performs a specific task. Functions are a fundamental building block of most programming languages, and they are used to organize and reuse code.

Functions are defined with a function signature, which consists of the function name, the list of parameters, and the return type. The function body contains the code that is executed when the function is called.

Here is an example of a simple function in TypeScript:

```Typescript
function add(x: number, y: number): number {
  return x + y;
}

console.log(add(1, 2)); // 3
```

In this example, we defined a function named add that takes two parameters x and y of type number and returns a value of type number. The function body contains a single line of code that adds x and y and returns the result. We called the add function and passed in the values 1 and 2 as arguments, which resulted in the output 3.

## What are functions used for?
Functions are used for a variety of purposes, including:

- Organizing and reusing code: Functions allow you to define a block of code and reuse it multiple times in your program. This helps to keep your code organized and reduces duplication.

- Modularizing code: Functions allow you to divide your code into smaller, more manageable pieces. This makes it easier to understand and debug your code.

- Separating concerns: Functions allow you to isolate different pieces of code that have different responsibilities, which makes it easier to understand the overall structure of your program.

- Improving performance: Functions can improve performance by allowing you to execute code only when it is needed, rather than executing all of your code at once.

- Enabling code reuse: Functions can be called from other parts of your program, or even from other programs, which allows you to reuse your code in multiple contexts.

## Return types and purpose

The return type of a function is the type of the value that the function returns when it is called. The return type is specified in the function signature after the parameters, using a colon and the type name.

For example:

```Typescript
function add(x: number, y: number): number {
  return x + y;
}
```

In this example, the return type of the add function is number. This means that the function will return a value  of type number when it is called.

The purpose of the return type is to specify the type of the value that the function returns, so that the compiler can check that the return value is used correctly. For example, if you try to assign the return value of the add function to a variable of type string, the compiler will give an error because the return type is number and not string.

```Typescript
let result: string = add(1, 2); // error: Type 'number' is not assignable to type 'string'.
```

If the function does not return a value, you can specify the return type as void. For example:

```Typescript
function log(message: string): void {
  console.log(message);
}

log("Hello, world!"); // Hello, world!
```

In this example, the log function takes a parameter message of type string and does not return a value. The return type is void, which means that the function does not return a value. We called the log function and passed in the string "Hello, world!" as an argument, which resulted in the output "Hello, world!".

## Defining Functions
In TypeScript, you can define a function using the function keyword followed by the function name and a list of parameters inside parentheses. The function body is enclosed in curly braces. The syntax for defining a function is:

```Typescript
function functionName(parameter1: type1, parameter2: type2, ...): returnType {
  // function body
  return value;
}
```
The functionName is the name of the function. The parameter1, parameter2, etc. are the names of the parameters that the function accepts. The type1, type2, etc. are the types of the parameters. The returnType is the type of the value that the function returns. If the function does not return a value, you can use the void type as the returnType.

For example:

```Typescript
function add(x: number, y: number): number {
  return x + y;
}
console.log(add(1, 2)); // 3

```

In this example, we defined a function named add that takes two parameters of type number and returns a value of type number. We called the add function and passed in the values 1 and 2 as arguments, which resulted in the output 3.

## Optional Parameters
In TypeScript, you can make a function parameter optional by adding a ? after the parameter name. Optional parameters are defined after required parameters.

For example:

```Typescript
function greet(name: string, greeting?: string): void {
  console.log(`${greeting}, ${name}!`);
}

greet("John"); // Hello, John!
greet("John", "Hi"); // Hi, John!
```

In this example, we defined a function named greet that takes a required parameter name of type string and an optional parameter greeting of type string. We called the greet function with only one argument, which resulted in the output "Hello, John!". We also called the greet function with two arguments, which resulted in the output "Hi, John!".

## Default Parameters
In TypeScript, you can assign a default value to a function parameter by using the = operator. Default parameters are defined after optional parameters.

For example:

```Typescript
function greet(name: string, greeting: string = "Hello"): void {
  console.log(`${greeting}, ${name}!`);
}

greet("John"); // Hello, John!
greet("John", "Hi"); // Hi, John!
```
In this example, we defined a function named greet that takes a required parameter name of type string and a default parameter greeting of type string with the value "Hello". We called the greet function with only one argument, which resulted in the output "Hello, John!". We also called the greet function with two arguments, which resulted in the output "Hi, John!".

## Rest Parameters
In TypeScript, you can use the ... syntax to define a rest parameter, which is an array that captures all the remaining arguments of a function. Rest parameters are defined after required and optional parameters.

For example:

```Typescript
function sum(x: number, y: number, ...values: number[]): number {
  let total = x + y;
  values.forEach(value => {
    total += value;
  });
  return total;
}

console.log(sum(1, 2, 3, 4, 5)); // 15

```

In this example, we defined a function named sum that takes two required parameters x and y of type number, and a rest parameter values of type number[]. The forEach loop iterates over each element in the values array and adds it to the total variable. We called the sum function and passed in the values 1, 2, 3, 4, and 5 as arguments, which resulted in the output 15.

Function Overloads
In TypeScript, you can use function overloads to define multiple functions with the same name but different parameter lists. When calling the function, the correct function will be selected based on the number and types of the arguments.

For example:

```Typescript
function greet(name: string): void;
function greet(age: number): void;
function greet(nameOrAge: string | number): void {
  if (typeof nameOrAge === "string") {
    console.log(`Hello, ${nameOrAge}!`);
  } else {
    console.log(`You are ${nameOrAge} years old.`);
  }
}

greet("John"); // Hello, John!
greet(30); // You are 30 years old.
```

In this example, we defined three functions with the same name greet but different parameter lists. The first two functions are the overloads, and the third function is the implementation. The first overload takes a parameter name of type string, and the second overload takes a parameter age of type number. The implementation takes a parameter nameOrAge of type string | number, which means that it can be either a string or a number.

The implementation uses the typeof operator to check the type of the nameOrAge parameter, and logs a different message depending on the type. We called the greet function with a string argument and a number argument, which resulted in the output "Hello, John!" and "You are 30 years old.", respectively.

## Anonymous Functions
In TypeScript, you can define an anonymous function, which is a function without a name. Anonymous functions are usually used as callback functions or immediately-invoked function expressions (IIFEs).

To define an anonymous function, you can omit the function name and assign the function to a variable. The syntax for defining an anonymous function is:

```Typescript
let variableName = function(parameter1: type1, parameter2: type2, ...): returnType {
  // function body
  return value;
};
```

For example:

```Typescript
let add = function(x: number, y: number): number {
  return x + y;
};

console.log(add(1, 2)); // 3
```

In this example, we defined an anonymous function and assigned it to the variable add. The anonymous function takes two parameters x and y of type number and returns a value of type number. We called the add function and passed in the values 1 and 2 as arguments, which resulted in the output 3.

Arrow Functions
In TypeScript, you can use the arrow function syntax to define a function. Arrow functions are a shorthand way to write anonymous functions, and they have a shorter syntax and lexical scoping of the this keyword.

To define an arrow function, you can use the => operator followed by the function body. If the function has one parameter, you can omit the parentheses. If the function has no parameters or multiple parameters, you must include the parentheses. The syntax for defining an arrow function is:

let variableName = (parameter1: type1, parameter2: type2, ...): returnType => {
  // function body
  return value;
};
For example:

```Typescript
let add = (x: number, y: number): number => {
  return x + y;
};

console.log(add(1, 2)); // 3
In this example, we defined an arrow function and assigned it to the variable add. The arrow function takes two parameters x and y of type number and returns a value of type number. We called the add function and passed in the values 1 and 2 as arguments, which resulted in the output 3.

If the function has only one statement, you can omit the curly braces and the return keyword. The syntax for defining a single-line arrow function is:

```Typescript
let variableName = (parameter1: type1, parameter2: type2, ...): returnType => expression;
For example:

```Typescript
let add = (x: number, y: number): number => x + y;

console.log(add(1, 2)); // 3
```

In this example, we defined a single-line arrow function and assigned it to the variable add. The arrow function takes two parameters x and y of type number and returns a value of type number. We called the add function and passed in the values 1 and 2 as arguments, which resulted in the output 3.

## Function Types
In TypeScript, you can use the function type to specify the type of a function. The syntax for the function type is:

```Typescript
let variableName: (parameter1: type1, parameter2: type2, ...) => returnType = functionName;
For example:

function add(x: number, y: number): number {
  return x + y;
}

let addFunction: (x: number, y: number) => number = add;

console.log(addFunction(1, 2)); // 3
```

In this example, we defined a function named add that takes two parameters x and y of type number and returns a value of type number. We also defined a variable addFunction of type (x: number, y: number) => number, which means that it is a function that takes two parameters of type number and returns a value of type number. We assigned the add function to the addFunction variable. We called the addFunction function and passed in the values 1 and 2 as arguments, which resulted in the output 3.

Function types are useful when you want to specify the type of a function that you pass as an argument to another function, or when you want to specify the type of a function that you return from another function.

For example:

```Typescript
function apply(func: (x: number, y: number) => number, x: number, y: number): number {
  return func(x, y);
}

console.log(apply(add, 1, 2)); // 3

```

In this example, we defined a function named apply that takes a parameter func of type (x: number, y: number) => number, which means that it is a function that takes two parameters of type number and returns a value of type number. The apply function also takes two parameters x and y of type number. The apply function calls the func function with the x and y arguments and returns the result. We called the apply function and passed in the add function and the values 1 and 2 as arguments, which resulted in the output 3.

Function types are useful when you want to specify the type of a function that you pass as an argument to another function, or when you want to specify the type of a function that you return from another function.

For example:

```Typescript
function createAdder(x: number): (y: number) => number {
  return function(y: number): number {
    return x + y;
  };
}

let add10 = createAdder(10);
console.log(add10(5)); // 15

```

In this example, we defined a function named createAdder that takes a parameter x of type number and returns a function of type (y: number) => number, which means that it is a function that takes a parameter y of type number and returns a value of type number. The createAdder function defines an anonymous function that takes a parameter y of type number and returns the sum of x and y. We assigned the returned function to the variable add10. We called the add10 function with the value 5 as an argument, which resulted in the output 15.