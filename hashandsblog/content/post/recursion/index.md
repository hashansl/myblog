+++
title = "Recursion"
date = "2025-06-18"
author = "Hashan Fernando"
description = "As with so many things in life, something that I used to think was really difficult and cumbersome turns out to be really easy if you just take the time to understand it."
categories = ["DSA"]
tags = ["Algorithms", "DSA"]
toc = true  # Table of contents (requires config below)
image = 'card-img.jpg'
hideNav = 'false'

+++

As a student of Statistics and Data Science, I used to overlook certain topics in Data Structures and Algorithms. To be honest, I never really needed them in my research work, so I let myself believe they weren’t relevant. But as I started taking on different kinds of projects, especially ones involving coding challenges and system design, I realized I was missing something important.

One of the concepts I struggled with the most was **recursion**. It felt confusing and even a bit intimidating. I would look at recursive code and wonder, *Where does it end? How does it even work?* So, I ignored it until I couldn’t anymore.

Eventually, I decided to face it head-on. And when I did, I felt kind of silly… because it wasn’t as complicated as I had built it up to be.

---

## Where It Went Wrong

The part that always tripped me up was understanding what happens after a function calls itself. I couldn’t wrap my head around the idea that the code *after* the recursive call still gets executed—*but only after* the function starts returning.

Back then, I had this image in my mind that recursion just keeps going deeper and deeper, never to return. So I gave up. But what I didn’t grasp was the power of the **base case**—that small but crucial condition that stops the recursion from going on forever.

Once I truly understood that each recursive call pauses and stacks up, waiting for the one below it to finish, it clicked. Everything after the recursive call *does* run—just in reverse order as the call stack unwinds. It was like watching a row of dominoes fall… and then suddenly realizing they were being picked up in reverse.

---

## Base case

Recursion function needs to have a base case, otherwise it will keep calling itself and never return. The base case is the condition that stops the recursion. For example, in the following code, the base case is when `n` is equal to 0,

```python
def factorial(n):
    if n == 0:
        return 1  # Base case
    else:
        return n * factorial(n - 1)  # Recursive case
```
In this example, the function `factorial` calculates the factorial of a number `n`. If `n` is 0, it returns 1 (the base case). Otherwise, it multiplies `n` by the factorial of `n - 1`, which is the recursive case.

## Stack frames

When a recursive function is called, it creates a new stack frame for each call. The stack is a data structure that stores the function calls in a last-in-first-out (LIFO) order. Each time the function calls itself, a new stack frame is created, and when the function returns, the stack frame is removed from the stack.

To understand this better, let's look at the example of calculating the factorial of a number using recursion. When you call `factorial(3)`, the following happens,

```python
factorial(3)  # Call 1
    if n == 0:
        return 1  # Base case
    else:
        return 3 * factorial(3 - 1)  # Recursive case

```

```python
factorial(2)  # Call 2
    if n == 0:
        return 1  # Base case
    else:
        return 2 * factorial(2 - 1)  # Recursive case

```

```python
factorial(1)  # Call 3
    if n == 0:
        return 1  # Base case
    else:
        return 1 * factorial(1 - 1)  # Recursive case

```

```python
factorial(0)  # Call 4
    if n == 0:
        return 1  # Base case
    else:
        return 0 * factorial(0 - 1)  # Recursive case
```
In this example, the function `factorial` is called four times. Each call creates a new stack frame. The first call is `factorial(3)`, which checks if `n` is 0. Since it is not, it calls `factorial(2)`. This process continues until it reaches the base case, `factorial(0)`, which returns 1.
After reaching the base case, the function starts returning back through the stack frames. The return value of `factorial(0)` is 1, which is then used to calculate `factorial(1)`, and so on, until it finally returns the result for `factorial(3)`.

This is how recursion works. Each time the function calls itself, it creates a new stack frame, and when it reaches the base case, it starts returning back through the stack frames until it reaches the original call.

It is also important to understand that recursion can lead to stack overflow if the recursion depth is too high. This happens when the function calls itself too many times without reaching the base case.

![Recursion illustration](card-img.jpg)
*Figure: A visual metaphor for recursion: like a robot entering a spaceship again and again.*

## Conclusion

Silly thing I understood is code after the recursive call runs only after the function starts returning! Also all the stack functions will be executed in reverse order! The first function call will be the last one to return! This solved my confusion about recursion and made it much easier to understand.

I hope this post helps you understand recursion better. It’s not as scary as it seems once you get the hang of it. Just remember to always define a base case, and you’ll be on your way to mastering this powerful technique.
