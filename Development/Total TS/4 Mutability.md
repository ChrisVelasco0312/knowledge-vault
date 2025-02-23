---
id: 4 Mutability
aliases: []
tags: []
---

# Inference differences between `let` and `const`

When we try to do something like this:

```ts
type ButtonAttributes = {
  type: "button" | "submit" | "reset";
};

let type = "button";

const buttonAttributes: ButtonAttributes = {
  type, // red squiggly line under type
};
```

TypeScript shows an error indicating that the type property is not
compatible because it is interpreted as string instead of "button".

```ts
Type 'string' is not assignable to type '"button" | "submit" | "reset"'
```

TypeScript does not make the connection between the `ButtonAttributes` type and the
type variable, because the `let`declaration of the variable indicates that the
variable can change in the future.

We solve it using `const`

```ts
// hovering over type
let type = "button";

// shows
let type: string;
```

# Objects and Assignability

Again we have an error when trying to use an object variable.
This happens because TypeScript knows objects in JavaScript can change even when
are declared with `const`.

```ts
const buttonAttributes = {
  type: "button",
};

const modifyButton = (attributes: ButtonAttributes) => {};
modifyButton(buttonAttributes);
```

The solution is to add a type to the `buttonAttributes` variable

```ts
const buttonAttributes: ButtonAttributes = {
  type: "button",
};

const modifyButton = (attributes: ButtonAttributes) => {};
modifyButton(buttonAttributes);
```

# Specifying `ReadOnly` property

```ts
type User = {
  readonly id: number;
  name: string;
  age: number;
};
```

# Readonly type helper

Convert all object properties to read-only

```ts
Readonly<YourObject>;
```

# Using `as const`

Adding `as const` to a variable, a `readonly` is applied to the type

```ts
type ButtonAttributes = {
  type: "button" | "submit" | "reset";
};

const buttonAttributes = {
  type: "button",
} as const;

// hovering over buttonAttributes shows:
const buttonAttributes: {
  readonly type: "button";
};
```

# `Object.freeze` vs `as const`

`Object.freeze` is a built in Object method in JavaScript that avoids mutation of
object propert values only at top level. Hence TypeScript infers only the top
level values as literals, it is not recursive.

`as const` works making readonly properties in nested objects, so it is
recursive and works perfectly in compile time.

# Creating Read-Only arrays

```ts
function printNames(names: readonly string[]) {
  ...
}

// or you can also use ReadoonlyArray utility

function printNames(names: ReadonlyArray<string>) {
  ...
}
```

# Use safe tuples

Use always readonly tuples in TypeScript to prevent mutability over tuples.

```ts
type Coordinate = readonly [number, number];

const myHouse: Coordinate = [0, 0];

const dangerousFunction = (arrayOfNumbers: number[]) => {
  arrayOfNumbers.pop();
  arrayOfNumbers.pop();
};

dangerousFunction(
  // @ts-expect-error
  myHouse, // red squiggly line under myHouse
);

// hovering over myHouse shows:
Argument of type 'Coordinate' is not assignable to parameter of type 'number[]'.
  The type 'Coordinate' is 'readonly' and cannot be assigned to the mutable type 'number[]'.
```
