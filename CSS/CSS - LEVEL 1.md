==**Including Style**==
```css
/* INLINE */
<h1 style:"colour:red">  Apna college </h1>

	/* STYLE */
<style>
    h1{
        colour:red;
    }
</style>
```
==**External stylesheet**==
```css
<link rel = "stylesheet" href = "style.css">

/* this should be written in head tag and href= repreents the name of css file
```
==**Color property**==
```css
h1{
        colour:red;
    }
    
body{
        background-color: red;
    }

```
![[Pasted image 20251024182135.png]]
![[Pasted image 20251024182146.png]]

==**Selectors**==
```css
## universal selector =
 * {
        CSS properties 
    }        /* Selects all elements on the page */


## Element Selector
h1 {
        CSS properties 
}
- /* Selects all `<h1>` elements (replace `h1` with any tag). */


## Id Selector
#myId {
        CSS properties
}
- /* Selects one element with a specific id.*/

 
## Class Selector
.myClass {
        CSS properties 
}


- /* Selects all elements with a specific class.*/
```
---------------------------------------------------------------------
==**# Common Pseudo-Class Selectors**== 
Pseudo-class selectors in CSS target elements based on their state or user interaction, letting you style elements dynamically.  


- `:hover`      
    Applies when the user points or hovers over an element (e.g., with a mouse).      
    
- `:active`      
    Applies when the element is being activated (e.g., a button being pressed).  
    
- `:visited`        
    Used for links that the user has already visited.      
    
- `:focus`       
    Matches elements that have focus, like an input field selected by clicking or tabbing into it. 
- `:nth-child(n)`     
    Selects elements based on their position (n-th child) among siblings.  
    You can use numbers, keywords like `odd`/`even`, or formulas (e.g., `2n+1`).  
    Example: `li:nth-child(3)` selects the third `<li>` in each parent.  
    
```css
a:hover {
  color: blue;      /* Highlight link when hovered over */
}

button:active {
  background: yellow; /* Change button color when pressed */
}

a:visited {
  color: purple;    /* Change the color of visited links */
}

input:focus {
  border: 2px solid green; /* Highlight input when focused */
}

li:nth-child(2) {
  background: #ffd700; /* Highlights the second list item */
}

p:first-child {
  font-weight: bold; /* Makes the first paragraph bold */
}

li:last-child {
  color: red; /* Styles the last list item in red */
}

```

<hr>
# CSS Pseudo-Element Selectors

<!-- Pseudo-elements style specific parts of elements, using double colons (::). Common for fine-grained styling and UI/UX polish. -->

### `::first-line`

Styles only the first line of a block element’s text.

```css

`p::first-line { 
  font-weight: bold;   /* First line appears bold */ 
  color: darkblue; }`

<!-- Great for highlighting introductory sentences in paragraphs. -->
```
### `::first-letter`

Styles the first letter of a block element.


```css

`p::first-letter {
   font-size: 2em;      /* Enlarges first letter (drop cap) */
   color: orange;
   font-weight: bold; 
}`

<!-- Perfect for magazine-style effects or creative intros. -->
```
### `::before`

Inserts content before the real content of the element.

```css

`h1::before {   
	content: "★ ";       /* Adds a star before every <h1> */  
	color: gold;
}`

<!-- No need to change the underlying HTML for icons or highlights. -->
```

### `::after`

Inserts content after the element’s content.

```css

`button::after {   
	content: " ⏎";       /* Adds an arrow after each button */  
	color: gray; 
}`

<!-- Use for action hints, tooltips, badges, or explanatory symbols. -->
```

### `::marker`

Styles the marker (bullet/number) of list items.

```css
`li::marker {   
	color: red;          /* Makes bullets/numbers red */  
	font-size: 1.4em; 
}`

<!-- Lets you change the look of lists quickly without extra markup. -->
```
### `::selection`

Changes styles for text selected/highlighted by users.

```css
`::selection {   
	background: yellow;  /* Selected text gets a yellow background */  
	color: black; 
}`

<!-- Limited to text and background color; cannot style fonts or layout. -->
```

<hr>

==**CSS attribute selectors**==

[CSS Attribute Selectors](https://www.w3schools.com/css/css_attribute_selectors.asp)


	==**Text Properties**==
- T=text-align : left / right / center
```css
selector {
  text-align: center;
}

```

- text-decoration : underline / overline / line-through
```css
selector {
   text-decoration : underline;
}
```

> *%% Check mdn web docs for more properties %%*
> 


 - font-weight : normal / bold / bolder / lighter
 - font-weight : 100-900
```css
selector {
   font-weight : lighter;
}
/* font weight: 400 is bold */
   
```

- font-family : arial
- font-family : arial, roboto
```css
selector {
  font-family: font1, font2, ...;
}

```

==**Units in CSS - ABSOLUTE**==
pixels (px)
96px = 1 inch
-font-size
- font-size: 2px;

-line-height
- line-height : 2px
- line-height : 3
- line-height : normal

-text-transform
- text-tranform : uppercase / lowercase / capitalize / none

