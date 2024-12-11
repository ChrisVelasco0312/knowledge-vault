
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