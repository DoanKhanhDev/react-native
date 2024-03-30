# Typescript Basic



## 1. Introduction

### 1.1 What is typescript?

- **TypeScript** is a superset of JavaScript that adds optional type annotations and other features such as interfaces, classes, and namespaces.

**Keyword:** Types, Syntax, Tooling, Backwards Compatibility.

### 1.2 TS/JS Interoperability

- Typescript and JavaScript have full interoperability. Meaning you can use TypeScript code in JavaScript and vice versa
- You can use JavaScript libraries in TypeScript project by either including the JavaScript files directly
- The TypeScript libraries use in JavaScript libraries is no problems. The generated JavaScript can be used in any JavaScript environment and it will work the same way at regular JavaScript code.

### 1.3 Install and configuration

- To install you need create apps from TypeScript template

Example with React Native:

```bash
npx create-expo-app my-app —template
```

- Additional, you can install typescript as a project dependency by running following command:

```bash
npm install --save-dev typescript
```

- To config TypeScript for your project. You create `tsconfig.json` file in your project directory to specify the compiler option for building your project. For Example:

```json
{
  "compilerOptions": {
    "target": "es5",
    "module": "commonjs",
    "strict": true,
    "outDir": "./dist",
    "rootDir": "./src"
  },
  "exclude": ["node_modules"]
}
```

### 1.4 What is tsc?

- `tsc` is the command line tool for the Typescript complier. It complies Typescript code into Javascript code, making it compatible  with the browser or any Javascript runtime environment.
- To complier Typescript code in your project, you can run following command and this is command will compile all Typescript file that are specify in `tsconfig.json` file:

```bash
tsc
```

- You can compile specify a file by command:

```
tsc index.ts
```

### Read more

- [tsc CLI Options](https://www.typescriptlang.org/docs/handbook/compiler-options.html#using-the-cli)
- [ts-node - Run Typescript with ts-node](https://www.digitalocean.com/community/tutorials/typescript-running-typescript-ts-node)
- [TS Playground - Tool Typescript Online](https://www.typescriptlang.org/play)

---

## 2. Typescript Types

### 2.1 Primitive types

- Boolean
- Number
- String
- Void
  - In JavaScript, a function that doesn’t return any value will implicitly return the value undefined. However, void and undefined are not the same thing in TypeScript.
- Undefined
- Null

### 2.2 Object types

- Inteface
- Class
- Enum
- Array
- Tuples
  - Example:

  ```typescript
  const pair: StringNumberPair = ['hello', 42];
  ```

### Other Types

- Any
- Object
- Unknown
- Never

### Assertions

- Type assertions in TypeScript are a way to tell the compiler to treat a value as a specific type, regardless of its inferred type. For example:

  ```typescript
  // using as syntax
  let str2 = num as string;
  ```

## 3. Combining types

### 3.1 Union types

- Union Types in TypeScript allow you to specify multiple possible types for a single variable or parameter. A union type is written as a vertical bar | separated list of types.

  For example:

  ```typescript
  function combine(input1: string | number, input2: string | number) {
    return input1 + input2;
  }
  ```

### 3.2 Intersection Types

- An intersection type creates a new type by combining multiple existing types. The new type has all features of the existing types.

- To combine types, you use the & operator as follows:

  For example:

  ```typescript
  type typeAB = typeA & typeB;
  ```

### 3.4 Type Aliases

- A Type Alias in TypeScript allows you to create a new name for a type.

  Here’s an example:

  ```typescript
  type Name = string;
  type Age = number;
  type User = { name: Name; age: Age };

  const user: User = { name: 'John', age: 30 };
  ```

### 3.5 Keyof

- The keyof operator takes an object type and produces a string or numeric literal union of its keys.

  For example:

  ```typescript
  type Arrayish = { [n: number]: unknown };
  type A = keyof Arrayish; // type A = number
  type Mapish = { [k: string]: boolean };
  type M = keyof Mapish; // type M = string | number
  ```

- `M` is `string` | `number` this is because JavaScript object keys are always coerced to a string, so `obj[0]` is always the same as `obj["0"]`.


## 4. Type Guards/Narrowing

### 4.1 Instanceof

- The `instanceof` operator is a way to narrow down the type of a variable. It is used to check if an object is an instance of a class.

### 4.2 Typeof

- The `typeof` operator is used to check the type of a variable. It returns a string value representing the type of the variable.

## 5. Typescript Function

### 5.1 Typing Function

- In TypeScript, functions can be typed in a few different ways to indicate the input parameters and return type of the function.

- Function declaration with types:

  ```typescript
  function add(a: number, b: number): number {
    return a + b;
  }
  ```

- Arrow function with types:

  ```typescript
  const multiply = (a: number, b: number): number => {
    return a * b;
  };
  ```

- Funtion type:

  ```typescript
  let divide: (a: number, b: number) => number;

  divide = (a, b) => {
    return a / b;
  };
  ```

### 5.2 Functuion Overloading

- Function Overloading in TypeScript allows multiple functions with the same name but with different parameters to be defined. The correct function to call is determined based on the number, type, and order of the arguments passed to the function at runtime.

## 6. Typescript interface

### 6.1 Type vs Interface

- Types are used to create a new named type based on an existing type or to combine existing types into a new type.
- Interfaces, on the other hand, are used to describe the structure of objects and classes.

### 6.2 Extending interface

- In TypeScript, you can extend an interface by creating a new interface that inherits from the original interface using the “extends” keyword. The new interface can include additional properties, methods, or redefine the members of the original interface.

  For example:

  ```typescript
  interface Shape {
    width: number;
    height: number;
  }

  interface Square extends Shape {
    sideLength: number;
  }

  let square: Square = {
    width: 10,
    height: 10,
    sideLength: 10,
  };
  ```


### 6.3 Interface Declaration

- The age property is optional, indicated by the ? symbol.

  ```typescript
  interface Person {
    firstName: string;
    lastName: string;
    age?: number;

    getFullName(): string;
  }
  ```

## 7. Classes

### 7.1 Constructor Params

- In TypeScript, constructor parameters can be declared with access modifiers (e.g. public, private, protected) and/or type annotations. The parameters are then automatically assigned to properties of the same name within the constructor, and can be accessed within the class.

  For example::

  ```typescript
  class Example {
    constructor(private name: string, public age: number) {}
  }
  ```

## 8. Generic

### 8.1 Generic Types

- Generic types in TypeScript allow you to write objects, functions and classes that work with multiple data types, instead of being limited to a single data type. A generic type is defined using angle brackets <T> and can be used as a placeholder for a specific data type. The actual data type is specified when the function or class is used.

  For example:

  ```typescript
  function identity<T>(arg: T): T {
    return arg;
  }

  let output = identity<string>('Hello'); // type of output will be 'string'
  ```

### 8.2 Generic Constraints

- Generic constraints in TypeScript allow you to specify the requirements for the type parameters used in a generic type. These constraints ensure that the type parameter used in a generic type meets certain requirements.

- Constraints are specified using the extends keyword, followed by the type that the type parameter must extend or implement.

  For example:

  ```typescript
  interface Lengthwise {
    length: number;
  }

  function loggingIdentity<T extends Lengthwise>(arg: T): T {
    // Now we know it has a .length property, so no more error
    console.log(arg.length);

    return arg;
  }

  loggingIdentity(3); // Error, number doesn't have a .length property
  loggingIdentity({ length: 10, value: 3 }); // OK
  ```

## 9. Decorators

- Decorators are a feature of TypeScript that allow you to modify the behavior of a class, property, method, or parameter. They are a way to add additional functionality to existing code, and they can be used for a wide range of tasks, including logging, performance optimization, and validation.

  For example

  ```typescript
  function log(
    target: Object,
    propertyKey: string | symbol,
    descriptor: PropertyDescriptor
  ) {
    const originalMethod = descriptor.value;

    descriptor.value = function (...args: any[]) {
      console.log(`Calling ${propertyKey} with arguments: ${args}`);
      return originalMethod.apply(this, args);
    };

    return descriptor;
  }

  class Calculator {
    @log
    add(a: number, b: number): number {
      return a + b;
    }
  }

  const calculator = new Calculator();
  calculator.add(1, 2);
  // Output: Calling add with arguments: 1,2
  // Output: 3
  ```

## 10. Utility Types

### 10.1 Partial

- The Partial type in TypeScript allows you to make all properties of a type optional. This is useful when you need to create an object with only a subset of the properties of an existing type.

  For example:

  ```typescript
  interface User {
    name: string;
    age: number;
    email: string;
  }

  function createUser(user: Partial<User>): User {
    return {
      name: 'John Doe',
      age: 30,
      email: 'john.doe@example.com',
      ...user,
    };
  }

  const newUser = createUser({ name: 'Jane Doe' });

  console.log(newUser);
  // Output: { name: 'Jane Doe', age: 30, email: 'john.doe@example.com' }
  ```

### 10.2 Pick

- Pick constructs a type by picking the set of properties Keys (string literal or union of string literals) from Type.

  For example:

  ```typescript
  interface Todo {
    title: string;
    description: string;
    completed: boolean;
  }

  type TodoPreview = Pick<Todo, 'title' | 'completed'>;

  const todo: TodoPreview = {
    title: 'Clean room',
    completed: false,
  };
  ```

### 10.3 Omit

- Omit constructs a type by picking all properties from Type and then removing Keys (string literal or union of string literals).

  For example:

  ```typescript
  interface Todo {
    title: string;
    description: string;
    completed: boolean;
    createdAt: number;
  }

  type TodoPreview = Omit<Todo, 'description'>;

  const todo: TodoPreview = {
    title: 'Clean room',
    completed: false,
    createdAt: 1615544252770,
  };

  type TodoInfo = Omit<Todo, 'completed' | 'createdAt'>;

  const todoInfo: TodoInfo = {
    title: 'Pick up kids',
    description: 'Kindergarten closes at 5pm',
  };
  ```
### 10.4 Readonly

- Readonly constructs a type with all properties of Type set to readonly, meaning the properties of the constructed type cannot be reassigned.

  For example:

  ```typescript
  interface Todo {
    title: string;
  }

  const todo: Readonly<Todo> = {
    title: 'Delete inactive users',
  };

  // Cannot assign to 'title' because it is a read-only property.
  todo.title = 'Hello';
  ```

### 10.5 Record

- Record constructs an object type whose property keys are Keys and whose property values are Type. This utility can be used to map the properties of a type to another type.

  For example:

  ```typescript
  interface CatInfo {
    age: number;
    breed: string;
  }

  type CatName = 'miffy' | 'boris' | 'mordred';

  const cats: Record<CatName, CatInfo> = {
    miffy: { age: 10, breed: 'Persian' },
    boris: { age: 5, breed: 'Maine Coon' },
    mordred: { age: 16, breed: 'British Shorthair' },
  };
  ```

### 10.6 Exclude

- Exclude constructs a type by excluding from UnionType all union members that are assignable to ExcludedMembers.

  For example:

  ```typescript
  type T0 = Exclude<'a' | 'b' | 'c', 'a'>; // "b" | "c"
  type T1 = Exclude<'a' | 'b' | 'c', 'a' | 'b'>; // "c"
  type T2 = Exclude<string | number | (() => void), Function>; // string | number
  ```

### 10.7 Extract

- Extract constructs a type by extracting from Type all union members that are assignable to Union.

  For example:

  ```typescript
  type T0 = Extract<'a' | 'b' | 'c', 'a' | 'f'>;
  //  ^ = type T0 = "a"
  ```

- If extracing from type all union memebers that are no assigable to Union. type `T0` is `nerver`

  For example:

  ```typescript
  type T0 = Extract<'a' | 'b' | 'c', 'd' | 'f'>;
  //  type T0 = nerver
  ```

### 10.8 Non Nullable

- Non-Nullable constructs a type by excluding null and undefined from Type.

  For example:

  ```typescript
  type T0 = NonNullable<string | number | undefined>;
  // type T0 = string | number

  type T1 = NonNullable<string[] | null | undefined>;
  // type T1 = string[]
  ```

### 10.9 Parameters

- Parameters constructs a tuple type from the types used in the parameters of a function type Type

  For example:

  ```typescript
  type T0 = Parameters<() => string>;
  // type T0 = []

  type T1 = Parameters<(s: string) => void>;
  // type T1 = [s: string]

  type T2 = Parameters<<T>(arg: T) => T>;
  // type T2 = [arg: unknown]

  declare function f1(arg: { a: number; b: string }): void;
  type T3 = Parameters<typeof f1>;
  // type T3 = [arg: {
  //     a: number;
  //     b: string;
  // }]

  type T4 = Parameters<any>;
  // type T4 = unknown[]

  type T5 = Parameters<never>;
  // type T5 = never

  type T6 = Parameters<string>;
  // ^ Type 'string' does not satisfy the constraint '(...args: any) => any'.

  type T7 = Parameters<Function>;
  // ^ Type 'Function' does not satisfy the constraint '(...args: any) => any'.
  ```

### 10.10 ReturnTypes

- Return type constructs a type consisting of the return type of function Type.

  For example:

  ```typescript
  type T0 = ReturnType<() => string>;
  // type T0 = string

  type T1 = ReturnType<(s: string) => void>;
  // type T1 = void

  type T2 = ReturnType<<T>() => T>;
  // type T2 = unknown

  type T3 = ReturnType<<T extends U, U extends number[]>() => T>;
  // type T3 = number[]

  declare function f1(): { a: number; b: string };
  type T4 = ReturnType<typeof f1>;
  // type T4 = {
  //     a: number;
  //     b: string;
  // }

  type T5 = ReturnType<any>;
  // type T5 = any

  type T6 = ReturnType<never>;
  // type T6 = never

  type T7 = ReturnType<string>;
  // ^ Type 'string' does not satisfy the constraint '(...args: any) => any'.

  type T8 = ReturnType<Function>;
  // ^ Type 'Function' does not satisfy the constraint '(...args: any) => any'.
  ```

### 10.11 InstanceType

- This type constructs a type consisting of the instance type of a constructor function in Type.

  For example:

  ```typescript
  class C {
    x = 0;
    y = 0;
  }

  type T0 = InstanceType<typeof C>;
  // type T0 = C

  type T1 = InstanceType<any>;
  // type T1 = any

  type T2 = InstanceType<never>;
  // type T2 = never

  type T3 = InstanceType<string>;
  // ^ Type 'string' does not satisfy the constraint 'abstract new (...args: any) => any'.

  type T4 = InstanceType<Function>;
  // ^ Type 'Function' does not satisfy the constraint 'abstract new (...args: any) => any'.
  ```

### 10.12 Awaited

- This type is meant to model operations like await in async functions, or the .then() method on Promises - specifically, the way that they recursively unwrap Promises.

  For example:

  ```typescript
  type A = Awaited<Promise<string>>;
  // type A = string

  type B = Awaited<Promise<Promise<number>>>;
  // type B = number

  type C = Awaited<boolean | Promise<number>>;
  // type C = number | boolean
  ```
