**==List in HTML==**
```html
<!-- Unordered List (bullets) -->
 <ul>                 <!-- unordered list-->
   <li>Apple</li>     <!-- list item-->    
   <li>Banana</li>
   <li>Cherry</li> 
</ul>

<!-- Ordered List (numbers) -->
<ol>
  <li>First step</li>
  <li>Second step</li>  
  <li>Third step</li>
</ol>

<!-- Definition List -->
<dl>
  <dt>HTML</dt>
  <dd>HyperText Markup Language</dd>
  <dt>CSS</dt>
  <dd>Cascading Style Sheets</dd>
  <dt>JavaScript</dt>
  <dd>A programming language used to create dynamic web pages.</dd>
</dl>

```
- `<dl>`: Container for the entire definition list.
- `<dt>`: Represents each term or item.
- `<dd>`: Contains the description or definition related to the term.

**==Tables==**

```html
<table>
  <thead>
    <tr>
      <th>Firstname</th>
      <th>Lastname</th>
      <th>Age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Priya</td>
      <td>Sharma</td>
      <td>24</td>
    </tr>
    <tr>
      <td>Arun</td>
      <td>Singh</td>
      <td>32</td>
    </tr>
    <tr>
      <td>Sam</td>
      <td>Watson</td>
      <td>41</td>
    </tr>
  </tbody>
</table>

```
code written with thead and tbody
![[Pasted image 20251021231403.png]]
![[Pasted image 20251021231415.png]]
![[Pasted image 20251021231427.png]]
![[Pasted image 20251021231917.png]]
```html
<th colspan="2">Data</th>
```


**==Forms in HTML==**
```html
<form action = "/action.php">
    <input type ="text" placeholder ="username">
    <input type ="password" placehodler ="password" >
    
</form>

<!--Forms are used to collect data from the user-->
```

![[Pasted image 20251022154705.png]]

**==Label in HTML==**
```html
<form action = "/action.php">
    <input type ="text" placeholder ="username">
    <input type ="password" placehodler ="password" >
    
    <input type = "radio" value = "class X" name = "class">class X
    <input type = "radio" value = "class XI" name = "class">class XI
 
</form>
```
Radio without label, forms this which can only be entered when pressed on checkbox
```html
<label for="id1">
    <input type="radio" value="class X" name="class" id="id1">
</label>

<label for="id2">
    <input type="radio" value="class X" name="class" id="id2">
</label>
```
![[Pasted image 20251022160233.png]]

CLasses and ID
![[Pasted image 20251022191411.png]]


==**checkbox==**
![[Pasted image 20251022191444.png]]
**==Textarea==**
![[Pasted image 20251022191511.png]]
==**SELECT ==**
![[Pasted image 20251022191848.png]]
![[Pasted image 20251022191911.png]]

**==Iframe tag==**
![[Pasted image 20251022205814.png]]

==**Video Tag**==
![[Pasted image 20251022205850.png]]

==**Frame Tag**== :- to frame webpages
```html
<frameset cols="25%,75%">
  <frame src="menu.html" name="list" ></frame>
  <frame src="home.html" name="home"></frame>
</frameset>
```