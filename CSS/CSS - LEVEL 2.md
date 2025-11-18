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
# CSS Text Effects
- **text-shadow:** Adds shadow behind text for depth.  
    Example: `text-shadow: 2px 2px 3px gray;
    **text-shadow syntax:**  
    `text-shadow: horizontal-offset vertical-offset blur-radius color;`

- **text-transform:** Changes text case to uppercase, lowercase, or capitalize.  
    Example: `text-transform: uppercase;`

- **text-decoration:** Adds underline, overline, or line-through effects.  
    Example: `text-decoration: underline;`

- **text-overflow:** Controls overflowed text display (e.g., show ellipsis).  
    Example: `text-overflow: ellipsis;`

- **word-break & word-wrap:** Controls how text breaks or wraps inside containers.
    - `word-break: break-word;` lets long words break.
    - `word-wrap: break-word;` wraps text properly.

- **writing-mode:** Changes text direction (horizontal or vertical).

# CSS `object-fit` and `object-position` 

### `object-fit`

- Controls how an image or video fits within its container.
- Common values:    
    - **fill**: Stretches to fill container; may distort aspect ratio.
        
    - **contain**: Scales to fit container while preserving aspect ratio; may leave empty space.
        
    - **cover**: Scales and crops to fill container, preserving aspect ratio.
        
    - **none**: No resizing; uses original size.
        
    - **scale-down**: Displays smaller of `none` or `contain`.
        
#### Usage example:
```css
img {
  width: 300px;
  height: 200px;
  object-fit: cover;
}
```
### `object-position`
- Defines which part of the image/video is visible inside container, especially when cropped.
    
- Uses horizontal and vertical values (keywords like `top`, `center`, `bottom` or percentages).
    
- Default is `50% 50%` (center).
#### Usage example:
```css
img {
  object-position: top right;
}

object-position: <horizontal> <vertical>;  /*syntax*/

```
