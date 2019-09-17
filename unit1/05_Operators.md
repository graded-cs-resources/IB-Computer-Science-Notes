---
title: Operators
---

# Operators

An **operator**:star:, in a programming language, is a tool used to modify, manipulate, or work with individual values or variables. It is almost always represented using some form of *word* or *symbol*, but it differs from a function in that it is simply put before, after, or between values or variables.

Modern programming languages have MANY operators. We will define the most important ones below - a lot of them will seem obvious, but having the reference could be valuable.

I have bolded the ones that might have something kind of surprising or that you might not have seen before - if you only read a few of them, read those!

## Operators on Numeric Values

### Arithmetic Operators

The operators you are most familar with: these do math.

The examples below represent the results from TypeScript. java would be mostly the same. The exception shown below is integer division, which only exists on typescript.

| Operator                                       | Code Sample                                  | Result                                                 | IB    |
| ---------------------------------------------- | -------------------------------------------- | ------------------------------------------------------ | ----- |
| Addition (`+`)                                 | `let a = 2; let b = 7;`<br>`a + b`           | <br>`9`                                                |
| Subtraction (`-`)                              | `a - b`                                      | `-5`                                                   | `+`   |
| Multiplication (`*`)                           | `a * b`                                      | `14`                                                   | `*`   |
| Division (`/`)                                 | `a / b` <br> `b / a`                         | `0.2857142857142857`<br>`3.5`                          | `/`   |
| **Modulus or Remainder (`%`)**                 | `a % b`<br>`b % a`                           | `2` (remainder of 2 / 7) <br> `1` (remainder of 7 / 2) | `mod` |
| Integer Division (`/`)<br>(java only)          | `int a = 2, b = 7`;<br> `a / b` <br> `b / a` | <br>`0`<br>`3`                                         | `div` |
| **Exponentiation  (`**`)**<br>(TypeScipt only) | `a ** b`                                     | `128` (2<sup>7</sup>)                                  | N/A   |

### Comparison Operators

These operators return boolean values - either `true` or `false`.

| Operator                     | Code Sample                         | Result                       | IB  |
| ---------------------------- | ----------------------------------- | ---------------------------- | --- |
| Greater than (`>`)           | `2 > 3` <br> `3 > 3`<br> `4 > 3`    | `false`<br>`false`<br>`true` | `>` |
| Greater than or equal (`>=`) | `2 >= 3` <br> `3 >= 3`<br> `4 >= 3` | `false`<br>`true`<br>`true`  | `≥` |
| Less than (`<`)              | `2 < 3` <br> `3 < 3`<br> `4 < 3`    | `true`<br>`false`<br>`false` | `<` |
| Less than or equal (`<=`)    | `2 <= 3` <br> `3 <= 3`<br> `4 <= 3` | `true`<br>`true`<br>`false`  | `≤` |
| Equal to (`==`)              | `2 == 3` <br> `3 == 3`<br> `4 == 3` | `false`<br>`true`<br>`false` | `=` |
| **Not Equal (`!=`)**         | `2 != 3` <br> `3 != 3`<br> `4 != 3` | `true`<br>`false`<br>`true`  | `≠` |

## Operators on Strings

| Operator                     | Code Sample                                 | Result          | IB  |
| ---------------------------- | ------------------------------------------- | --------------- | --- |
| **Concatenation (`+`)** <br> | `let b = "bob"`;<br>`b + " " + b + "mary";` | <br>bob bobmary | N/A |

**Note that since the same operator, `+` is used for strings and numbers, you can get some odd results if you aren't careful.** Feel free to use `ts-node` in your command line to test these results below.

```ts
"a" + 3; // result: "a3" - converts 3 to a string then concatentes
3 + "a"; // result: "3a" - same as above
3 + 2 + "a" // result: "5a" - does 3 + 2 first, then concatenates with a
3 + (2 + "a") // result: 32a. Concatenates 2 and a to "2a" then concatenates the 3.
"a" + 3 + 2 // result: a32
"a" + (3 + 2) // result: a5
"a" + (3 - 2) // result: a1
"a" + 3 - 2 // error! tries to do "a3" - 2, which is not possible.
```

## Logic Operators

These are used when working with boolean statements, to combine multiple statments together or change them around. You will commonly see them in `if` statements.

| Operator                                                                                                      | Code Sample                                   | Result              | IB    |
| ------------------------------------------------------------------------------------------------------------- | --------------------------------------------- | ------------------- | ----- |
| **And (`&&`)** <br> True only if both sides are true                                                          | `(3 > 2) && (2 > 1)`<br>`(3 > 2) && (2 == 3)` | ``true``<br>`false` | `AND` |
| **Or (`||`)** <br> True if EITHER or BOTH sides are true                                                      | `(3 > 2) || (2 > 1)`<br>`(3 > 2) || (2 == 3)` | ``true``<br>`true`  | `OR`  |
| **Not (`!`)** <br> Comes BEFORE a boolean statement, and <br>changes it from `true` to `false` or vice versa. | `!(3 > 2)`<br>`!(2 == 3)`                     | `false`<br>`true`   | `NOT` |

## Assignment Operators

These operators change the value stored inside a variable. By far the most important one is the first one; we will mostly avoid using the others, but they exist.

| Operator                                                                            | Code                     | Result                                 | Note                      | IB  |
| ----------------------------------------------------------------------------------- | ------------------------ | -------------------------------------- | ------------------------- | --- |
| Assignment (`=`)                                                                    | `a = 3;`<br>`a = a + 1;` | `a` has value 3<br>now `a` has value 4 |                           | `=` |
| **Increment (`++`**) <br>increases variable value by 1.<br>Used AFTER the variable. | `a = 3;`<br>`a++;`       | `a` has value 3<br>now `a` has value 4 | equivalent to `a = a + 1` | N/A |
| Decrement (`--`) <br>decreases variable value by 1.<br>Used AFTER the variable.     | `a = 3;`<br>`a--;`       | `a` has value 3<br>now `a` has value 2 | equivalent to `a = a - 1` | N/A |
| Addition assignment (`+=`) <br> increases variable on left by amount on right.      | `a = 3;`<br>`a += 4;`    | `a` has value 3<br>now `a` has value 7 | equivalent to `a = a + 4` | N/A |

There are also versions of the last one for subtraction `-=`, division `/=`, and multiplication `*=`. You should not use ANY of these, generally, as they can be hard to read since they look too much like `==`. The `++` operator is pretty common, though, and probably worth using.

## Check your Learning

To check your answers, open `ts-node` in your command line and copy these commanss.

1. At the end of the code block below, what will be printed?
   
   ```ts
   let a = 7;
   let b = 3;
   a = a - b;
   a = a**2;
   a++;
   b++;
   console.log(a+b);
   ```

2. Will the following statement be `true` or `false`?
   
   ```ts
   ! ((2 == 2) || (3 != 3))
   ```

3. What would be the value of `b` below?
   
   ```ts
   let s = "23";
   let n = 43
   let b = s + n;
   ```

