# HW 7

## Question

a) Build 3 diff non-zero arithmetic sequences w/ the following propery:
- $\{m, n \in Z \quad | \quad m\neq n\}$
- $\sum\limits_{k=0}^m A(k) = \sum\limits_{k=0}^n A(k)$

b) Can you build an arithmetic sequence with the following property:
> the sum of any number of consecutive terms, starting with the first term, is three times the square of the number of consecutive terms?

- $\sum\limits_{k=0}^n A(k) = 3n^2 $

> Where $A(k)$ is a function modeling an Arithmetic sequence such that $k^{th}$ term in the arithmetic sequence

## Knowns / Assumptions

**Arithmetic Seq**: difference in consec. terms are equal.

Can be written in the form:

```
A(n) = a + dn       // General form

A(0) = a            // First term
A(1) = a + d        // Second term
A(2) = a + 2d       // Third term
```

## Attempt A1

```math
\begin{align*}
\sum_{k=0}^m A(k)   &= \sum_{k=0}^n A(k) + \sum_{k=n+1}^m A(k)\\
\sum_{k=0}^n A(k)   &= \sum_{k=0}^n A(k) + \sum_{k=n+1}^m A(k)\\
0                   &= \sum_{k=n+1}^m A(k)\\
\end{align*}
```

```math
\begin{align*}
\sum_{k=n+1}^m A(k) &= (a + d(n+1)) + (a + d(n+2)) + ... + (a + d(m-1)) + (a + d(m))\\
\sum_{k=n+1}^m A(k) &= (a + d(m)) + (a + d(m-1)) + ... + (a + d(n+2)) + (a + d(n+1))\\
\\
2\sum_{k=n+1}^m A(k)&= ((a + a) + (a + a) + ... + (a + a) + (a + a))\\
                    &+  d(n+1 + m) + d(n+2 + m-1) + ... + d(m-1 + n+2) + d(m + n+1)\\
\\
2\sum_{k=n+1}^m A(k)&= (m-n)(2a) + (m-n)(d(n+1 + m))\\
                    &= (m-n)(2a + d(n+1+m))\\
\end{align*}
```

```math
\begin{align*}
2(0)                    &= (m-n)(2a + d(n+1+m))\\
2(0)                    &= (2a + d(n+1+m))\\
-\frac{1}{2}d(n+1+m)    &= a\\
\end{align*}
```

Play around with sliders for $n, m,$ and $d$ in [this desmos][desmos]

Examples: 

F(k) = 12.5 -2.5k
k       | F(k)  | $\sum\limits_0^k$
---     | ---:  | ---:
 0      | 12.5  | 12.5
 1      | 10.0  | 22.5
 2 (n)  |  7.5  | **30.0**
 3      |  5.0  | 35.0
 4      |  2.5  | 37.5
 5      |  0    | 37.5
 6      | -2.5  | 35.0
 7 (m)  | -5.0  | **30.0**

F(k) = -4.5 + k
k       | F(k)  | $\sum\limits_0^k$
---     | ---:  | ---:
 0      | -4.5  | -4.5
 1      | -3.5  | -8.0
 2 (n)  | -2.5  | **-10.5**
 3      | -1.5  | -12.0
 4      | -0.5  | -12.5
 5      |  0.5  | -12.0
 6 (m)  |  1.5  | **-10.5**

F(k) = 5 - k
k       | F(k)  | $\sum\limits_0^k$
---     | ---:  | ---:
 0      |  5.0  |  5.0
 1      |  4.0  |  9.0
 2      |  3.0  | 12.0 
 3      |  2.0  | 14.0
 4 (n)  |  1.0  | **15.0**
 5 (m)  |  0.0  | **15.0**

## Attempt B1

```math
\begin{align*}
\sum_{k=0}^n A(k)   &= a + (a + d) + (a + 2d) + ... + (a + d(n-2)) + (a + d(n-1)) + (a + d(n)) \\
\sum_{k=0}^n A(k)   &= (a + dn) + (a + d(n - 1)) + (a + d(n-2)) + ... + (a + 2d) + (a + d) + a \\
\\
2\sum_{k=0}^n A(k)  &= a + (a + d) + (a + 2d) + ... + (a + d(n-2)) +  (a + d(n-1)) + (a + d(n)) \\
                    &+ (a + dn) + (a + d(n - 1)) + (a + d(n-2))... + (a + 2d) + (a + d(n)) + a \\
\\
2\sum_{k=0}^n A(k)  &= (a + (a + dn)) + (a + d + a + d(n-1)) + (a + 2d + a + d(n-2)) + ... \\
                    &= (2a + dn) + (2a + dn) + (2a + dn) + ... \\
                    &= (n+1)(2a + dn)\\
\\
\sum_{k=0}^n A(k)   &= \frac{1}{2}(n+1)(2a + dn)\\
\end{align*}
```

> We want the above to be equal to $3n^2$

```math
\begin{align*}
3n^2                                &= \frac{1}{2}(n+1)(2a + dn)\\
6n^2                                &= (n+1)(2a + dn)\\
\frac{6n^2}{n+1}                    &= (2a + dn)\\
\frac{6n^2}{n+1}-dn                 &= 2a\\
\frac{6n^2}{2(n+1)}-\frac{dn}{2}    &= a\\
\end{align*}
```

Well as it seems like the value of $a$ relies on a select value of $n$, I don't believe a sequence can be generated where the property holds true for ALL n in the series.

## Attempt B2

For $n=0$, $3n^2 = 0 = \sum F(k) = a$

Meaning, we know that a must be 0

```math
\begin{align*}
\frac{6n^2}{n+1}                    &= (2a + dn)\\
\frac{6n^2}{n+1}                    &= dn\\
\frac{6n}{(n+1)}                 &= d\\
\end{align*}
```

Again it looks like the value of $d$ relies on a select value of $n$, so a value doesn't exist where it holds true for ALL n in the series.

[This graph](desmos2) shows what we want the sum of consecutive terms to be equal to (dotted purple) as well as the actual sum of consecutive terms (red line)

Still trying to figure out why this makes sense logically

[desmos]:https://www.desmos.com/calculator/21v1tsybfu
[desmos2]:https://www.desmos.com/calculator/pjz89yn2ka