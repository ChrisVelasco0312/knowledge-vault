## Thinking in react
We break our app into pieces called components.
Then we describe different visual states for each one.
Finally, connect the components together so the data flows through them.

**STEPS**

### 0. Start with mockup
Imagine you have already a JSON API, we have to write the dummy or simulated data, that returns the API.

```javascript
[  
	{ category: "Fruits", price: "$1", stocked: true, name: "Apple" },  
	{ category: "Fruits", price: "$1", stocked: true, name: "Dragonfruit" },  
	{ category: "Fruits", price: "$2", stocked: false, name: "Passionfruit" },  
	{ category: "Vegetables", price: "$2", stocked: true, name: "Spinach" },  
	{ category: "Vegetables", price: "$4", stocked: false, name: "Pumpkin" },  
	{ category: "Vegetables", price: "$1", stocked: true, name: "Peas" }  
]
```

### 1. Break the UI into a component hierarchy
Draw boxes around every component and subcomponent. With [Figma,](https://www.figma.com) we can use the Layer panel to organize our component hierarchy if possible, but if not, we can duplicate the project and make our own annotations over the prototype.

* __Programming__ Using the single responsibility principle. A component should ideally do one thing. If it ends up growing, it should be decomposed into smaller subcomponents.
* __CSS__ Think about the classNames

With the JSON well-structures, the data should naturally map to the component structure of the UI. Data models have the same information architecture, the same shape. Separating the data into components, where each component matches a piece of the data model.

### 2. Build a static version in React
It's often easier to build a static version first and then add interactivity.
For building the static version, build components that reuse other components and pass data using **props** 
Remember __state__ is reserved only for interactivity - data changes over time.
On smaller projects, it's easier to go top-down and in bigger bottom-up.

### 3. Find minimal but complete representation of UI state

The state as the minimal set of changing data, changed by interaction with the UI.
Questions for deciding if something needs a state:
	- Does it remain unchange over time?
	- Is it passed from a parent via props?
	- Can you compute it based on existing state or props in your component?

### 4. Identify where your state should live
Identify which component is responsible for changing state or owns the state.
1.  Identify _every_ component that renders something based on that state.
2.  Find their closest common parent component—a component above them all in the hierarchy.
3.  Decide where the state should live:
    1.  Often, you can put the state directly into their common parent.
    2.  You can also put the state into some component above their common parent.
    3.  If you can’t find a component where it makes sense to own the state, create a new component solely for holding the state and add it somewhere in the hierarchy above the common parent component.