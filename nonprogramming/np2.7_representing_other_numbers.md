---
title: Representing Other Numbers
---

# A Note Before Reading

This page of notes goes pretty detailed into a lot of math. You are not required by the IB to be able to reproduce ANY of this math, so if you are a little lost or confused as you try to follow this *do not stress out*. This is provided in the interest of completion, but at the end of each section I have listed the takeaways you need to really remember for each section.

# Negative Integers

In [Lesson 2.5](np2.5_representing_integers.md), we learned how to convert binary in our computer into positive integers in decimal. But of course most of the time we are working with math on our computer, we want to be able to do more than just work with positive integers.

To do this, we need to find a useful encoding scheme for other numbers. For negative integers, the encoding scheme we use is called **Two's Complement**:star:

## Two's Complement

Consider the positive number represented in binary by the value `0101 1011`. You can convert that to decimal to see that this will have the value 91.

Two's complement allows you to represent the value -91 by following these steps:

1. Reverse all of the bits in the original number - in this case creating `1010 0100`
2. Add 1 to the number. In this case that creates `1010 0101`

This value is called the *Two's Complement* of 91. Why do we use this? Well, imagine adding the two numbers together. Note that adding binary numbes works exactly like adding numbers in decimal, except that since 1 + 1 = 10 in binay, you have to carry a one whenever you have 1+1, which is what the litte 1's represent in the picture below. 


```none
   ₁₁₁₁ ₁₁₁
   0101 1011
+  1010 0101
  ---------
  10000 0000
```

This value, if converted to decimal, is 256. But it's also 9 bits, but we started with 8-bit integers, so what actually happens is *the 1 in front is dropped and completely disappears*, leaving this sum as 0. Exactly what -91 + 91 should be!

Consider this example, where we add -91 (the same nubmer before) and positive 4.

```none
       ₁   
  1010 0101
+ 0000 0100
  ---------
  1010 1101
 ```

The final number, `1010 1001` is negative - we can tell because of the 1 in front. To find its value, undo two's complement by subtracting 1 and reversing, which gives us `0101 0111`. This number has the value 87 (check it!), so the actual sum was -87, as expected.

Consider another addition, -91 + -5. (-5 is `1111 1011` in two's complement...)

```none
  ₁₁₁₁ ₁₁₁
  1010 0101
+ 1111 1011
-----------
1 1010 0000
```

Again, we can ignore the first 1 here since it's the 9th bit, so the sum we will look at here is `1010 0000`, a negative number. Subtract one to get `1001 1111`and then invert to get `0110 0000`, which = 32 + 64 = 96. Thus our sum had the value -96, as expected.

### Takeaways

* Negative numbers are represented in computers using a system called Two's Complement
  
* This system allows the computer to use the same circuits to add negative numbers as positive numbers, making processors more efficient


### Check your understanding

1. Why do we use two's complement to represent negative numbers, instead of a simpler scheme?
   <details markdown="1"><summary>Click to expand answer</summary>
   Two's complement allows us to add negative numbers using the same adding systems we use for
   positive numbers. A simpler encoding scheme might be easier to understand, but would not allow
   us to do that.
   </details>

## What if we have more than one byte?

With one byte, using two's complement will allow you to store numbers from -128 (represented by `1000 0000`) up through 127 (represented by `0111 1111`).

If you use TWO bytes to represent integers, your values can range from -32768 (-2^15) (`1000 0000 0000 0000`) up through 32767 (`0111 1111 1111 1111`). (2^15-1)

If you use FOUR bytes, the standard for an `int` variable in java, you can go from -2^31, or -2,147,483,648 up to 2^31 - 1, or 2,147,483,647

These are all asymmetric because we have a representation for 0, which takes up one of the "slots". More bytes (such as the 8 bytes used by `long` values on java) allow for even more possible values.

# Floating Point Numbers

Working with decimals or very large/small numbers in computers requires working with **floating point values**, like the `double` type in java.

Let's start by thining about how you can represent decimals in binary (you'll never need to do this on a test):

Imagine you want to represent 14.25 in your computer. You would need to start by converting this to binary. The 14 part we know how to do: 14 in decimal = `1110` in binary. To convert the .25 part, we need to turn it into powers of two as well! Luckily, 0.25 = 1/4, which is simply $$\frac{1}{2^2}$$ - therefore 0.25 in decimal is the same as `0.01`  in binary! so 14.25 in decimal is `1110.01` in binary

A floating point value represents all numbers in binary scientific notation, so we can start by writing this value as $$1.11001 \cdot 2^3$$ (notice the 2 instead of the 10 in binary)

In a java 64-bit `double`, we can represent this like so:

1. The first bit tells the sign (0 for positive, 1 for negative)
   
2. The next 11 bits hold the value of the exponent. In order to make it possible to have both negative an positive exponents, we add a *bias* to our exponent of 1023. This allows exponents ranging from -1022 to 2046
   
3. The remaining 52 bits hold the binary representation of the 52 digits AFTER the 1. We don't need to include the first 1 because ALL binary scientific notation values start with that 1!

To represent our $$1.11001 \cdot 2^5$$ (14.25 decimal) as a double, we can build our value like so:

```none
0       10000000010       11001 00000....(enough zeros to fill 52 bits)

sign    3 + 1023=1026                  52 bits to hold the value
       this is 1026 in binary
``` 
Try using the app below to turn other doubles into binary if you want.

<div class="iframe-container" style="padding-top:50%">
<iframe width="100%" class="slides" src="https://codehs.com/sandbox/dgriswoldgraded/Double_to_Binary/embed/?display_mode=displayOnly&show_file_tree=False" frameborder="0" allowfullscreen class="video-iframe"></iframe>
</div>

There are a few special numbers that can't be represented using this scheme and have their own special encodings. the most important is 0, which is simply represented by 64 0's. 

There are some challenges with floating point representation, the most important being loss of precision. Consider a number easy to represent in decimal like 0.1, or one-tenth. This number CANNOT be represented as a binary decimal exactly, becase 1/10 is not a sum of powers of 2. So because of that, there will be some rounding error when representing 1/10 in binary.

You can use the program below to test out what happens if you count by floating point values. Some values, like `0.25` will work exactly as expected because they make easy powers of 2. Others, like `0.1` will work quite poorly with lots of rounding errors.

<div class="iframe-container" style="padding-top:50%">
<iframe width="100%" class="slides" src="https://codehs.com/sandbox/dgriswoldgraded/countBy/embed/?display_mode=displayOnly&show_file_tree=False" frameborder="0" allowfullscreen class="video-iframe"></iframe>
</div>

### Takeaways

* Floating Point numbers are always represented using binary scientific notation
* Floating point representations represent the SIGN, the EXPONENT, and the FRACTION in three separate parts
* Numbers that are easy to represent in decimal may not be easy to represent in binary floating point, leading to unexpected rounding errors