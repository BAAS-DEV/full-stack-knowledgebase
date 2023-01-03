# Import/Export Across Files

In TypeScript, you can use the export keyword to make a function, class, or other value available for other files to import. And you can use the import keyword to bring in values that have been exported in other files.

Here's an example of how you might export and import a function in TypeScript:

First, create a file named math.ts with the following contents:

```Typescript
export function add(a: number, b: number) {
  return a + b;
}

export function subtract(a: number, b: number) {
  return a - b;
}
```
Then, in a separate file, you can import the functions from the math.ts file like this:

```Typescript
import { add, subtract } from './math';

console.log(add(1, 2)); // 3
console.log(subtract(1, 2)); // -1
```

You can also use the export default syntax to specify a default export for a file. For example:

```Typescript
// math.ts
export default function add(a: number, b: number) {
  return a + b;
}

export function subtract(a: number, b: number) {
  return a - b;
}

// main.ts
import add, { subtract } from './math';

console.log(add(1, 2)); // 3
console.log(subtract(1, 2)); // -1
```

In this example, the add function is the default export, and the subtract function is a named export. When you import from the math.ts file, you can use the import add, { subtract } from './math' syntax to import both the default export and the named export.

You can also use the export keyword to export a class or interface. For example:

```Typescript
// animal.ts
export interface Animal {
  name: string;
  makeSound(): void;
}

export class Dog implements Animal {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
  makeSound() {
    console.log('Woof!');
  }
}

// main.ts
import { Animal, Dog } from './animal';

const dog: Animal = new Dog('Fido');
dog.makeSound(); // 'Woof!'
```

In this example, the Animal interface and the Dog class are both exported from the animal.ts file. You can then import them in the main.ts file using the import { Animal, Dog } from './animal' syntax.

