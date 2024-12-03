
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




 