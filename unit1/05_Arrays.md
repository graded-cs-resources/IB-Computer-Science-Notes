# Arrays

An **array**:star: is an ordered list of values (generally of the same type) with a single name. 

```ts
// TYPESCRIPT declaring an array with initial values
let array1:number[] = [1.2, 2.8, 9.9];

// no initial value
let array2:number[];
```

```java
// JAVA declaring an array with start values
double[] array1 = {1.2, 2.8, 9.9};

// an array with no initial value. 
// Must know size in advance!
double[] array2 = new double[5];
```

The diagram below shows an image of `array1` in java:

![java array](media/05/Array&#32;diagram.svg)

In lower-level languages like java or C, you can be certain that the elements of the array are actually stored next to each other in the RAM or cache; this ensures that accessing the array is as efficient as possible, but requires two things: 

1. Every element in the array must be the same type
2. The length of the array must be *fixed* and cannot change

More dynamic languages like javascript and TypeScript allow you to change the size of arrays and even store multiple types, which makes them more flexible but less fast; at the lowest level of memory, they may look quite different from the predictable java arrays. When the IB exam refers to an array it assumes you are using a fixed-length structure like the one from java; it will refer to ones that can change as *lists* or *collections*.

## Accessing Elements

The individual *elements* of an array are referred to using an **index**:star:, an integer value that tells you which element you want. In most programming languages (including TypeScript and java) the first index in an array is `0`.

```ts
// working with array elements in TypeScript. 
// java would be nearly identical.
console.log(array1[0]); // 1.2
console.log(array1[1]); // 2.8
array1[2] = 11.2; //change the value of array element 2
console.log(array1); // [1.2, 2.8, 11.2]
```

In both java and TypeScript, you can use the `length` property of an array to learn how many elements an array has.

```ts
console.log(array1.length); // 3
```

In java, as mentioned earlier, you CANNOT change the length of an array once it is declared, but in typescript you CAN.

```ts
// TYPESCRIPT
array1[3]=3.2;
console.log(array1) // [1.2, 2.8, 11.2, 32];
// java gives an ERROR if you try this.
```

In java, if you want an array whose size can be changed, you can create a special object called an ArrayList instead. We will look at that another time.

## Looping through an array, two ways

### Option 1 - The For Loop with an Index

A common thing to do with an array is go through each element in the array, one at a time, and do something to it. The following code is the MOST COMMON way to do that.
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

### Option 2 - The For...of loop

This looping is so common that both TypeScript and java provide *shortcuts* for it (though languages like C and javascript do not, so the above loop is still important!)

```ts
// typescript
for (let thisName:string of names) {
    console.log(thisName);
}
```

```java
// java
for (String thisName: names) {
    System.out.println(thisName);
}
```

This is certainly shorter and likely easier to use, but it is also less common; the index loop has been around for decades, works well, and needs to be understood by all programmers!

## Check your Understanding
1. How would you make a new array holding the first five letters of the alphabet (as strings) in TypeScript?
2. How would you make the same array in java?
3. How would you access the third element ("c") in the previous array?
4. If you want to change the last element to be "z", how would you do that?
5. How do you loop through all of the elements in your array of letters and print them all out (using `console.log`)?

## Flashcards

* array
* contiguous memory
* index
* accessing an array element
* for loop
* looping through an array (*write the loop on the back*)