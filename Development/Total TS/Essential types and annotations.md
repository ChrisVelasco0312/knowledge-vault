
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

### Sp