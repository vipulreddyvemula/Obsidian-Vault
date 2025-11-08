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

