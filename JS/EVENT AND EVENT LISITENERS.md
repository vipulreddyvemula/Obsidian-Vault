- `click`
- `dblclick`  
- `keyup`   
- `keydown` 
- `mouseover`   
- `submit`  
- `change` 
- `load`
## **Ways to Add Event Listeners**

**A) addEventListener() — Best & Modern Way**
```js
element.addEventListener("click", function () {
    // This code runs when the element is clicked
});
```
     Using arrow function:
```js
element.addEventListener("click", () => {
    // arrow function version
});
```

**B) HTML Event Handler (Not recommended)**
```js
<button onclick="alert('Clicked!')">Click</button>
```
Avoid this; mixes HTML & JavaScript

**C) JS Property Method**
```js
element.onclick = () => {
    // runs on click
};
```
❌ Only one function can be assigned — new one overwrites old

## **Removing Listeners**
```js
function greet() {
    console.log("hi");
}

element.addEventListener("click", greet);
element.removeEventListener("click", greet);
```
> Must use the **same function reference** to remove it.

## **Common Events**

- Mouse: `click`, `dblclick`, `mouseover`, `mouseout`
- Keyboard: `keydown`, `keyup`   
- Input: `input`, `change` 
- Form: `submit`
- Document: `DOMContentLoaded`
- Window: `load`, `scroll`, `resize`
