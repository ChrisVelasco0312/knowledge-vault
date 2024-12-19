
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
