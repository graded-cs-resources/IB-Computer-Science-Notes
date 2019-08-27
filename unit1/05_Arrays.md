# Arrays

An **array**:star: is an ordered list of values (generally of the same type) with a single name. You can access individual elements of the array by referring to its number.

```ts
// TYPESCRIPT declaring an array with start values
let array1:number[] = [1.2, 2.8, 9.9];
```

```java
// JAVA declaring an array with start values
double[] array = {1.2, 2.8, 9.9};
```
The individual *elements* of an array are referred to using an **index**:star:, an integer value that tells you which element you want. In most programming languages (including TypeScript and java) the first index in an array is `0`.

```ts
// working with array elements in TypeScript. java is almost identical.
console.log(array1[0]); // 1.2
console.log(array1[1]); // 2.8
array1[2] = 11.2; //change the value of array element 2
console.log(array1); // [1.2, 2.8, 11.2]
```

In both java and TypeScript, you can use the `length` property to learn how many elements an array has.

```ts
console.log(array1.length); // 3
```

In java, you CANNOT change the length of an array once it is declared, but in typescript you CAN.

```ts
// TYPESCRIPT
array1[3]=3.2;
console.log(array1) // [1.2, 2.8, 11.2, 32];
// java gives an ERROR if you try this.
```

In java, if you want an array whose size can be changed, you can create a special object called an ArrayList instead. We will look at that another time.

## Looping through an array - For Loops

A common thing to do with an array is go through each element in the array, one at a time, and do something to it. The following code is the most common way to do that.

```ts
// Assume names[] is an array of strings representing
// the names of students
for (let i = 0; i < names.length; i = i + 1) {
    console.log(names[i]);
}
```
Let's break this code down!

* A `for` loops is a powerful structure from C that allows us to keep repeating something as long as one thing is true. You can see semi-colons separating the parentheses of the for loop.

    * The first section of the `for` loop, `let i = 0`; is run at the very beginning of the loop. In this case, we make a new number variable and set it equal to 0.
    * The second section of the `for` loop, `i < names.length` is the *conditional statement*. The loop will run *as long as* that condition is true. In this case, i will be 0 first.
    * The third section of code is run at the END of each loop. In this case, we will make `i` bigger by one at the end of each loop. So `i` will be 0 the first time through, `1` the second time through, and keep getting bigger as long as it is less than the length of the array.

If we assume that `names` has 3 elements in it, then `i` will first take the value 0, then 1, then 2, at which point the loop will end. Those are, conveniently, the indexes of the array! So every element of the array will be printed in this loop.