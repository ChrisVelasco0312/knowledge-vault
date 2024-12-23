
# Type never
Represent the type of value that never returns. For example a function that always throws an Error (exception) or one that never returns. It is at the bottom of all types, so it is a subtype of every other type

![[never-type-diagram.png]]

# Discriminated unions

We can use the union type to discriminate between different variants of an object type with an identical property:
```ts
type Shape =
| { kind: "circle"; radius: number }
| { kind: "square"; x: number }
| { kind: "triangle"; x: number; y: number };

function area(s: Shape) {
  if (s.kind === "circle") {
    return Math.PI * s.radius * s.radius;
  } else if (s.kind === "square") {
    return s.x * s.x;
  } else {
    return (s.x * s.y) / 2;
  }
}
```

This way we can narrow the type using normal JavaScript, checking the identical property in all the options. So the key is to use `kind` as the discriminator. It is important to maintain the discriminator property consistent.

# Destructuring discriminated unions

https://kyleshevlin.com/discriminated-unions-and-destructuring-in-typescript/

```ts
function calculateArea(shape: Shape) {
  if (shape.kind === "circle") {
    const { radius } = shape;
    return Math.PI * radius * radius;
  } else {
    const { sideLength } = shape;
    return sideLength * sideLength;
  }
}
```

# Switch true

```ts
function calculateArea(shape: Shape) {
  switch (true) {
    case shape.kind === "circle": {
      return Math.PI * shape.radius * shape.radius;
    }
    case shape.kind === "square": {
      return shape.sideLength * shape.sideLength;
    }
  }
}
```

# Why prefer Interfaces Over Intersections

https://github.com/microsoft/TypeScript/wiki/Performance#preferring-interfaces-over-intersections

# Dynamic Keys with Index Signatures and Record Types.

**Index signatures** Typescript only accept one index signature per object
```ts
type Scores = {
	[suject: string]: number;
}
```
**Record** is a helper type can be used for the same however it is better when we want specific key names.
```ts
const scores: Record<string, number> = {}
```

# Using the PropertyKey Type in TypeScript

`PropertyKey` is a globally available type that represents all distinguishable keys that an object might need. The type definition of `PropertyKey` looks familiar:

```ts
// inside lib.es5.d.ts
declare type PropertyKey = string | number | symbol;
```

`PropertyKey` type is great for use cases like this or when using index signatures!

# Pick Utility Type

`Pick` allows to create new types by selectively choosing properties from an existing interface

```ts
type PickedUser = Pick<User, "name" | "email">;
```

This technique allow us to have **User** as a source of truth while also creating subtypes of **User** that contain only the properties needed.
It is important to know that this utility types don't work well with union types. They are essentially designed for objects.

# Omit Utility Type

`Omit` allows to exclude particular properties from a  type in TypeScript.

```ts
type ProductWithoutId = Omit<Product, "id">;
```

# Mutability

**Inference error**

When using let, to pass a variable as the value of an object with a defined type, typescript shows an error:

```ts
type Button = {
  type: "button" | "submit" | "reset";
};

let type = "button";

let myObj: Button = {
  type,
};
// Type 'string' is not assignable to type '"button" | "submit" | "reset"'

```

This happens because typescript knows that variables declared with `let` can be modified later in the code. TypeScript infers `let` as the most general possible version of the type to allow mutations `string`.

To solve this error we have to specify the variable as a `const`, that way TypeScript knows the variable is not going to change:

```ts
type Button = {
  type: "button" | "submit" | "reset";
};

const type = "button";

let myObj: Button = {
  type,
};
```

# Object property inference

In function parameters occurs something similar
```ts
type Attributes = {
  kind: "monster" | "human" | "creature"
}

function myFunc (attributes: Attributes) {{attributes}}

const myAttrib = {
  kind: "human"
}

myFunc(myAttrib);
// Type 'string' is not assignable to type '"monster" | "human" | "creature"'. 
```

The solution is to add a type to the const myAttrib, this way TypeScript can check the types.

```ts
type Attributes = {
  kind: "monster" | "human" | "creature";
};

function myFunc(attributes: Attributes) {
  {
    attributes;
  }
}

const myAttrib: Attributes = {
  kind: "human",
};

myFunc(myAttrib);
```

# Read-only properties
TypeScript offers a first-class approach for this by adding the `readonly` keyword before the property, like so:
```ts
type User = {
  readonly id: number;
  name: string;
  age: number;
};
```

With this change, the `id` property becomes read-only, whereas the other properties `name` and `age` remain mutable.

Remember, object properties in both TypeScript and JavaScript are mutable by default.

Adding of `readonly` to a property has no runtime effect, but instead is a type annotation that provides crucial information. It informs you that a certain property should not be changed once it is set, which eliminates the risk of unwarranted mutations.