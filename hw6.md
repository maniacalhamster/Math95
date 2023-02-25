# HW 6

Start: 11:47AM
End: 1:02PM
Spent: 1 hr 15 min

## Question

A) Build a sequence that is both arithmetic and geometric. How many such sequences can you build?

B) Can you build an arithmetic sequence w/ the following property: 
> There are distinct positive integers m and n such that the sum of the first m terms in the sequence equals the sum of the first n terms in the sequence?

## Prior Knowledge/Assumptions

**Arithmetic Seq**: difference in consec. terms are equal.

Can be written in the form:

```
A(n) = a + d(n-1)   // General form

A(1) = a            // First term
A(2) = a + d        // Second term
A(3) = a + 2d       // Third term
```

**Geometric Seq**: ratio of consec. terms are equal.

Can be written in the form:

```
G(n) = b * r^(n-1)  // General form

G(1) = b            // First term
G(2) = b * r        // Second term
G(3) = b * r^2      // Third term
```

**Summation Rules**:
```math
\sum_i^n F(i)  = F(0) + F(1) + \dots + F(n-1) + F(n)
```
---
```math
\begin{align*}
\sum_i^n k     &= k + k + \dots + k + k\\
               &= n(k)
\end{align*}
```
---
```math
\sum_i^n (a+b) = \sum_i^n (a) + \sum_i^n (b)
```
---
```math
\begin{align*}
\sum_i^n i     &= 0 + 1 + \dots + n-1 + n\\
               &= \frac{n(n+1)}{2}\\
\end{align*}
```
- Refer to [HW4 part B](./hw4.md#part-b) for derivation of above formula

## Attempt A1

A) want both arith and geometric seq from a generator function F(n)
- refer to above for constraints (must satisfy A(n) and G(n) for each n)

```
F(2) = F(1) + d
F(2) = F(1) * r

F(1) + d = F(1) * r
       d =        r
```

```
F(n) = a + d(n-1) = b * r^(n-1)
       a + d(n-1) = b * r^(n-1)
```

-- Too many unknowns, maybe try something different?

## Attempt A2

For purpose of time, just trying out whatever pops into my head without working things out algebraically

```
1, 2, 4, 8      // not arithmetic

1, 2, 3, 4      // not geometric

e, 2e, 3e,      // not arithmetic

1^e, 2^e, 3^e   // neither

1, 1, 1, 1      // works!
```

Realized it can be generalized to any base (b): 
```
A(n) = b + 0(n-1)   
G(n) = b * 1^(n-1)
```

A sequence that is both arithmetic and geometric:
- 1, 1, 1, 1, 1, ... 

This can also be applied to any non-zero base (b)
- 2, 2, 2, 2, 2, ...
- -9, -9, -9, -9, ...

**Ans**: There are infinitely many sequences that can be built following the generalized form above for non-zero value base (b)

## Attempt B1

Recall: Create an **arithmetic** sequence with the properties:
> There are distinct positive integers m and n such that the sum of the first m terms in the sequence equals the sum of the first n terms in the sequence?
 
```math
\sum_i^m F(i) = \sum_i^n F(i)\\
```
-
```math
\forall \{m,n \in N \quad | \quad m \neq n \}\\
```
-
```math
F(i) = b + d(i-1)
```
---

```math
\begin{align*}

\sum_i^n F(i) &= \sum_i^n (b + d(i-1)) \\
              &= \sum_i^n (b) + \sum_i^n d(i-1) \\
              &= n(b) + d\sum_i^n (i-1) \\
              &= n(b) + d(\sum_i^n (i) + \sum_i^n (- 1)) \\
              &= n(b) + d(\frac{n(n+1)}{2} + n (- 1)) \\
              &= \frac{2n(b)}{2} + d(\frac{n(n+1)}{2} + \frac{-2n}{2}) \\
              &= \frac{2n(b) + d(n(n+1) -2n)}{2} \\
              &= \frac{2nb + nd(n+1) - 2nd)}{2} \\
              &= \frac{2nb + nd((n+1) - 2))}{2} \\
              &= \frac{2nb + nd(n - 1)}{2} \\
\end{align*}
```

Knowing this, we want the sums of first n and first m to be equal so:

```math
\begin{align*}
\sum_i^n F(i)                           &= \sum_i^m F(i)\\
\frac{2nb + nd(n - 1)}{2}               &= \frac{2mb + md(m - 1)}{2}\\
2nb + nd(n - 1)                         &= 2mb + md(m - 1)\\
2nb - 2mb                               &= md(m - 1) - nd(n - 1)\\
b(2n - 2m)                              &= d(m(m - 1) - n(n - 1))\\
b                                       &= d\frac{m(m - 1) - n(n - 1)}{2(n - m)}\\
b\frac{2(n - m)}{m(m - 1) - n(n - 1)}   &= d
\end{align*}
```

**Ans**: Arithmetic Sequence of the following form will satisfy the prompt so long as condition above holds

```math
F(i) = b + d(i-1)
```

> There are distinct positive integers m and n such that the sum of the first m terms in the sequence equals the sum of the first n terms in the sequence?

## Checking answer

Let: 
- b = 4
- n = 4
- m = 5

```math
\begin{align*}
d &= b\frac{2(n-m)}{m(m-1) - n(n-1)}\\
  &= 4\frac{2(4-5)}{5(5-1) - 4(4-1)}\\
  &= 4\frac{2(-1)}{5(4) - 4(3)}\\
  &= 4\frac{-2}{20 - 12}\\
  &= 4\frac{-2}{8}\\
  &= \frac{-2}{2}\\
d &= -1\\
\end{align*}
```

Arith sequence generator formula:
```math
F(i) = b - 1(i-1)
```

First 5 terms:
```
F(1) = 4
F(2) = 3
F(3) = 2
F(4) = 1
F(5) = 0
```

### Realization

This ultimately boils down to whether or not the (n+1, n+2, ..., m-1, m) terms in the sequence add up to 0.
- or (m+1, m+2, ..., n-1, n) if n > m

I don't know how to thorouhgly test if the expression I derived relating `b` to `d` gaurantees this
- neither through extensively testing all case examples
- nor through a rigorous proof (e.g. by induction)