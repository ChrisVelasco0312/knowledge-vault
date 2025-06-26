---
id: maps
aliases: []
tags: []
---

# JavaScript Maps

- Holds key-value pairs where keys can be any datatype.
- Remember the original insertion order of keys.

# Create a Map

- Passing an Array to `new Map()`

```js
const fruits = new Map([
  ["apples", 500],
  ["bananas", 300],
  ["oranges", 200]
]);
```

The `set()` can used to add element and change existing values.

```js
const fruits = new Map();

fruits.set("apples", 500);
fruts.set("bananas", 300);
fruits.set("oranges", 200);

fruits.set("apples", 230); // update the existing value
```

The `get()` method gets the value of a key in a Map

```js
fruits.get("apples");
```

The `size()` property returns the number of elements in a map:
```js
fruits.size;
```

`delete()` method remove a map element

```js
fruits.delete("apples");
```

`clear()` method remove all elements
`has()` returns true if a key exists

A Map is compatible with Set.

# Map.groupBy()

This method groups elements of an object according to string values returned
from a callback function.

In this example we transform a Map into an array of objects, and then used
Map.groupBy()

```js
const animalMap = new Map();
animalMap.set("Fausto", {
  age: 4,
  vaccine: false,
  species: "Cat",
});
animalMap.set("Alice", {
  age: 3,
  vaccine: true,
  species: "Cat",
});
animalMap.set("Ofelia", {
  age: 5,
  vaccine: true,
  species: "Cat",
});
animalMap.set("Piggy", {
  age: 2,
  vaccine: false,
  species: "Cat",
});

let animalObjArr = Object.fromEntries(animalMap);
animalObjArr = Object.entries(animalObjArr).map(([name, value]) => ({name: name, ...value}))

let vaccinatedGroup = Map.groupBy(animalObjArr, ({ vaccine }) =>
  vaccine ? "vaccinated" : "notVaccinated",
);
```

### Typescript
[[1 Essential types and annotations#adding-types-to-maps]]
