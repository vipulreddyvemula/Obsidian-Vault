### `datetime` Module

#### Import
```py
import datetime
```
Used for working with dates and times.

---
#### Create DateTime
```python
datetime.datetime(year, month, day)
```
or:
```py
datetime.datetime(year, month, day, hour, minute, second)
```

Example:
```python
x = datetime.datetime(2025, 8, 13, 10, 30, 0)
```

Output:
```
2025-08-13 10:30:00
```

---
#### Current Date/Time
```python
datetime.datetime.now()
```
Returns current date and time.

---
#### `timedelta`

Used to represent/add a time duration.
```py
x = datetime.datetime.now() + datetime.timedelta(hours=5)
```
Can be used for adding/subtracting time. Date automatically changes if time crosses midnight.

Mental model:
```
datetime   → when
timedelta  → how much time
```

---
#### `strftime()`
Converts a datetime into a **formatted string**.
```py
x.strftime(format)
```

Example:
```py
x.strftime("%A, %B %d, %Y")
```
#### Important format codes
```py
%Y → year (4 digit)
%m → month number
%d → day
%A → full weekday name
%B → full month name
%H → hour
%M → minute
%S → second
```

Example:
```py
x.strftime("%Y%m%d_%H%M%S")
```

Output:
```
20250812_143045
	```