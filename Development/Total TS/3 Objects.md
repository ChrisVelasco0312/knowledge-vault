---
id: 3 Objects
aliases: []
tags: []
---

# Dynamic Keys with Index signatures and record types.

When an object has an indetermined number of keys, and we need to add new properties to the object dynamically we can use `index signatures`:

```ts
const scores: { [key: string]: number } = {};

scores.math = 94;
scores.english = 90;
scores.science = 85;
```

The square bracket notation within the type definition resembles the way we would introduce keys to an actual JavaScript object.

We can use this notation with types and interfaces:

```ts
type Scores = {
  [subjects: string]: number;
};

interface Scores {
  [subject: string]: number;
}
```

And the same can be achieved using the `Record` helper type.

```ts
const scores: Record<string, number> = {};
```

# Default properties

Index signatures can be mixed with default properties:

```ts
interface Scores {
  [subject: string]: number;
  math: number;
  english: number;
  science: number;
}
```

# PropertyKey type

PropertyKey is a globally available type that represents all distinguishable
keys that and object might need.

```ts
// inside lib.es5.d.ts
declare type PropertyKey = string | number | symbol;
```

```ts
const hasKey = (obj: object, key: PropertyKey) => {
  return obj.hasOwnProperty(key);
};
```

This is great for cases when we are using index signatures.

# Records and Mapped types

We can limit the keys in a record (object), using the `Record` type.
Passing a type that is an union to the first parameter of the `Record` type.

```ts
type Environment = "development" | "production" | "staging";

type Configurations = Record<Environment, {
    apiBaseUrl: string;
    timeout: number;
};
```

You can also use the following syntax to achieve the same:

Known as **Mapped type**

```ts
type Configurations = {
  [Env in Environment]: {
    apiBaseUrl: string;
    timeout: number;
  };
};
```

# Declaration Merging

In Typescript is allowed to redeclare interfaces in the same scope because
aren't variables.

```ts
interface Logger {
  log(message: string, level: number): void;
}
interface Logger {
  log(message: string): void;
}
```

This behaviour is known as `Declaration Merging`, and allows to declare multiple
interfaces with the same name. This are merged together to form a single
definition.

With `type` this would not be allowed.

# Pick utility type

This utility type allows to create new types by choosing properties from an
existin interface.

```ts
type PickedUser = Pick<User, "name" | "email">;
```

This allows to have `User` as a source of truth while also creating subtypes of
`User` that contain only the properties we need.

Is important to know that `Pick` don't work well with union types.
Are essentially designed for objects.

# The Omit Utility Type

An utility type to exclude particular properties from a type.

```ts
type ProductWithoutId = Omit<Product, "id">;
```

However there is an interesting behaviour of the `Omit` utility type.
It allows to create new type that omits properties that don't exist:

```ts
type User = {
  id: number;
  name: string;
  email: string;
};

type UserWithoutPhoneNumber = Omit<User, "phoneNumber">;
```

While `Pick` throws an error when selecting properties that don't exist.

Learn more: [[Omit and Pick behind the scenes]]
