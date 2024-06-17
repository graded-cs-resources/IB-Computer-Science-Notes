---
title: Loops
---

A **loop** or **iteration** is a section of code that can potentially run more than once in code, used to deal with repetitive tasks in code.

## While Loops

The most basic type of loop is called a **while loop**, which works very similar to a conditional statement (if statement) but will repeat the code as long as the conditional stays true. For example, consider the following pseudocode:

```
X = 20
loop while X mod 2 = 0
    X = X / 2
end loop
output X
```

Try to guess what this loop will print out.

<details markdown="1"><summary>Click to expand answer</summary>
it will print out 5. here is a *trace table* for this loop.

| X   | Is mod 2 = 0? | output |
| --- | ------------- | ------ |
| 20  | yes           |        |
| 10  | yes           |        |
| 5   | no            | 5      |
</details>

Here is a similar loop in java:

```java
int x = 20;
while (x % 2 == 0) {
    x = x / 2;
}
System.out.println(x);
```

And here is a version that expands this concept to a method:

```java
public int biggestOddFactor(int x) {
    while (x % 2 == 0) {
        x = x / 2;
    }
    return x;
}
```

You can find practice problems for while loops in CS Awesome lesson 4.1

## For Loops
