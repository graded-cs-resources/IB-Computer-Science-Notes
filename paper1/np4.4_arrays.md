---
title: IB Arrays
---

# IB Arrays

An **array**:star: is like a collection in that it holds a group of connected items using a single variable name. Unlike a collection, *any* element of an array can be accessed at any time - you do not need to access the elements in order, you just need to know *where* in the array you can find the element you want.

Think of an array as being like a row of lockers - the lockers are numbered, and next to each other. You can access any locker you want, but you need to know which locker number to go to.

![Row of lockers](https://csawesome.runestone.academy/runestone/books/published/csawesome/_images/rowLockers.jpg)
<small>Image Credit: [CS Awesome](https://csawesome.runestone.academy/runestone/books/published/csawesome/Unit6-Arrays/topic-6-1-array-basics.html#declaring-and-creating-an-array)</small>

The code below shows two ways you might see arrays created in pseudocode

```js
   array1 = [1.2, 2.8, 9.9]
   array2 = new Array(5)
```

After running the code above, you will create the following in memory:

![Java arrays in memory](https://docs.google.com/drawings/d/e/2PACX-1vRD9Uec6OuweycqHcz6SKt_XnnRjHBFvMlScXoc1fPEkhgONDME61AG0tobw1kALxMyrZ3WNm1Mkm0j/pub?w=618&amp;h=336)
<small>Image Credit: [Me](https://docs.google.com/drawings/d/1DQpQOspzFO90crV4ujwrri7RNG19NW-2JEPkN6IlXzg/edit)</small>

In lower-level languages like java or C, and also in IB Pseudocode, you can be certain that the elements of the array are actually stored *next to each other in the RAM or cache*, as shown in the image above. This makes it MUCH more efficient to access elements further in the array. But it also means arrays are limited by the following rules:

1. Every element in the array must be the same type
2. The length of the array must be *fixed* and cannot change


## Accessing Elements

The individual *elements* of an array are referred to using an **index**:star:, an integer value that tells you which element you want. This is like the locker number in our metaphor above. In most programming languages the first index in an array (that is, the first locker number) is `0`.

```js
array1[0]; // 1.2
array1[1]; // 2.8
array1[2] = 11.2; // **change** the value of array element 2
array1; // [1.2, 2.8, 11.2]
```

In most languages like java and javascript, you can use the `length` property of an array to learn how many elements an array has. In IB Pseudocode this is not officially defined, but when it is needed the problem will *tell* you the length or how to access the length.

```js
array1.length; // 3
```

In java, as mentioned earlier, you CANNOT change the length of an array once it is declared, but in typescript you CAN.

In javascript, and certain other languages, you CAN change the length of an array after it is created, and some of our code.org work will ask you do to do so. It is important that you know you ***cannot do this in IB pseudocode***. If you need a data structure that gets larger over time in IB Pseudocode, your ONLY option is an IB Collection. 

## Looping through an array - JavaScript

A common thing to do with any collection is to go through each element one at a time, and do something to it. It's so common, in fact, that you can expect to see these structures usually multiple times in any remotely large project. 

The code below shows how you would do this in JAVASCRIPT

```js
// Assume names[] is an array of strings representing
// the names of students
for (var i = 0; i < names.length; i = i + 1) {
    console.log(names[i]);
}
```

* A `for` loop:star: is a powerful type of loop that allows us to keep repeating something as long as one thing is true. You can see semi-colons separating the parentheses of the for loop.

    * The first section of the `for` loop, `let i = 0`; is run at the very beginning of the loop. In this case, we make a new number variable and set it equal to 0.
    * The second section of the `for` loop, `i < names.length` is the *conditional statement*. The loop will run *as long as* that condition is true. In this case, `i` will be 0 first.
    * The third section of code is run at the END of each loop. In this case, we will make `i` bigger by one at the end of each loop. So `i` will be 0 the first time through, `1` the second time through, and keep getting bigger as long as it is less than the length of the array.

If we assume that `names` has 3 elements in it, then `i` will first take the value 0, then 1, then 2, at which point the loop will end. Those are, conveniently, the indexes of the array! So every element of the array will be printed in this loop.

## Looping through an array - Pseudocode

The code below shows the equivalent in IB pseudocode:

```python
   // assume the length is stored in the variable LENGTH
   loop I from 0 to LENGTH - 1
       output NAMES[I]
   end loop
```

Notice that the loop in IB Pseudocode is simpler it some ways - it simply allows you to make a variable count upward from a starting number (0 in this case) to a final number (LENGTH - 1). This is less powerful than a for loop, but easier to use!

Remember: when you are WRITING pseudocode, you have some flexibility in how you write it. If you wrote javascript code instead it would probably be fine, as long as they understood what you wrote. But you need to be able to READ IB Pseudocode.

## Implementing IB Collections with TypeScript arrays

An interesting mental exercise to try to better understand both the IB Collections and arrays is to compare their code. The below table shows how you would implement each of the IB collection methods with a TypeScript array. (in java, an array would be a poor choice for this because of its fixed size. Better choices exist; we will discuss them (much) later).

For each of these, assume a variable called `current_index` exists, and it starts out equal to 0 when the new collection is made.

| Method  name  | Brief description                      | Example: <br>HOT, a collection of temperatures | TypeScript equivalent                              |
| ------------- | -------------------------------------- | ---------------------------------------------- | -------------------------------------------------- |
| `addItem()`   | Add item at end                        | `HOT.addItem(42)`<br>`HOT.addItem("chile")`    | `hot.push(42)` or `hot[hot.length]=42;`            |
| `getNext()`   | Get the next item                      | `TEMP = HOT.getNext()`                         | `next = hot[current_index];`<br>`current_index++;` |
| `resetNext()` | Go back to the start of the collection | `HOT.resetNext()`                              | `current_index = 0;`                               |
| `hasNext()`   | Test: has next item                    | `if HOT.hasNext() then`                        | `if (current_index >= hot.length) {`               |
| `isEmpty()`   | Test: collection is empty              | `if HOT.isEmpty() then`                        | `if (hot.length==0) {`                             |

## Check your Understanding
1. What does the "resetNext()" command do for IB collections?
   
   <details markdown="1"><summary>Click to expand answer</summary>
   It makes it so the next time you call `getNext()` you will get the FIRST element.
   </details> 

2. How could you loop through an IB collection named NAMES and print out each element in the collection?
      
   <details markdown="1"><summary>Click to expand answer</summary>
   ```python
   NAMES.resetNext()
   loop while NAMES.hasNext()
     output(NAMES.getNext())
   end loop
   ```
   </details>

3. How would you make a new array holding the first five letters of the alphabet (as strings) in TypeScript?

   <details markdown="1"><summary>Click to expand answer</summary>
   ```ts
   let arr:string[] = ["a", "b", "c", "d", "e"];
   ```
   </details>

4. How would you make the same array in java?

   <details markdown="1"><summary>Click to expand answer</summary>
   ```java
   String[] arr = {"a", "b", "c", "d", "e"};
   ```
   </details>

5. How would you access the third element ("c") in the previous array?

   <details markdown="1"><summary>Click to expand answer</summary>
    ```ts
   arr[2]
   ```
   </details>

6. If you want to change the last element to be "z", how would you do that?

   <details markdown="1"><summary>Click to expand answer</summary>
   ```ts
   arr[4]="z";
   ```
   </details>

7. How do you loop through all of the elements in your array of letters and print them all out (using `console.log`)?

   <details markdown="1"><summary>Click to expand answer</summary>
   ```ts
   for (let i = 0; i < arr.length; i++) {
       console.log(arr[i]);
   }
   ```
   </details>

8. Open `ts-node` on your computer by typing the command on your command line. Then try these things. **Try to do each step WITHOUT referring back to the notes. Try 2 or 3 or 4 times if you need to, paying attention to the errors. If you still can't do them, look back, but do NOT copy and paste!*
   1. Create a new string array called `students`. 
   2. Assign this array to `students`: `["luca","joao","sofia","marina","yash"]`
   3. Write a loop that will go through all of the names and, for each one, use `console.log()` to print "Student name is: *name*".
      
      <details markdown="1"><summary>Click to expand answer</summary>
      ```ts
      let students:string[] = [];
      students = ["luca", "joao", "sofia", "marina", "yash"];
      for (let i = 0; i < students.length; i++) {
          console.log("Student name is: " + students[i]);
      }
      ```
      </details>

## Flashcards

* collection
* collection.addItem()
* collection.getNext()
* collection.resetNext()
* collection.hasNext()
* collection.isEmpty()
* array
* contiguous memory
* index
* accessing an array element
* for loop
* looping through an array (*write the loop on the back*)