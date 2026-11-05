# Matplotlib 

## Import

```
import matplotlib.pyplot as plt
```

## 1. Line plot

```
plt.plot(x, y)
plt.show()
```

If X is omitted, default X values are `0,1,2,...`.

## 2. Bar chart

```
plt.bar(x, y)     # Vertical bars
plt.barh(x, y)    # Horizontal bars
plt.show()
```

## 3. Pie chart

```
plt.pie(values, labels=names, autopct='%1.1f%%')
plt.show()
```

`autopct` displays percentages.

## 4. Scatter plot

```
plt.scatter(x, y)
plt.show()
```

## 5. Histogram

```
plt.hist(data, bins=5)
plt.show()
```

`bins` specifies the number of intervals.

## 6. Titles and labels

```
plt.xlabel("X Axis")
plt.ylabel("Y Axis")
plt.title("My Graph")
plt.legend()
plt.grid()
plt.show()
```

## 7. Colours, markers, line styles

```
plt.plot(x, y, color='red')
plt.plot(x, y, marker='o')
plt.plot(x, y, linestyle='dashed')
plt.plot(x, y, linewidth=2)
plt.plot(x, y, markersize=8)

plt.plot(x, y, 'o:r')
# o = circle
# : = dotted
# r = red
```

Marker codes:

- `o` — Circle
    
- `*` — Star
    
- `s` — Square
    
- `^` — Triangle
    
- `x` — Cross
    

Line styles:

- `'-'` — Solid
    
- `'--'` — Dashed
    
- `':'` — Dotted
    
- `'-.'` — Dash-dot
    

Colours: `r`, `g`, `b`, `k`, `y`.

## 8. Multiple lines

```
plt.plot(x, y1, label="Line 1")
plt.plot(x, y2, label="Line 2")
plt.legend()
plt.show()
```

## 9. Multiple figures / subplots

```
plt.figure()  # New figure
plt.plot(x, y)

plt.figure()
plt.bar(x, y)

plt.show()
```

```
plt.subplot(1, 2, 1)  # 1 row, 2 columns, plot 1
plt.plot(x, y)

plt.subplot(1, 2, 2)  # Plot 2
plt.bar(x, y)

plt.tight_layout()
plt.show()
```

## 10. Save chart

```
plt.savefig("chart.png")
plt.show()
```

## Actual PYQ — Nov 2025 End Sem, Q5(b), 5 marks

**Plot student names vs marks using a bar chart.**

```
import matplotlib.pyplot as plt

names = ["Ram", "Sam", "Priya"]
marks = [80, 90, 75]

plt.bar(names, marks)
plt.xlabel("Student Names")
plt.ylabel("Marks")
plt.title("Student Marks")
plt.show()
```

## Actual PYQ — Nov 2024 End Sem, Q3, 10 marks

**Bar chart + pie chart + placement trend line chart**

```
# Bar
plt.bar(companies, students_placed)
plt.show()

# Pie
plt.pie(students_placed, labels=companies,
        autopct='%1.1f%%')
plt.show()

# Line
plt.plot(years, placement_trend, marker='o')
plt.xlabel("Year")
plt.ylabel("Placement %")
plt.title("Placement Trend")
plt.show()
```

Assumes the data lists are already defined.

## Memory Tricks

|Function|Chart|
|---|---|
|`plot()`|Line|
|`bar()`|Vertical bar|
|`barh()`|Horizontal bar|
|`pie()`|Pie|
|`scatter()`|Scatter|
|`hist()`|Histogram|
|`show()`|Display|
|`savefig()`|Save image|

**Standard exam pattern:** Import → Data → Plot → Labels → Title → Show.