---
title: Algorithm Complexity (aka. the "Big Oh" thing)
---

# Algorithm Complexity (aka. the "Big Oh" thing)

**Algorithm complexity** is a measure of how much it takes to run a certain algorithm. The "it" thing could be either **time** or **memory**. The longer or larger the algorithm takes to complete their operation.

The shortest possible value of complexity would be **O(1)**, where for every number of inputs, the algorithm will always require the same level of time (or memory space) from. Oh, wait, you can also make it **O(0)**, meaning that the algorithm does and returns nothing!

The highest value? Infinite. And of course, we would really want to build algorithms as efficient as possible. Having to wait too long or consume large memory (RAM) for a program to load is mostly unacceptable and a waste of time, electricity, and even your patience.

## The Big Oh notation

The "big oh" notation is always written as **O(...)**, where you fill in the level of complexity inside the brackets, and in most cases, using the algebraic notation of ***n***, such as **O(*n*)**.

It is also possible to include more than one algebraic value, such as **O(*x*(*y*+1))**. Basic algebra rules do apply here, so **O(*n*)** means that the algoritm "will run dependent on the number of *n*-type inputs," like:

```ts
/**
 * Utility method to get a sum of numbers in JavaScript
 * @param items An array of numeric items
 * @returns The sum or all items
 */
function sum(items: Number[]) {
    let i;
    let sum = 0;
    for (i = 0; i < items.length; i++) {
        sum += items[i];
    }
    return sum;
}
```

Meanwhile, an algorithm that takes **O(*x*(*y*+1))** means that it dependents on the size of each variables *x* and *y*, and even though there are no items of *y*, the algorithm will return a complexity of **O(*x*(1))**, i.e. **O(*x*)**.

There are some cases where you might see the complexity be **O(*n*<sup>2</sup>)**, which means that the *n* is being used the *n* number of times. Like drawing a square full of asterisks in C:

```c
#import <stdio.h>

void draw_square(int size) {
    int i, j;
    for (i = 0; i < size; i++) {
        for (j = 0; j < size; i++) {
            printf("*");
        }
        printf("\n");
    }
}
```

And, you may also see things like **O(log(*n*))**. It means none other than **O(<sup>2</sup>log(*n*))** or **O(log<sub>2</sub>(*n*))**, since we mostly care about numbers in the powers of 2. You might found it in some advanced algorithms like binary trees, and that means an input of 8 items will return **O(3)** (because 8 = 2<sup>3</sup>), and an input of 12 items will return **O(4)** (because 12 ≈ 2<sup>3.585</sup>, and we round that 3.585 up to become 4).

In reality, the complexity of algorithms may not be as accurate as it is described. For example, a complexity of an algorithm described as **O(*n*<sup>2</sup>)** may actually be an **O(*n*(*n*+(*x*-1))+*y*)**. It's okay to simplify these to get the gist of the complexity.
