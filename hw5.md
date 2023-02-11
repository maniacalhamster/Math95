# Math 95 Homework Five

Start: 1:30 PM
End: 2:05 PM
Time: 35 min

Addendum: +20min to address part B
Total Time: 55min

> Note: Same stair-like structures from last week, but this time using toothpicks to construct the sides of the stairs

## Question
1. Is it possible to use exactly 2628 identical toothpicks to create a stair-like structure?
2. Attempt to justifyu any formulas used in part (a)

## Observations

```
b = 1, n = 1, t = 4
 __ 
|__|

b = 2, n = 3, t = 4 + 2(3) = 10
 __ 
|__|__
|__|__|

b = 3, n = 6, t = 10 + 2(3) + 1(2) = 18
 __ 
|__|__
|__|__|__
|__|__|__|

b = 4, n = 10, t = 18 + 2(3) + 2(2) = 28
 __
|__|__
|__|__|__
|__|__|__|__
|__|__|__|__|
```

> Think of building the structure:
- starting from the bottom left corner and 
- expanding outwards with each layer
    - always introduce 2(3) toothpicks for the topleft and bottomright
    - introduce x(2) toothpicks  for each of the intermediate "steps" generated

Noticed that for structure of base (b), expanding to the next base (b') would require (b-1) intermediate "steps" be generated.

In other words, for the current base, we introduced 2(b-1) toothpicks for the intermediate steps as well as 2(3) toothpicks for the new "corners".

Formula for the number of toothpicks used to generate a (b) base structure would look like so:

```math
\begin{align*}
T(b)    &= 4 + \delta(b-1)\times 6(b-1) + \delta(b-2)\times 2(\sum_{i=0}^{b-2} i) \\
        &= 4 + \delta(b-1)\times 6(b-1) + \delta(b-2)\times 2(\frac{(b-2-1)(b-2)}{2}) \\
        &= 4 + \delta(b-1)\times 6(b-1) + \delta(b-2)\times (b-3)(b-2)
\end{align*}
```

Where the dirac-delta equation is defined as:
```math
\delta(x) = \begin{cases}
                x\leq 0 & 0\\
                x > 0   & 1
    \end{cases}
```

## Work

We need to check if there exists a (b) such that $T(b) = 2628$:
```math
\begin{align*}
2628    &= 4 + 6(b-1) + (b-3)(b-2) \\
        &= 4 + 6b -6 + b^2 -5b+6 \\
        &= 4 + b + b^2 \\
2624    &= b + b^2 \\
        &= b(1 + b) \\
        &\approx b^2 \\
\sqrt{2624}  &\approx b\\
51.22        &\approx b
\end{align*}
```

Now we can test (51, 52) to check:

```math
51(52) = 2652 \neq 2624
```

## Final Answer

No, we cannot form a stair-like structure with exactly 2628 toothpicks

---

## Part B

```math
\begin{align*}
T(0)    &= 4 \\
T(1)    &= 4 + 2(3) = 10 \\
\\
T(2)    &= T(1) + 2(3) + 2(1) = 18 \\
T(3)    &= T(2) + 2(3) + 2(2) = 28 \\
T(4)    &= T(3) + 2(3) + 2(3) = 40 \\
T(5)    &= T(4) + 2(3) + 2(4) = 40 \\
\\
&\text{Generalized (for t > 1):} \\
\\
T(b)    &= T(b-1) + 2(3) +  2(b-1) \\
T(b-1)  &= T(b-2) + 2(3) +  2(b-2) \\
T(b-2)  &= T(b-3) + 2(3) +  2(b-3) \\
&\text{... and so on continues 'til T(b-x) hits T(1) and T(0)}
\end{align*}
```

> Note that for $b > 0$, each $T(b)$ always includes a $2(3)$ term. 
  - Since we build up $T(b)$ by adding on $T(b-1)$, $T(b-2)$, ... we are essentially adding up all the $2(3)$ terms. 
  - Since this term only gets added for $b > 0$, we use $\delta(b-1)$ (will be zeroed out for any $b < 1$)
  - Also since we add up the $2(3)$ for all $b > 0$ in $T(b)$, the number of terms we add up ends up being $b-1$

> Note that for $b > 1$, each $T(b)$ always includes a $2(b-1)$ term.
  - Since we build up $T(b)$ by adding on $T(b-1)$, $T(b-2)$, ... we are essentially adding up all the $2(b-1)$ terms. 
  - Since this term only gets added for $b > 1$, we use $\delta(b-2)$ (will be zeroed out for any $b < 2$)
  - Summing up the $2(b-1)$ terms will look like $\sum_{i=0}^{b-1} i$

Thus the equation used for the number of toothpicks in a base (b) stair structure is derived:

```math
T(b) = 4 + \delta(b-1)\times 6(b-1) + \delta(b-2)\times 2(\sum_{i=0}^{b-2} i)
```