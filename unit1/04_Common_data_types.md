# Common Data Types

In [previous notes](03_Data_on_computers.md), we mentioned that the bits and bytes on a computer can be interpreted in lots of different ways.

One of the ways our computer programs know how to interpret a byte (or more) of data in the context of a programming language is by the *type* of the data, which is set in the program. Every variable in a program can hold data of a specific type.

In a program, there are three types of things that have types:
* Variables, named locations in memory whose value may change over the course of the program.
* Constants, named locations whose value will always be the same
* Literals, individual typed things like `2` or `"abc"` that are used only once and represent a value directly.

|General Type| Languague-Specific usage | Description |
|------------|--------------------------|-------------|
| Boolean    | **TypeScript**<br>`let boo:boolean=true`<br><br>**java**<Br>`boolean boo=false` |The value of a boolean is either `true` or `false`. The simplest data type!|
|  Numeric   |  **TypeScript**<br>`let n:number = 1`<br>`let x:number = 3.21`<br><br>**java**<br>`int n = 11`<br> `double x = 1.2`  |  Holds a number. In TypeScript and javascript, all numbers are *floating point numbers* (meaning they can be integers or decimals) while java separates decimals (called *doubles* for historical reasons) from integers. There are advantages to both systems.  |
|  Characters and Strings  |  **Typescript**<br>`let k:string = "word"` <br><br>**java**<br>`char c = 'a'`<br>`String s = "12"`  |    A *character* is a single piece of text data, ready to print to the screen, such as the character `'a'` or `'8'` or `'â'` or even `'😀'`.<br><br>If you combine more than one character, you get a string, like `"string83"`. In javascript / TypeScript, characters are just small strings, but in java they are separate types of data with different rules. <br><br>Strings and characters are always surround by quotation marks.  |
|  Arrays     |  **TypeScript**<br>`let a:number[] = [1, 2, 3]`<br><br>**java**<br>`boolean[] a = {true, false}`  |  A collection of more than one item of any type (even other arrays!). `boolean[]` in either language creates a group that can hold many boolean values.  |
|   Objects    |  Much more later!  |  A group of many related values and functions that work together as one larger *thing*. The center of object-oriented programming. Objects often have their own special names.  |

### Check your Understanding

1. What type of data is the value `234` in TypeScript? What is it in java?
2. You want to write the code `j = "bob"`. What data type must `j` be for this to not give an error?
3. The following TypeScript code gives an error. Why?

   ```TypeScript
   let j:string;
   j = 123;
   ```
4. The following java code gives an error. Why?

    ```java
    int j;
    j = "123";
    ```
5. You write the following code:
   ```TypeScript
   b = (2 + 2 > 4);
   ```
   What do you think is the VALUE and TYPE of b?

