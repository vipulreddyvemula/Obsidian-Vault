`# JavaScript Arrays Syntax Quick Reference` 

`## Declaration and Initialization`
```js
// Empty array  
let arr = [];

// Array with elements  
let fruits = ["Apple", "Banana", "Cherry"];
```

`## Accessing Elements`

```js
let first = fruits; // "Apple"  
let last = fruits[fruits.length - 1]; // "Cherry"
```

`## Modifying Elements`

```js
fruits = "Orange"; // changes "Banana" to "Orange"
```

`## Adding Elements`

```js
fruits.push("Mango"); // adds "Mango" to end  
fruits.unshift("Strawberry"); // adds to start
```
text

`## Removing Elements`

```js
fruits.pop(); // removes last element  
fruits.shift(); // removes first element
```

`## Looping through Arrays`
```js
for (let i = 0; i < fruits.length; i++) {  
console.log(fruits[i]);  
}

fruits.forEach(fruit => console.log(fruit));

```

`## Array Methods Examples`
```js
// Concatenate arrays  
let moreFruits = ["Peach", "Grapes"];  
let allFruits = fruits.concat(moreFruits);

// Slice array  
let someFruits = fruits.slice(1, 3); // from index 1 to 2

// Find index  
let pos = fruits.indexOf("Banana"); // -1 if not found
```
