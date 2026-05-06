
# GCD
## 1) Euclidean Algorithm (Division Method)

**Principle:**
gcd(a,b) = gcd(b,a%b);
**Steps**
1. Divide `a` by `b`
2. Replace `(a, b)` with `(b, a mod b)`
3. Repeat until `b = 0`
4. GCD = `a`

**Example:** gcd(48,18)

```
48 % 18 = 12
18 % 12 = 6
12 % 6 = 0
→ GCD = 6
```

**Complexity:** O(log n) → very fast

**Key Point:**
Efficient and preferred in exams and programming.

---
## 2️⃣ Repeated Subtraction Method

**Principle:**
Subtract smaller number from larger repeatedly until both become equal.
**Steps**
1. If `a > b` → `a = a − b`
2. If `b > a` → `b = b − a`
3. Repeat until `a = b`
4. GCD = `a`
**Example:** gcd(48,18)

```
48−18=30
30−18=12
18−12=6
12−6=6
→ GCD = 6
```

**Complexity:** Slow (can take many steps)

NOTE:- GCD(a,b)=GCD(a-b,b);

---

## 3) To check if a number is prime or not
```cpp
bool isPrime(int n){  
if(n <= 1) return false;  
for(int i = 2; i * i <= n; i++){  
if(n % i == 0) return false;  
}  
return true;  
}
```
##### Complexity
O(√n)

#####  Key Idea
- Divisors come in pairs → only check till **√n**
---


## 5)📐 Quadratic Sequences (Second-Order)

## 🧩 Core Concept

A sequence where the common difference increases by a constant amount each time.

- First Differences: Not constant (e.g., $+2, +4, +6 \dots$)
- Second Differences: Constant (e.g., $+2, +2, +2 \dots$)

## 🔢 The $n$-th Term Formula

The general form is:  
$$T_n = an^2 + bn + c$$

## How to find $a, b,$ and $c$:

1. Find $a$: $2a = \text{second difference}$
2. Find $b$: $3a + b = \text{first difference (between term 1 and 2)}$
3. Find $c$: $a + b + c = \text{the first term}$

---

## ➕ Sum of the Series ($S_n$)

The sum is always cubic. Use the standard summation identities:

|Term|Summation Formula $\sum$|
|---|---|
|$n^2$|$\frac{n(n+1)(2n+1)}{6}$|
|$n$|$\frac{n(n+1)}{2}$|
|$c$|$cn$|

Full Formula:  
$$S_n = a\left[\frac{n(n+1)(2n+1)}{6}\right] + b\left[\frac{n(n+1)}{2}\right] + cn$$

---

## 💡 Quick Example

Sequence: $3, 8, 15, 24 \dots$

1. Differences: $5, 7, 9$ (1st diff); 2 (2nd diff)
2. Solve $a$: $2a = 2 \implies a = 1$
3. Solve $b$: $3(1) + b = 5 \implies b = 2$
4. Solve $c$: $1 + 2 + c = 3 \implies c = 0$  
    Result: $T_n = n^2 + 2n$

---


Yet another array problem
eucledian algorithm
