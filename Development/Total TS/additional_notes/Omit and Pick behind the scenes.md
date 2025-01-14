---
id: Omit and Pick behind the scenes
aliases: []
tags: []
---

### Why the Omit Utility Type in TypeScript Allows to “Omit” Properties That Do Not Exist, While Pick Doesn’t

To understand why the `Omit` utility type in TypeScript allows you to omit properties
that do not exist on a given type, while `Pick` enforces strict validation of property keys,
we need to break this down step by step:

# How Omit and Pick Work Internally

Both `Omit` and `Pick` are utility types provided by `TypeScript`
to create new types based on existing ones.

They operate on the principle of key manipulation within object types.

`Pick`: This utility type constructs a new type by selecting
only the keys specified in `K` from the base type `T`.

The second parameter, `K`, must strictly be a subset of the keys of `T`.
If you try to use a key that does not exist in `T`, TypeScript will throw
a compile-time error because it ensures that only valid keys are picked.

```ts
interface Person {
  name: string;
  age: number;
  address: string;
}

type PickedPerson = Pick<Person, "name" | "age">;

// invalid usage (causes error)
type InvalidPickedPerson = Pick<Person, "id" | "name">;
```

`Omit`: This utility type constructs a new type by removing
the keys specified in `K` from the base type `T`.

However, unlike `Pick`, there is no strict enforcement that
the keys in `K` must actually exist in `T`.

If you specify non-existent keys in `K`,
TypeScript will simply ignore them without throwing an error.

# Further reading sources

- [Pick Utility Type](https://refine.dev/blog/typescript-pick-utility-type/#what-is-typescript-pick)
- [Stack overflow discussion](https://stackoverflow.com/questions/73164042/why-does-typescripts-omit-not-enforce-the-value-of-the-omitted-properties)

# A custom Stricter Version of Omit

The original implementation of the `Omit` utility is:
`type Omit<T, K extends keyof any> = Pick<T, Exclude<keyof T, K>>;`

This means `K` is constrained by keyof any, allowing any string-based keys.

A custom strict `Omit` needs to constrain `K` to `keyof T`. Meaning only
properties existing on `T` can be specified for omission.

`type StrictOmit<T, K extends keyof T> = Pick<T, Exclude<keyof T, K>>;`
