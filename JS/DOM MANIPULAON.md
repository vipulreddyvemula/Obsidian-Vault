1. Changing Text
```js
element.textContent = "New Text"; 
// Replaces only the text (safest, no HTML interpretation)
//replaces the text completely

element.innerText = "Visible Text"; 
// Similar to textContent but respects CSS (like hidden text)
//doesnt touch hidden text

element.innerHTML = "<b>Bold Text</b>"; 
// Inserts HTML → be careful with user input
//can change the tag and <b> doesnt print
```

<hr>

2. Changing Attributes
```js
element.setAttribute("src", "image.png"); 
// Sets an attribute

element.getAttribute("href"); 
// Reads the value of an attribute

element.removeAttribute("disabled"); 
// Removes an attribute
```
Shortcut (direct property access):
```js
element.id = "newId";      // sets id
element.src = "photo.jpg"; // sets src
```

<hr>

3. Changing Styles
```js
element.style.color = "red"; 
// Changes text color

element.style.backgroundColor = "yellow"; 
// Changes background

element.style.fontSize = "20px"; 
// Changes font size
```
Multiple styles together:
```js
element.style.cssText = "color: red; background: black;";
// Applies many styles at once
```

<hr>

4. Adding & Removing Classes
```js
element.classList.add("active");    
// Adds a class(like it adds a class to div named active if not present)

element.classList.remove("hidden"); 
// Removes a class(removes the class named hidden)

element.classList.toggle("open");   
// Adds class if missing, removes if present

element.classList.contains("active"); 
// Checks if class exists → returns true/false
```

<hr>

5. Creating Elements
```js
const div = document.createElement("div"); 
// Creates a new <div> element

div.textContent = "Hello!"; 
// Adds text to it
```

<hr>

6. Adding Elements to Page
```js
parent.appendChild(child); 
// Adds element at the end of parent
//adds just one element and cant enter its text

parent.append(newElement);  
// Same as appendChild but more flexible
//can add text too
	ul.append(document.createElement("li"), "More");
	//creates li,adds it to ul,give the text more

parent.prepend(newElement); 
// Adds at the start of parent

parent.insertBefore(newEl, existingEl); 
// Inserts newEl before existingEl
```

<hr>

7. Removing Elements
```js
element.remove(); 
// Removes the element directly

// OR
parent.removeChild(child); 
// Removes a child using the parent
```

<hr>

8. Replacing Elements
```js
parent.replaceChild(newEl, oldEl); 
// Replaces oldEl with newEl
```

<hr>

9. Cloning Elements
```js
const clone = element.cloneNode(true); 
// true → deep clone (copies children too)

parent.appendChild(clone); 
// Adds the clone to the page
```

<hr>

### Event-Based Manipulation
```js
element.addEventListener("click", () => {
    // This code runs when element is clicked
    element.style.color = "blue"; 
	});
```