1. `getElementById()`
```js
document.getElementById("myId");
```
2. `getElementsByClassName()`
```js
document.getElementsByClassName("myClass");
```
3. `querySelector()`
```js
document.querySelector(".class"); 
document.querySelector("#id");
document.querySelector("div > p");
```
✔ Returns the **first match**  
4. `querySelectorAll()`
```js
document.querySelectorAll("p.myClass");
```

# DOM Manipulation
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
//

parent.append(newElement);  
// Same as appendChild but more flexible

parent.prepend(newElement); 
// Adds at the start of parent

parent.insertBefore(newEl, existingEl); 
// Inserts newEl before existingEl

```
 