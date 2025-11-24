# CSS Flexbox – Quick Notes (with code)

## 1. What flexbox is

- Flexbox is a layout system for arranging items in **one direction** (row or column).   
- It makes it easy to **align**, **space**, and **resize** items inside a parent container.

---

## 2. Making a flex container

```css
.container {
  display: flex;      /* turn this element into a flex container */
}
```

- All **direct children** of `.container` become **flex items**.
- After this, flex properties like `justify-content`, `align-items` etc. start working.

---

## 3. Direction: row vs column
```css
.container {
  display: flex;
  flex-direction: row;      /* items: left → right (default) */
  /* flex-direction: column;   items: top → bottom */
}
```

- `row` → horizontal.
- `column` → vertical.

---

## 4. Centering items

```css
.container {
  display: flex;
  justify-content: center;  /* center on main axis */
  align-items: center;      /* center on cross axis */
}
```

- With `flex-direction: row` → main axis is horizontal.
- With `flex-direction: column` → main axis is vertical.
    

**Full‑page center (like your form):**
```css
body {
  margin: 0;
  min-height: 100vh;
  display: flex;
  justify-content: center;  /* left–right center */
  align-items: center;      /* top–bottom center */
}
```

---

## 5. Wrapping and gaps
```css
.container {
  display: flex;
  flex-wrap: wrap;   /* allow items to move to next line */
  gap: 16px;         /* space between flex items */
}
```

- `flex-wrap: nowrap` (default) → one line.   
- `wrap` → items go to new row/column when no space.

---

## 6. Controlling item size

```css
.item       { flex: 1; }           /* grow and share space equally   */
.item-big   { flex: 2; }           /* takes 2× space of flex:1 item  */
.item-fixed { flex: 0 0 200px; }   /* fixed ~200px, no grow/shrink   }
```
- `flex` is shorthand for: `flex-grow flex-shrink flex-basis`.
- Higher `flex` value → wider item (when there is extra space).

---

## 7. When to use flexbox

- Centering cards/forms in the page.
- Horizontal navbars or button rows.
- Simple two‑column layouts (sidebar + main).
- Any situation where you want easy spacing + alignment in one direction.

