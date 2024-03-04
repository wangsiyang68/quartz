# Extended Euclidean Algorithm
---
**Key idea**: In addition to finding the gcd of r0and r1, it returns s and t such that $s*r0 + t*r1 = gcd(r0,r1)$. Goes a step further than [[Euclidean Algorithm]]

**Steps**
Recursive formula
```
function extended_gcd(a, b)
    (old_r, r) := (a, b)
    (old_s, s) := (1, 0)
    (old_t, t) := (0, 1)
    
    **while** r ≠ 0 **do**
        quotient := old_r **div** r
        (old_r, r) := (r, old_r − quotient × r)
        (old_s, s) := (s, old_s − quotient × s)
        (old_t, t) := (t, old_t − quotient × t)
    
    **output** "Bézout coefficients:", (old_s, old_t)
    **output** "greatest common divisor:", old_r
    **output** "quotients by the gcd:", (t, s)    
```

**Usefulness in DHKE**
It helps to compute inverses mod n. 

First, remember that Inverses are defined such that $a * a^{-1} = 1\ mod\ polynomial(n)$

Assuming that the remainder is 1 (since seleceted polynomial(n) is "prime" in the GF),  I can represent $gcd(a,polynomial(n)) = 1$ as $s*polynomial(n)+t*a = 1$. 

Remembering that it is in a polynomial(n) GF, we can represent it as  $(s*polynomial(n)+t*a)\ mod \ polynomial(n) = 1$, which can be simplified into  $(t*a) = 1\ mod \ polynomial(n)$

Therefore, the coefficient t of EEA is the inverse of a

#foc