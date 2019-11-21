# Binary and Hexadecimal

As we discussed in [unit 1](../unit1/03_Data_on_computers.md), all computer data is stored as a series of *bits* - tiny pieces of information that can only be on or off. 

Because our brain works best using letters or numbers, it is easiest to think of these bits as either having the values **T** and **F** (for true/false as discussed in our [logic lesson](./06_boolean_logic.md)) or **0** and **1**. The second is more common.

A single bit can only contain 2 possible values. We usually want to be able work with more options for a piece of data than that, so we often work with larger chunks.

## Working with 4 bits - the *nibble*

A **nibble** consists of four bits taken together as a single chunk. A single nibble can have 16 possible values, which we can match up with the first 16 numbers in our normal decimal system as follows:

```
0: 0000   1: 0001    2: 0010   3: 0011   4: 0100   5: 0101   6: 0110   7: 0111

8: 1000   9: 1001   10: 0101  11: 1011  12: 1100  13: 1101  14: 1110  15: 1111
```

You can think of the nibbles (made of bits) as representing numbers in a system called the **binary number system** which, unlike our own system (base-10, or **decimal**), has only 2 digits (ours has 10). 

### Binary and Decimal 

Let's consider one of the number combinations above:

**14 (decimal) ≡ 1110 (binary)**
{: .giantText}

To understand why these two numbers are the same, you have to think about what the 1 and the 4 actually mean - place value!

**14** = **1** Ten + **4** Ones
{: .giantText}

Of course you know that if I added more digits, my *place value* would keep multiplying by 10. But why 10? Because there are 10 digits! The place value can be thought of as the "when do I need to roll over to the next digit", which in decimal happens every 10 cycles of the earlier digit, as you can see on the "odometer" to the left.

![combined odometer](media/07/combined_odometer.gif)
{: .image-right style="width:20em"}

In binary, there are only two digits, so the "rollover" happens much faster. This means that binary digits numbers take up more space for the same size number, as you can see in the odometer. It also means that place value in binary isn't about powers of 10 - it's about powers of **2**.

<p class="giantText" markdown="1">**1110** = **1** eight (2<sup>3</sup>) + **1** four (2<sup>2</sup>)  
+ **1** two (2<sup>1</sup>) + **0** ones (2<sup>0</sup>)
</p>

This, of course, is equivalent to 14 in decimal, as we already saw. You could convert the other way by working backwards and finding powers of two that can be added to get your number.

If you want more information about converting to and from decimal and binary, I suggest using [Khan Academy's article](https://www.khanacademy.org/computing/ap-computer-science-principles/computers-101/digital-data-representation/a/bits-and-binary) and [practice problems](https://www.khanacademy.org/computing/ap-computer-science-principles/computers-101/digital-data-representation/e/bits-and-binary-exercise) to help you understand more completely.

### Hexadecimal digits

![hex odometer](media/07/hex_odometer.gif)
{: .image-right style="width:20em"}

It turns out, however, that our normal decimal numbers are a pretty bad way to work with nibbles (and, later, bytes) because the conversion between the two is never pretty. So computer scientists often work with nibbles using a system called **hexadecimal**. In this world, we imagine that we actually have MORE digits - 16 of them - rather than fewer. To make this work, we add the digits `A B C D E F` to our normal `0 - 9` to get a total of 16 digits, with A representing 10 up through F representing 15.

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

Working in hexadecimal allows us to directly convert 4 bits (a very common chunk of data) into a single "digit" that takes up much less space (and might be easier to read), but without any of the annoying mathematical calculations of moving back and forth to decimal.

## Working with bytes (8 bits)

A **byte** consists of 8 bits, or 2 nibbles. Because each nibble can take any of 16 possible values, there are $$ 16 \cdot 16 = 256 $$ possible values for a single byte - enough that we're starting to get interesting!

We will not list every possible byte, but consider an example: `1101 0011` (it is common to write bytes with a space between the nibbles, for readability). If I wanted to convert this into a SINGLE decimal value, I coud use place value: $$ 2^7 + 2^6 + 2^4 + 2^1 + 2^0 $$ $$ = 128 + 64 + 16 + 2 + 1 $$ $$ = 211 $$. 

We could also represent this byte in hexadecimal. The easiest way to do that is to go one nibble at a time - the first nibble, `1101` corresponds to 13, or the hex digit `D`. The second nibble is `3` in both decimal and hexadecimal. So in hex, this entire byte could be written `D3` in hexadecimal. Let's confirm that this is the same decimal value, realizing that in hexadecimal our place values are powers of 16!

**D3** = **13** (D) sixteens (16<sup>1</sup>) + **3** ones (16<sup>0</sup>)
{: .giantText}

Since $$ 13 \cdot 16 + 3 \cdot 1 = 211 $$, this works!

**A single byte represents 8 bits, so it can always be represented by exactly 2 hexadecimal digits**

If you want to read more about hexadecimal, and do some practice conversions, [khan academy](https://www.khanacademy.org/computing/ap-computer-science-principles/computers-101/digital-data-representation/a/hexadecimal-numbers) is still your friend.
