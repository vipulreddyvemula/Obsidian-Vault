
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
	
