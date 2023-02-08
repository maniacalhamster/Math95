Start: 11:17PM  
End: 11:50PM

Spent: 33min

# Math 95 Homework 4

Stair-like structure problem.

![](images/2023-02-04-23-17-57.png)

Figure above has a base of 5

## Questions

1. You have 1176 identical square pieces. Can you use all the pieces to construct a stair-like structure?

2. Justify any formulas you used while solving part 1

## Observation

The number of squares in a base-n stair-like structure:
```
base 1: 1
[ ]

base 2: 1 + 2
[ ]
[ ] [ ]

base 3: 1 + 2 + 3
[ ]
[ ] [ ]
[ ] [ ] [ ] 

```

base n = 
```math
\sum_{i=1}^n i
```

## Work

Well I know there's a "Series" formula for sums and the derivation goes like so:

```math
\begin{align*}
\sum_{i=1}^n i  &= 0 + 1 + 2 + ...  + n-2 + n-1 + n \\
                &= (0 + n) + (1 + n-1) + 2 + (n-2) + ...  \\
                &= n + n + n + ...  \\
\end{align*}
```

Actually wait, I realized this is more intuitive with boxes:

```
base 5:
[1]
[2] [ ] 
[3] [ ] [ ] 
[4] [ ] [ ] [ ] 
[5] [ ] [ ] [ ] [ ] 

// boxes can be rearranged like so

[1]
[4] [ ] [ ] [ ] 
[2] [ ] 
[3] [ ] [ ] 
[5] [ ] [ ] [ ] [ ] 

// Like the equation above, we get groups of 5:

[1] [4] [ ] [ ] [ ] 
[2] [ ] [3] [ ] [ ] 
[5] [ ] [ ] [ ] [ ] 

// base 5 has 5(3) = 15 boxes
```

What about for even bases?
```
base 6:
[1]
[2] [ ] 
[3] [ ] [ ] 
[4] [ ] [ ] [ ] 
[5] [ ] [ ] [ ] [ ] 
[6] [ ] [ ] [ ] [ ] [ ]

// Rearrangment
[1]
[5] [ ] [ ] [ ] [ ] 
[2] [ ] 
[4] [ ] [ ] [ ] 
[6] [ ] [ ] [ ] [ ] [ ]
[3] [ ] [ ] 

// Grouping into 6s
[1] [5] [ ] [ ] [ ] [ ]
[2] [ ] [4] [ ] [ ] [ ]
[6] [ ] [ ] [ ] [ ] [ ]
[3] [ ] [ ]

// Bas 6 has 6(3 + 1/2) = 21
```

It seems like the general formula for the number of boxes would look like:

```math
\begin{align*}
n(n/2 + 1/2) \\
\\
= \frac{(n)(n+1)}{2}

\end{align*}
```

---

To answer part 1 though:

We just have to check if there is an Integer value N we can plug into the equation above to get 1176. So:
- we set the LHS to 1176
- we solve for n
- check if n is a whole number

```math
\begin{align*}
1176    &= \frac{(n)(n+1)}{2}\\
2352    &= n(n+1)\\
\\
2352    &= n^2+n\\
2352+1/4&= n^2+n+1/4\\
2352+1/4&= n^2+2(n)(1/2)+(1/2)^2\\
\\
2352+1/4&= (n+1/2)^2\\
\sqrt{9408/4+1/4}&= n+1/2\\
-1/2 \pm \sqrt{9409/4}&= n\\
\\
-1/2 \pm \sqrt{9409}/2&= n\\
-1/2 \pm 97/2&= n\\
\\
\{-1/2 - 97/2, -1/2 + 97/2\}&= n\\
\{-98/2, 96/2\}&= n\\
\\
\{-49, 48\}&= n\\
\end{align*}
```

Looks like n=48 is a valid solution

> Note: we can't have negative base structures since they weren't defined.

## Checking answer

```math
\begin{align*}
48(48+1)/2  &=\\
            &=  48*49/2\\
            &=  24*49\\
            &= 1176
\end{align*}
```

## Part B 

Figured out the algebraic proof:

$$
\begin{align*}
    2 \sum_i^n i    &= \sum_i^n i + \sum_i^n i \\
                    &= (0 + 1 + 2 + ... + n-2 + n-1 + n)\\
                    &  (n + n-1 + n-2 + ... + 2 + 1 + 0)\\
                    &= (0+n) + (1+n-1) + (2+n-2) + ... + (n-2+2) + (n-1+1) + (n+0) \\
                    & \text{There are n+1 terms (0 through n)}\\
                    &= n + n + n + ... + n + n + n \\
    2 \sum_i^n i    &= n(n+1)\\
      \sum_i^n i    &= \frac{n(n+1)}{2}\\
\end{align*}
$$
