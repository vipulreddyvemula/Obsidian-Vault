**==BOX MODEL IN CSS==**

![[Pasted image 20251026204851.png]]
![[Pasted image 20251026204905.png]]
![[Pasted image 20251026204923.png]]
![[Pasted image 20251026204940.png]]
![[Pasted image 20251026204956.png]]
![[Pasted image 20251026205008.png]]
![[Pasted image 20251026205020.png]]
![[Pasted image 20251026205034.png]]
![[Pasted image 20251026205056.png]]
![[Pasted image 20251026205114.png]]
# CSS Box-Sizing Property
```css
/* Default behaviour */
div.content-box {
  box-sizing: content-box;
  width: 200px;
  padding: 20px;
  border: 10px solid black;
  /* Actual total width is 200 + 2*20 + 2*10 = 260px */
}

/* Border-box behaviour */
div.border-box {
  box-sizing: border-box;
  width: 200px;
  padding: 20px;
  border: 10px solid black;
  /* Actual total width remains 200px, content shrinks */
}
```
<hr>
# CSS Display Property

- Controls how an element is displayed and how it participates in the layout.
- Common values:
    - `block`: Element starts on a new line and takes full width (e.g., `<div>`, `<p>`).    
    - `inline`: Element flows with text and only takes as much width as needed (e.g., `<span>`, `<a>`).
    - `inline-block`: Like inline but can have width and height.
![[Pasted image 20251026212012.png]]
![[Pasted image 20251026212024.png]]
![[Pasted image 20251026212036.png]]
