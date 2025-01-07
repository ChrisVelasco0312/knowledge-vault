# Dynamic Keys with Index signatures and record types.

When an object has an indetermined number of keys, and we need to add new properties to the object dynamically we can use `index signatures`:

```ts
const scores: { [key: string]: number } = {}

scores.math = 94;
scores.english = 90;
scores.science = 85;
```

The square bracket notation within the type definition resembles the way we would introduce keys to an actual JavaScript object.

We can use this notation with types and interfaces:
```ts
type Scores = {
	[subjects: string]: number;
}

interface Scores {
	[subject: string]: number;
}
```

And the same can be achieved using the `Record` helper type.

```ts
const scores: Record<string, number> = {};
```

# Default properties

