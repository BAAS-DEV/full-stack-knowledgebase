# Conditional Statements

## The If Statement
The if statement is used to execute a block of code only if a certain condition is true. The syntax for an if statement is:

```Typescript
if (condition) {
  // code to execute if condition is true
}
```
For example:

```Typescript
let x = 10;

if (x > 5) {
  console.log("x is greater than 5");
}
```

In this example, the code inside the if block will be executed because the condition x > 5 is true.

You can also use the else keyword to execute a block of code if the condition is false. The syntax for an if-else statement is:

```Typescript
if (condition) {
  // code to execute if condition is true
} else {
  // code to execute if condition is false
}
```

For example:

```Typescript
let x = 10;

if (x > 5) {
  console.log("x is greater than 5");
} else {
  console.log("x is not greater than 5");
}
```

In this example, the code inside the if block will be executed because the condition x > 5 is true.


## The Switch Statement
The switch statement is used to execute a block of code based on the value of a variable. The syntax for a switch statement is:

Copy code
switch (variable) {
  case value1:
    // code to execute if variable is value1
    break;
  case value2:
    // code to execute if variable is value2
    break;
  default:
    // code to execute if variable is not value1 or value2
}
The break keyword is used to exit the switch block after a match is found.

For example:

```Typescript
let x = "red";

switch (x) {
  case "red":
    console.log("x is red");
    break;
  case "blue":
    console.log("x is blue");
    break;
  default:
    console.log("x is neither red nor blue");
}
```

In this example, the code inside the case "red": block will be executed because the value of x is "red".

## The Ternary Operator

The ternary operator (also known as the conditional operator) is a shorthand way to write an if-else statement. The syntax for the ternary operator is:

```Typescript
condition ? value1 : value2
```

This is equivalent to the following if-else statement:

```Typescript
if (condition) {
  value1;
} else {
  value2;
}

```

For example:

```Typescript
let x = 10;
let y = x > 5 ? "x is greater than 5" : "x is not greater than 5";

console.log(y);
```

In this example, the value of y will be "x is greater than 5" because the condition x > 5 is true.

