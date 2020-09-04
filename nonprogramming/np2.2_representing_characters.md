---
title: Non-Programming Lesson 2.2 - Representing Characters
---
# Representing Characters

When you have a block of memory dedicated to text in your computer, it is encoded as a series of **characters**, like the `char` variables in java.

The simplest way to think about storing characters is to imagine a *lookup table* of characters - basically a list of all the characters you want on one side, and a number (in hexadecimal!) that corresponds to that character. We call this a **character set**:star: and the history of character sets is fascinating.

## The original character set - ASCII

Traditional, older computers from the 20th century almost all used a character set called ASCII, short for American Standard Code for Information Exchange. This table only included 128 characters, so it required a mere 7 bits of data for each character! The image below shows the full table, and as you can see it includes every character on the US English keyboard, as well as my special characters that were used to give instructions to older printers and screens. (**Note:** in the image, the `0x` in front of each hex value is simply a shorthand often used to indicate the value is in hexadecimal)

![ASCII table](media/ascii.jpg);

## ASCII Extensions

Characters were traditionally represented using a single byte, which offers 2^8 = 256 options. ASCII only needed 128, so the other 128 options were often used for ASCII *extensions*. These extensions varied depending on need - for example, the *Latin extended* variation added characters such as `à` and `ã` that would be needed for other latin-based languages. But other extensions added Germanic characters like `ü` or Arabic characters like `ﺖ` . Because different people across the world needed different extensions, the programmer had to know which extension was used in order to read the files correctly.

This was still insufficient for languages such as Japanese or Korean, which have thousands of characters, and they had to use complex customized solutions for years. This made it very challenging to pass text information between people from different countries successfully.

## Unicode

Finally, in the 1990s, organizations from all over the world got together to create a standard *character set* that would connect a valid hexadecimal value to every single character used by every language, modern and ancient, and with room to spare for convenience characters and future characters as well.

After several years, what emerged was the Unicode standard. This standard uses up to 21 bits to represent characters, which means it could represent over 2 MILLION different characters. So far, only 120,000 characters have been assigned, so there's lots of room to grow still! 

The worldwide acceptance of unicode has meant that any computer can read and write characters as diverse as `a` (Latin 'a'), `🐱‍👤` (ninja emoji), `ה` (Hebrew 'he'), `∰` (volume integral symbol), `갦` (Korean, or hangul, 'Gaelm'), and `𓀤` (Egyptian heiroglyph). Feel free to explore the unicode character set at [Unicode Table](https://unicode-table.com/en/) - it's very cool!

The adoption of unicode was slow, and still has the challenge that there are at least two possible ways to actually *encode* the unicode values. 

1. In **UTF-16** *almost* every character takes up 2 bytes, though a few of the special ones (like many of the emoji) take 4.  
   * **Advantages**: Since the vast majority of characters are the same size, it doesn't take much 'thinking' on the part of a computer to interpret the data. Programming languages like can use 2 bytes to store `char` variables and they will usually be able to hold the complete character in that space. The two-byte characters in UTF-16 are also very easy to convert, even by hand, since they simply store the unicode hex value directly.
  
   * **Disadvantages**: Every single character takes at least 2 bytes, even the most common ASCII characters, which can make for very inefficient space usage. This is especially true in situations like computer code, which is written almost entirely using ASCII characters. This also means that files saved in UTF-16 are not backwards compatible with any older character systems. And because many of the use-cases of UTF-16 tend to assume everything is 2 bytes, the special 4-byte characters are often misinterpreted or provide difficulties.
  
2. In **UTF-8**, characters can take up different amounts of space, anywhere from 1 up to 4 bytes - the first bit(s) of each byte essentially tell the computer whether it needs to pull in more bytes to get the entire character.
   * **Advantages**: UTF-8 is completely compatible with ASCII. This means that any old file written in ASCII is a completely valid UTF-8 file, because those 128 characters only take one byte in UTF-8. This is a huge advantage on the web, because all of the code that makes a website uses ASCII characters, even if the content does not. This means that UTF-8 files are almost always significantly smaller than UTF-16 ones.

   * **Disadvantages**: The biggest disadvantage is that the more complex encoding scheme means the processor has to work harder to decode the files. It is also not an appropriate scheme for primitive data types in programming languages like java, since characters can range from 1-4 bytes with little expectation that most would be 2 bytes like in UTF-16. The complexity of the encoding scheme also makes it harder to write your own code to interpret the data, or interpret it by hand (rare though that need is).

The video below is optional, but if you find this stuff at all interesting it can be cool to see. In it, I explore the text string `Hi João! 👋` in several different character encoding schemes, and show what would happen if you try to open it in the WRONG scheme.

<div class="iframe-container">
<iframe width="100%" src="https://www.youtube.com/embed/jLtV3j9j3ls" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
