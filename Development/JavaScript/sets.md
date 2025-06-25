---
id: sets
aliases: []
tags: []
---

# Sets

In JavaScript Set is a collection of unique values.
The values can be of any type.

# How to create a Set

- Passing an array to `new Set()`

```js
const insects = new Set(["Worm", "Spider", "Fly"]);
```

- Create an empty set and use add() to add values

```js
const animals = new Set();
animals.add("Elephant");
animals.add("Chicken");
animals.add("Dog");
```

# List elements

Sets are an iterable object.
So we can use for loops.

```js
const letters = new Set(["a", "b", "c"]);

let text = "";
for (const x of letters) {
  text += x;
}
```

# Set Methods

```js
const mySet = new Set(["a", "b", "c"]);

// Get the number of elements
mySet.size; 

// has() return true if a value exists in a set
mySet.has("d") // false

// values() returns an iterator object with the values in a Set
mySet.values()
```

# Notes over the use of semantic methods.

Is interesting to note that methods like .values() return iterator.
However you might ask why get an iterator when a set is already an iterator
object.

In programming, semantics can be a way to make intentions explicit. Hence we can
improve the readability of the code using some methods over implicit shortcuts.

Certainly to transform a Set into an array we can do:
```js
const mySet = new Set(["a", "b", "c"]);
const arr = [...mySet];
```

But using values can be more explicit when reading it.
```js
const arr = Array.from(mySet.values());
//or
const arr = mySet.values().toArray();
```
