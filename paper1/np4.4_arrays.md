---
title: IB Arrays
---

# Arrays

An **array**:star: holds a group of connected items using a single variable name. *Any* element of an array can be accessed at any time - you do not need to access the elements in order, you just need to know *where* in the array you can find the element you want.

Think of an array as being like a row of lockers - the lockers are numbered, and next to each other. You can access any locker you want, but you need to know which locker number to go to.

![Row of lockers](https://csawesome.runestone.academy/runestone/books/published/csawesome/_images/rowLockers.jpg)
<small>Image Credit: [CS Awesome](https://csawesome.runestone.academy/runestone/books/published/csawesome/Unit6-Arrays/topic-6-1-array-basics.html#declaring-and-creating-an-array)</small>

We will use arrays in both java AND in IB Pseudocode

Here are two ways you might see an array being created in pseudocode:

```js
   array1 = [1.2, 2.8, 9.9]
   array2 = new Array(5)
```

and here is how you would create the same arrays in java:

```java
   int[] array1 = {1.2, 2.8, 9.9};
   int[] array2 = new int[5];
```

After running the code above, you will create the following in memory:

![Java arrays in memory](https://docs.google.com/drawings/d/e/2PACX-1vRD9Uec6OuweycqHcz6SKt_XnnRjHBFvMlScXoc1fPEkhgONDME61AG0tobw1kALxMyrZ3WNm1Mkm0j/pub?w=618&amp;h=336)
<small>Image Credit: [Me](https://docs.google.com/drawings/d/1DQpQOspzFO90crV4ujwrri7RNG19NW-2JEPkN6IlXzg/edit)</small>

In languages that have true arrays, you can be certain that the elements of the array are actually stored *next to each other in the RAM or cache*, as shown in the image above. This makes it MUCH more efficient to access elements further in the array. But it also means arrays are limited by the following rules:

1. Every element in the array must be the same type
2. The length of the array must be *fixed* and cannot change

## Accessing Elements

The individual *elements* of an array are referred to using an **index**:star:, an integer value that tells you which element you want. This is like the locker number in our metaphor above. In most programming languages the first index in an array (that is, the first locker number) is `0`.

```java
array1[0]; // 1.2
array1[1]; // 2.8
array1[2] = 11.2; // **change** the value of array element 2
array1; // [1.2, 2.8, 11.2]
```

In most languages like java and javascript, you can use the `length` property of an array to learn the size of the array. In IB Pseudocode this is not officially defined, but when it is needed the problem will *tell* you the length or how to access the length.

```js
array1.length; // 3
```

In java, as mentioned earlier, you CANNOT change the length of an array once it is declared.

In javascript, and certain other languages, you CAN change the length of an array after it is created, because they work differently internally. It is important that you know you ***cannot do this in IB pseudocode***. If you need a data structure that gets larger over time in IB Pseudocode or java, you must use something other than an array.

## Looping through an array - Java

A common thing to do with any collection is to go through each element one at a time, and do something to it. It's so common, in fact, that you can expect to see these structures usually multiple times in any remotely large project. 

The code below shows how you would do this in JAVASCRIPT

```java
// Assume names is an array of strings representing
// the names of students
// whwere numElements is the number of elements we want to iterate
for (int i = 0; i < numElements; i = i + 1) {
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

## Check your Understanding

1. How would you make a new array holding the first five letters of the alphabet (as strings) in JavaScript?

   <details markdown="1"><summary>Click to expand answer</summary>
   ```js
   var arr = ["a", "b", "c", "d", "e"];
   ```
   </details>

2. How would you access the third element ("c") in the previous array?

   <details markdown="1"><summary>Click to expand answer</summary>
    ```ts
   arr[2]
   ```
   </details>

3. If you want to change the last element to be "z", how would you do that?

   <details markdown="1"><summary>Click to expand answer</summary>
   ```ts
   arr[4]="z";
   ```
   </details>

4. How do you loop through all of the elements in your array of letters and print them all out (using `console.log`)?

   <details markdown="1"><summary>Click to expand answer</summary>
   ```ts
   for (let i = 0; i < arr.length; i++) {
       console.log(arr[i]);
   }
   ```
   </details>

5. Open a fresh app on code.org App Lab, Tten try these things. **Try to do each step WITHOUT referring back to the notes. Try 2 or 3 or 4 times if you need to, paying attention to the errors. If you still can't do them, look back, but do NOT copy and paste!*
   1. Create a new array called `students`. 
   2. Assign this array to `students`: `["luca","joao","sofia","marina","yash"]`
   3. Write a loop that will go through all of the names and, for each one, use `console.log()` to print "Student name is: *name*".
      
      <details markdown="1"><summary>Click to expand answer</summary>
      ```ts
      var students = [];
      students = ["luca", "joao", "sofia", "marina", "yash"];
      for (var i = 0; i < students.length; i++) {
          console.log("Student name is: " + students[i]);
      }
      ```
      </details>

## Flashcards

* array
* contiguous memory
* index
* accessing an array element
* for loop
* looping through an array (*write the loop on the back*)