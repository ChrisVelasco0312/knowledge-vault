
### Optional parameter in functions
Adding  question mark `?` to the end of a parameter, it will be marked as optional

The last will receive either `string` or `undefined` -> `string | undefined`
```ts
function concatName (first: string, last?:string) {
...
}
```

### Default parameter in functions

Use the =  syntax also used in JavaScript.
```ts
export const concatName = (first: string, last?: string = "Pocock") => {
	return `${first} ${last}`;
};
```

Because a default value is added to the parameter, the `| undefined` part of the type is no longer applicable

### The Array modifier syntax `[]`

In the next type, items will be an array of strings.
```ts
type ShoppingCart = {
	userId: string;
	items: string[];
};
```

A second syntax is to explicitly write `Array` with the type inside of angle brackets `<>`
```ts
type ShoppingCart = {
	userId: string;
	items: Array<string>;
};
```

### Array of Objects 

```ts
type Ingredient = {
	name: string;
	quantity: string;
}

type Recipe = {
	title: string;
	instructions: string;
	ingredients: Ingredient[];
};
```

And `Array<Ingredient>` would also work
```ts
type Recipe = {
	title: string;
	instructions: string;
	ingredients: Array<Ingredient>;
};
```

### Rest parameters

When using rest parameters, all of the arguments passed to the parameter will end up as an array that is passed to the function.
```ts
export function concatenate(...strings: string[]) {
	return strings.join("");
}
```

It's also possible to have other parameters come before the rest parameter. For example, we could have a `num` parameter of number before the rest parameter:

```ts
export function concatenateWithNumber(num: number, ...strings: string[]) {
	return strings.join("");
}
```

### Tuple syntax

Use square brackets with types inside: `[number, number]`

```ts
const setRange = (range: [number, number]) => {
  ...
}
```

A tuple here is equal to an array of two members. If we pass it too few arguments, TypeScript will show an error:
```
Argument of type 'number' is not assignable to parameter of type '[number, number]'.
```

For more clarity, you can add names for each of the types
```ts
[x: number, y: number]

setR
```