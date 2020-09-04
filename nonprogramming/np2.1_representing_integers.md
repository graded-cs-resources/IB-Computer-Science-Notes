---
title: Non-Programming Lesson 2.1 - Representing Integers
---

# Binary and Hexadecimal

As we have seen before, all data on computers is stored as a series of *bits* - tiny pieces of information that are either on or off, with no region in between.

Because our brain works best using letters or numbers, it is easiest to think of these bits as either having the values **`T`** and **`F`**,  or **`0`** and **`1`**. The second is more common.

Working with only two digits, `0` and `1`, creates an entirely new number system called **binary**:star:. You can think of binary as being a system for an alien race that only has 1 finger on each hand, so they only ever created two digits! The system we normally use, with 10 digits, is called the **decimal**:star: system.

Because only having two options for any particular piece of data is USUALLY not enough, we often want to work with larger groups of bits, to give us the possibility of representing bigger numbers.

## Numbers in 4 bits - the nibble

A **nibble** consists of four bits taken together as a single chunk. If we read data in as nibbles, then each nibble can stand for any number between 0 and 15, as shown below. 

| Decimal | Binary |     | Decimal | Binary |
| ------- | ------ | --- | ------- | ------ |
| 0       | 0000   |     | 8       | 1000   |
| 1       | 0001   |     | 9       | 1001   |
| 2       | 0010   |     | 11      | 1010   |
| 3       | 0011   |     | 10      | 1011   |
| 4       | 0100   |     | 12      | 1100   |
| 5       | 0101   |     | 13      | 1101   |
| 6       | 0110   |     | 14      | 1110   |
| 7       | 0111   |     | 15      | 1111   |

The image below demonstrates how we count in binary AND decimal - it actually works just like counting in regular numbers, its just that we can only alternate between 0's and 1's in each spot, rather than counting all the way up to 9 in each spot!

![combined odometer](media/combined_odometer.gif)

### Converting between Binary and Decimal 

Let's consider one of the number combinations above:

**14 (decimal) ≡ 1110 (binary)**
{: .giantText .center}

To understand why these two numbers are the same, you have to think about what the 1 and the 4 actually mean - place value!

**14** = **1** Ten + **4** Ones
{: .giantText .center}

In binary, because there are only TWO possibilities for each digit instead of 10, the place values aren't about 10s - they are about 2's! Specifically, POWERS of two.

<p class="giantText" markdown="1">**1110** = **1** eight (2<sup>3</sup>) + **1** four (2<sup>2</sup>)  
+ **1** two (2<sup>1</sup>) + **0** ones (2<sup>0</sup>)
</p>

This, of course, is equivalent to 14 in decimal, as we already saw. You could convert the other way by working backwards and finding powers of two that can be added to get your number.

#### Check Your Understanding

1. Convert the 6-bit binary number `10 1101` to decimal.
   <details markdown="1"><summary>Click to show answer</summary>
   $$2^0 + 2^2 + 2^3 + 2^5 = 1 + 4 + 8 + 32 = 45$$
   </details>

2. Convert the decimal value 55 to binary
   <details markdown="1"><summary>Click to show answer</summary>
   Write 55 as a sum of powers of 2  
   $$55 = 32 + 16 + 4 + 2 + 1 = 2^5 + 2^4 + 2^2 + 2^1 + 2^0$$   
   So in binary, we would write this as `11 0111`
   </details>
   
If you want more information about converting to and from decimal and binary, I suggest using [Khan Academy's article](https://www.khanacademy.org/computing/ap-computer-science-principles/computers-101/digital-data-representation/a/bits-and-binary) and [practice problems](https://www.khanacademy.org/computing/ap-computer-science-principles/computers-101/digital-data-representation/e/bits-and-binary-exercise) to help you understand more completely.

### Hexadecimal digits

![hex odometer](media/hex_odometer.gif)
{: .image-right style="width:20em"}

It turns out, however, that our normal decimal numbers are a pretty bad way to work with nibbles (and, later, bytes) because the conversion between the two is never pretty. This is because the CARRYOVER vale in decimal (10) does not match up with a carryover value in binary, so things don't line up nicely.

To get around this, computer scientists often work with nibbles using a system called **hexadecimal**. In this world, we imagine that we actually have MORE digits - 16 of them - rather than fewer. To make this work, we add the digits `A B C D E F` to our normal `0 - 9` to get a total of 16 digits, with A representing 10 up through F representing 15.

In this case, our table of nibbles simply looks like this:

| decimal | binary | hexadecimal | --- | decimal | binary | hexadecimal |
| ------- | ------ | ----------- | --- | ------- | ------ | ----------- |
| 0       | 0000   | 0           |     | 8       | 1000   | 8           |
| 1       | 0001   | 1           |     | 9       | 1001   | 9           |
| 2       | 0010   | 2           |     | 10      | 1010   | A           |
| 3       | 0011   | 3           |     | 11      | 1011   | B           |
| 4       | 0100   | 4           |     | 12      | 1100   | C           |
| 5       | 0101   | 5           |     | 13      | 1101   | D           |
| 6       | 0110   | 6           |     | 14      | 1110   | E           |
| 7       | 0111   | 7           |     | 15      | 1111   | F           |

Working in hexadecimal allows us to directly convert a single nibble (a very common chunk of data) into a single "digit" that takes up much less space on paper (and might be easier to read), but without any of the annoying mathematical calculations of moving back and forth to decimal. This makes it much easier to work with larger chunks of data, like bytes.

## Working with bytes (8 bits)

A **byte** consists of 8 bits, or 2 nibbles. Because each nibble can take any of 16 possible values, there are $$ 16 \cdot 16 = 256 $$ possible values for a single byte - enough that we're starting to get interesting!

We will not list every possible byte, but consider an example: `1101 0011` (it is common to write bytes with a space between the nibbles, for readability). If I wanted to convert this into a SINGLE decimal value, I coud use place value: $$ 2^7 + 2^6 + 2^4 + 2^1 + 2^0 $$ $$ = 128 + 64 + 16 + 2 + 1 $$ $$ = 211 $$. This is a LOT of work though!

We could also represent this byte in hexadecimal. Because hexadecimal has a direct connection to nibbles, I can just convert each nibble INDEPENDENTLY! Starting with the first nibble: 

**1101** (bin) ≡ **13** (dec) ≡ **D** (hex)
{: .giantText .center}

Then the second nibble:

**0011** (bin) ≡ **3** (dec) ≡ **3** (hex)
{: .giantText .center}

So therefore we have

**1101 0011** (bin) ≡ **D3** (hex)
{: .giantText .center}

We could confirm that this is the same value by converting the new hexadecimal value back into decimal. To do this, we need to realize that hexadecimal uses powers of 16, so we would have **D3** = $$13 \cdot 16^1 + 3 \cdot 16^0 = 208 + 1 = 211$$ . This tracks with our work earlier, and lets us see the very important result:

**A single byte represents 8 bits, so it can always be represented by exactly 2 hexadecimal digits**
{: .largeText}

### Check Your Understanding

1. Convert the binary value `0010 1111` to hexadecimal
   <details markdown="1"><summary>Click to expand answer</summary>
   Working one nibble at a time:  
   `0010` is equivalent to 2 in decimal, so it is 2 in hexadecimal.  
   `1111` is equivalent to 8 + 4 + 2 + 1 = 15 in decimal, so it is F in hexadecimal.  
   Thus, the total value here is `2F` in hexadecimal.
   </details>
2. Convert the binary value `1101 0101 0000 1011` to hexadecimal
   <details markdown="1"><summary>Click to expand answer</summary>
   Working one nibble at a time:  
   `1101` is equivalent to 8 + 4 + 1 = 13 in decimal, which is D in hexadecimal.  
   `0101` is equivalent to 4 + 1 = 5 in decimal, so it is 5 in hexadecimal.  
   `0000` is 0 in everything including hexadecimal.  
   `1011` is 8 + 2 + 1 = 11 = B in hexadecimal.  
   Thus, the total value here is `D5 0B`
   </details>
3. Convert the hexadecimal value `A5` to binary and decimal
   <details markdown="1"><summary>Click to expand answer</summary>
   Working one nibble at a time (for binary conversion): 
   `A` is 10 in decimal, which is 8 + 2 in binary, so that is `1010`  
   `5` is 5 in decimal too, which is 4 + 1 = `0101` in binary  
   So the total value here is `1010 0101`  

   For the decimal conversion, we use powers of 16.  
   $$10 \cdot 16^1 + 5 \cdot 10^0 = 160 + 5 = 165$$ in decimal.
   </details>
   
If you want to read more about hexadecimal, and do some practice conversions, [khan academy](https://www.khanacademy.org/computing/ap-computer-science-principles/computers-101/digital-data-representation/a/hexadecimal-numbers) is still your friend.

# Calculating the possibilities for given space

To find the total number of values that can be stored in $$n$$ bits, use the calculation $$2^n$$. 

So in a byte, we can fit up to $$2^8 = 256$$ possible values. If we are storing integers as shown above, those will be the values from 0 to 255 (`0000 0000` to `1111 1111`, or, in hexadecimal, `00` to `FF`). But as we will see, we can use binary to represent all sorts of things, from letters to colors to sounds, and no matter what you are representing, if you read one byte you get 256 options for that byte!

In java, an `int` variable actually uses FOUR bytes, or 32 bits, of space. That means it can hold $$2^{32} = 4,294,967,296$$ possible values! You could also calculate this with $$256^4$$ since each byte holds 256 options, and there are 4 bytes. And a `double` in java uses EIGHT bytes, 64 bits - That means it can hold $$2^{64} = 256^8$$ possible numbers, a whopping 18 QUINTILLION different values!

You will not have a calculator available on IB tests, so for problems like this you would generally expected to leave answers as an unworked calculation, such as $$2^{64}$$.

### Check your undersanding

1. How many different values can be stored in 3 bytes? (leave your answer as an unworked value)
   <details markdown="1"><summary>Click to expand answer</summary>
   $$2^{24}$$ or $$256^3$$
   </details>
1. Web browsers represent colors using 4 bytes. How many different colors can be represented using four bytes? (leave your answer as an unworked value)
   <details markdown="1"><summary>Click to expand answer</summary>
   $$2^{32}$$ or $$256^4$$
   </details>
1. The Unicode standard uses 21 bits to hold different characters. How many possible characters can be encoded using 21 bits?
   <details markdown="1"><summary>Click to expand answer</summary>
   $$2^{21}$$
   </details>

# Negative Integers

The above information is useful to help us visualize the actual bits inside a computer as numbers that are easier for us to understand, but you might notice that we can only use this system to represent non-negative, or *unsigned* integers. What if we want to represent something else, like, say, negative numbers?

If we want to represent other things, we need to come up with an **encoding scheme**:star: - an agreed-upon way of storing the information we care about using nothing but bits. As long as the person or program STORING the data and the person or program READING the data both agree on the encoding scheme, then the information can be stored.

The first encoding scheme we will use is called **Two's Complement** and it is used in almost every modern processor to let us store NEGATIVE numbers.

## Two's Complement

Consider the positive number represented in binary by the value `0101 1011`. You can convert that to decimal to see that this will have the value 91.

Two's complement allows you to represent the value -91 by following these steps:

1. Reverse all of the bits in the original number - in this case creating `1010 0100`
2. Add 1 to the number. In this case that creates `1010 0101`

This value is called the *Two's Complement* of 91. Why do we use this? Well, imagine adding the two numbers together. Note that adding binary numbes works exactly like adding numbers in decimal, except that since 1 + 1 = 10 in binay, you have to carry a one whenever you have 1+1, which is what the litte 1's represent in the picture below. 

**Note**: You will never be required to add binary numbers like in the below section, though I'd like you to be able to calculate the two's complement of a given binary number. Try to follow the area below, but don't stress too much if it feels overwhelming.
{: .smallText}

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

### The takeaway




### Check your understanding

1. What is the two's complement of `0110 1011` and what value does it represent?
   <details markdown="1"><summary>Click to expand answer</summary>
   To find two's complement, invert every bit then add one.  
   Inverting gives: `1001 0100` and adding one gives `1001 0101`

   To find the value, convert the original binary to decimal.  
   $$2^0 + 2^1 + 2^3 + 2^5 + 2^6 = 1 + 2 + 8 + 32 + 64 = 107$$  
   Therefore the two's complement value represents $$-107$$
   </details>
2. Why do we use two's complement to represent negative numbers, instead of a simpler scheme?
   <details markdown="1"><summary>Click to expand answer</summary>
   Two's complement allows us to add negative numbers using the same adding systems we use for
   positive numbers. A simpler encoding scheme might be easier to understand, but would not allow
   us to do that.
   </details>

## What if we have more than one byte?

With one byte, using two's complement will allow you to store numbers from -128 (represented by 1000 0000) up through 127 (represented by 0111 1111).

If you use TWO bytes to represent integers, your values can range from -32768 (-2^15) (1000 0000 0000 0000) up through 32767 (0111 1111 1111 1111). (2^15-1)

If you use FOUR bytes, the standard for an `int` variable in java, you can go from -2^31, or -2,147,483,648 up to 2^31 - 1, or 2,147,483,647

These are all asymmetric because we have a representation for 0, which takes up one of the "slots". More bytes (such as the 8 bytes used by `long` values on java) allow for even more possible values.


