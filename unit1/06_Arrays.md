# IB Collections and Arrays

## Collections

A **collection**:star: is a general term for a set of values that are stored in a connected way, generally with only one large name for the entire collection. Some types of collections that you might see in modern programming languages include *linked lists*, *doubly linked lists*, *stacks*, *queues*, and *dictionaries*, and *arraylists*; some of these will be studied explicitly by HL students later, but for now we will focus on collections as a general idea, specifically focusing on how the IB exam will use it in Pseudocode.

The following table comes directly from the IB exam:

| Method  name  | Brief description                      | Example: <br>HOT, a collection of temperatures | Comment                                                                                                                                                              |
| ------------- | -------------------------------------- | ---------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `addItem()`   | Add item                               | `HOT.addItem(42)`<br>`HOT.addItem("chile")`    | Adds an element to the end of the collection that contains the argument, whether it is a value, String, object, etc.                                                 |
| `getNext()`   | Get the next item                      | `TEMP = HOT.getNext()`                         | `getNext()` will return the first item in the collection when it is first called.<br><br>Note: getNext() does not remove the item from the collection.               |
| `resetNext()` | Go back to the start of the collection | HOT.resetNext()<br>HOT.getNext()               | Restarts the iteration through the collection.  The two lines shown will retrieve the first item in the collection.                                                  |
| `hasNext()`   | Test: has next item                    | `if HOT.hasNext() then`                        | Returns TRUE if there are one or more elements in the collection that have not been accessed by the present iteration: used to see if we are at the end of the list. |
| `isEmpty()`   | Test: collection is empty              | `if HOT.isEmpty() then`                        | Returns TRUE if the collection does not contain any elements.                                                                                                        |

A common goal is to go through all the items in a collection: for this, you could use a structure like this one.

**Sample Code**
```
 // STUFF is a collection that already exists 
STUFF.resetNext()  	
loop while STUFF.hasNext() 
	ITEM = STUFF.getNext() 
 	// process ITEM in whatever way is needed  	
end loop 
```
The generic IB collection is most similar to a *linked list*, but it can be implemented with a wide variety of tools in modern programming languages.

## Arrays

An **array**:star: is an ordered list of values (generally of the same type) with a single name. They are one of the simplest collection types, and the most commonly used one in most languages.

![java array](media/05/Array&#32;diagram.svg){: .image-right style="width:45%"}
```ts
// TYPESCRIPT declaring an array with initial values
let array1:number[] = [1.2, 2.8, 9.9];
// no initial value (empty array)
let array2:number[] = [];
```
{: style="width:50%"}
```java
// JAVA declaring an array with initial values
double[] array1 = {1.2, 2.8, 9.9};
// an array with no initial value. 
// Must know size in advance!
double[] array2 = new double[5];
```
{: style="width:50%"}

In lower-level languages like java or C, you can be certain that the elements of the array are actually stored next to each other in the RAM or cache, as shown in the image above; this ensures that accessing the array is as efficient as possible, but requires two things: 

1. Every element in the array must be the same type
2. The length of the array must be *fixed* and cannot change

More dynamic languages like javascript and TypeScript allow you to change the size of arrays and even store multiple types, which makes them more flexible but less fast; at the lowest level of memory, they may look quite different from the predictable java arrays. When the IB exam refers to an array it assumes you are using a fixed-length structure like the one from java; it will refer to ones that can change as *lists* or *collections*.

## Accessing Elements

The individual *elements* of an array are referred to using an **index**:star:, an integer value that tells you which element you want. In most programming languages (including TypeScript and java) the first index in an array is `0`.

```ts
// working with array elements in TypeScript. 
// java would be identical.
array1[0]; // 1.2
array1[1]; // 2.8
array1[2] = 11.2; //change the value of array element 2
array1; // [1.2, 2.8, 11.2]
```

In both java and TypeScript, you can use the `length` property of an array to learn how many elements an array has.

```ts
array1.length; // 3
```

In java, as mentioned earlier, you CANNOT change the length of an array once it is declared, but in typescript you CAN.

```ts
// TYPESCRIPT
array1[3]=3.2;
console.log(array1) // [1.2, 2.8, 11.2, 32];
// java gives an ERROR if you try this.
```

In java, if you want an array whose size can be changed, you can create a special object called an ArrayList instead. We will look at that another time.

## Looping through an array with a for loop

A common thing to do with any collection is to go through each element one at a time, and do something to it. It's so common, in fact, that you can expect to see these structures usually multiple times in any remotely large project. 

This is the MOST COMMON way because something like it works in every language that has arrays.

```ts
// Assume names[] is an array of strings representing
// the names of students
for (let i = 0; i < names.length; i = i + 1) {
    console.log(names[i]);
}
```
Let's break this code down!

* A `for` loop:star: is a powerful structure from C that allows us to keep repeating something as long as one thing is true. You can see semi-colons separating the parentheses of the for loop.

    * The first section of the `for` loop, `let i = 0`; is run at the very beginning of the loop. In this case, we make a new number variable and set it equal to 0.
    * The second section of the `for` loop, `i < names.length` is the *conditional statement*. The loop will run *as long as* that condition is true. In this case, `i` will be 0 first.
    * The third section of code is run at the END of each loop. In this case, we will make `i` bigger by one at the end of each loop. So `i` will be 0 the first time through, `1` the second time through, and keep getting bigger as long as it is less than the length of the array.

If we assume that `names` has 3 elements in it, then `i` will first take the value 0, then 1, then 2, at which point the loop will end. Those are, conveniently, the indexes of the array! So every element of the array will be printed in this loop.

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
2. How could you loop through an IB collection named NAMES and print out each element in the collection?
3. How would you make a new array holding the first five letters of the alphabet (as strings) in TypeScript?
4. How would you make the same array in java?
5. How would you access the third element ("c") in the previous array?
6. If you want to change the last element to be "z", how would you do that?
7. How do you loop through all of the elements in your array of letters and print them all out (using `console.log`)?
8. Open `ts-node` on your computer by typing the command on your command line. Then try these things. **Try to do each step WITHOUT referring back to the notes. Try 2 or 3 or 4 times if you need to, paying attention to the errors. If you still can't do them, look back, but do NOT copy and paste!**
   1. Create a new string array called `students`. 
   2. Assign this array to `students`: `["luca","joao","sofia","marina","yash"]`
   3. Write a loop that will go through all of the names and, for each one, use `console.log()` to print "Student name is: *name*".

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