---
date: 07-08-2023
type: Lecture
subject: Chapter 4
tags: lecture
Topic:: 
---
# [[Continuity]]
#MATH1051 

```toc
```


## 5.1 Definition of Continuity
We say that a function $f$ is *continuous at* $a$ if $f(a)$ is defined, $\lim_{ x \to a }f(x)$ exists and $\lim_{ x \to a }f(x)=f(a)$. ^cde39d

If $f$ is not continuous at $a$, we say that $f$ is *discontinuous at* $a$, or $f$ has a *discontinuity at* $a$.

A function may not be continuous at $x=a$ for a number of reasons.

### 5.1.1 Example

Let
$$
f(x)=\begin{cases}
x, & x\neq 0  \\
1, & x=0. 
\end{cases}
$$
Then $f$ has a discontinuity at $x=0$. This is because $f(0)=1$ while $\lim_{ x \to 0 }f(x)=0$. Hence the [[#^cde39d|third condition]] does not hold.

## 5.2 Continuity of Intervals

We say that $f$ is continuous on the *open* interval $(a,b)$ if $f$ is continuous at $c$, for all $c \in (a,b)$.

If $f$ is continuous on the *closed* interval $[a,b]$, then $f$ is continuous on $(a,b)$ and 
$$
\lim_{ x \to a^+ } f(x)=f(a), \quad \lim_{ x \to b^- } f(x)=f(b).
$$
You could think of a continuous function being one that on an interval can be drawn without lifting your pen.

## 5.3 Properties of Continuous Functions

If $f(x)$ and $g(x)$ are continuous at $x=a$ and $c$ is a constant, then the following functions are all continuous at $x=a$.
$$
\begin{align}
  & 1.& f(x)\pm g(x) \\
  & 2.& c \times f(x) \\
  & 3.& f(x) \times g(x) \\
  & 4.& \frac{f(x)}{g(x)}, \quad s.t.\quad g(a)\neq 0.
\end{align}
$$
Since the function $f(x)=x$ is continuous, this proves that any polynomial is continuous, and any ratio of polynomials is continuous, provided the denominator is not zero.

## 5.4 The Intermediate Value Theorem (IVT)

Suppose that $f$ is continuous on the closed interval $[a,b]$ and let $N$ be any number between $f(a)$ and $f(b)$, where $f(a)\neq f(b)$. Then there exists a number $c \in (a,b)$ such that $f(c)=N$.

### 5.4.1 Example

You want to show that there is at least one real solution for a function. Say, for example, show that the equation  $3x+2\cos x+5=0$ has one real solution for $x$.

First, you can just test out any two numbers in between the function that would make sense. Since we have a cosine ($\cos x$), we will use $-\pi$ or $\pi$ for one of our $x$.
$$
f(0) = 0+2+\cos(0)+5
$$
$$
f(0)=7,\quad 7>0
$$
Now that we shown that this $x$ bound is too big, we go for a smaller number, say $-\pi$.
$$
f(-\pi) = -3\pi+2\cos(-\pi)+5
$$
$$
f(-\pi)=-3\pi-2+5
$$
$$
f(-\pi) = 3(-\pi+1), \quad 3(-\pi+1)<0
$$
Since the higher bound of $x$ and the lower bound of $x$ are between 0, that means that there will be a real solution for $x$ at some point in between.

## 5.5 Application of the IVT (Bisection Method)
The *bisection method* is a procedure for approximating the zeros of a continuous function. It first cuts the interval $[a,b]$ in half (say, at a point $c$) and then decides in which of the smaller intervals ($[a,c]$, or $[c,b]$) the zero lies. This process is repeated until the interval is small enough to give a significant approximation of the zero itself.

We can present this bisection method as an *algorithm*:

1. Given $[a,b]$ such that $f(a)f(b)<0$, let $c=\frac{a+b}{2}$.
2. If $f(c)=0$ then quit; $c$ is a zero of $f$
3. If $f(c)\neq 0$ then:
	1. If $f(a)f(c)<0$, a zero lies in the interval $[a,c)$. So replace $b$ by $c$.
	2. If $f(a)f(c)>0$, replace $a$ by $c$.
4. If the interval $f[a,b]$ is small enough to give a precise enough approximation then quit. Otherwise, go to step 1.
