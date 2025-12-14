**==UNITS IN CSS - RELATIVE==**
- %
- em
- rem
![[Pasted image 20251027160632.png]]
![[Pasted image 20251027160644.png]]
![[Pasted image 20251027160702.png]]
![[Pasted image 20251027160730.png]]


# CSS Position Property

The `position` property in CSS specifies how an element is positioned in the document. It works together with `top`, `right`, `bottom`, and `left` offset properties.

## Values

### 1. `static`

Default value. Elements are positioned according to the normal flow of the document.

```css
div {
 position: static; /* This is the default,you usually don't need to set it */
}
```

<!-- `top`, `left`, `right`, and `bottom` have no effect here. -->

---

### 2. `relative`

Element is positioned relative to its normal position. Offsets move it, but the space it would take up remains.

```css
div {
  position: relative;
  top: 20px;   /* Moves down by 20px */
  left: 10px;  /* Moves right by 10px */
}
```

<!-- Other elements act as if the div hasn't moved. -->

---

### 3. `absolute`

Element is removed from the normal flow and positioned relative to the nearest positioned ancestor, or the viewport if none.

```css
div {
  position: absolute;
  top: 40px;   /* 40px from top edge of positioned ancestor */
  left: 60px;  /* 60px from left edge of positioned ancestor */
}
```

<!-- Useful for overlays and tooltips. -->

---

### 4. `fixed`

Element is removed from normal flow and positioned relative to the browser window (viewport). Stays in place when scrolling.

```css
div {
  position: fixed;
  bottom: 10px;  /* 10px from bottom of viewport */
  right: 20px;   /* 20px from right edge */
}
```

<!-- Common for sticky navbars or back-to-top buttons. -->

---

### 5. `sticky`

Element toggles between `relative` and `fixed`, depending on the scroll position. It acts as `relative` until it crosses a threshold, then becomes `fixed`.

```css
div {
  position: sticky;
  top: 0;  /* Sticks to the top once you scroll past it */
}
```

<!-- Great for sticky headers and sidebars. Supported in all modern browsers. -->

<hr>

# CSS Float Notes

- Use `float` to make elements like images float left or right.
- Surrounding text flows around the floated element.
- Clear the float using `clear: both` to avoid layout issues.
#### Example:
```css
img {
  float: left;
  margin-right: 10px; /* space between image and text */
  width: 150px;
}
```
This floats the image to the left, adds spacing, and lets text wrap on the right.

- The `clear` property controls whether an element can be adjacent to floated elements or must move below them.
- It is often used after floated elements to avoid text or elements wrapping beside floats.
### Values(Clear):

- `none` (default) — Allows elements to wrap next to floats.
- `left` — Element moves below left floats.
- `right` — Element moves below right floats.
- `both` — Element moves below all floats (left and right).
#### Example:
```css
selector{
  clear: left; /*This element will be positioned below all floated elements*/
}
```