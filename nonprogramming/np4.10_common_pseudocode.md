---
title: Common Pseudocode Techniques
---

# Common Pseudocode Techniques

## Loop through an array or collection and track something

### Linear search of an array

Used to search for a single element in an array and output *whether* it was found, *where* it was found, or a *related* value from another array

Generally, given an array `ARR`, a length `N`, and a search value `S`

```
FOUND = false // a flag
FOUNDINDEX = -1 //where did we find it?

loop I from 0 to N-1
    VALUE = ARR[I]
    if VALUE = S then
       FOUND = true
       FOUNDINDEX = I
    end if
end loop

if FOUND then
  output "Found" 
  // or output FOUNDINDEX 
  //or output OTHER[FOUNDINDEX]
else
  output "Not found"
end if
```

#### Wrinkle 1 - counting elements that make something true

Given an arr `NUMBERS` of length `N` count how many are positive

```
COUNT = 0
loop I from 0 to N-1
    if NUMBERS[I]>0 then
        COUNT = COUNT + 1
    end if
end loop

Output COUNT + " positive numbers found"
```

#### Wrinkle 2 - finding the average

Given an array of numbers, called `NUMBERS` and a length `N`

```
SUM = 0
loop I from 0 to N-1
    SUM = SUM + NUMBERS[I]
end loop
output SUM / N
```

#### Wrinkle 3 - finding the average of all positive numbers

```
SUM = 0
COUNT = 0
loop I from 0 to N-1
   if NUMBERS[I] > 0
      COUNT = COUNT +1
      SUM = SUM + NUMBERS[I]
   end if
end loop
output SUM / COUNT
```

#### Wrinkle 4 - find a name in one array and calculate from another

Given three arrays `NAMES`, `HEIGHTS`, `WEIGHTS` and a function called `calcBMI(h,w)` output the BMI of all people named John

```
loop I from 0 to N-1
    if NAMES[I] = "John" then
       output calcBMI(HEIGHTS[I],WEIGHTS[I])
    end if
end loop
```

### Linear search of a collection

Given a collection named `COLLECTION` and a search value `S` 
```
FOUND = false
loop while COLLECTION.hasNext()
    VALUE = COLLECTION.getNext()
    if (VALUE = S) then
        // do whatever with value/search
        FOUND = true
    end if
end loop

if FOUND then
   output "Found!"
else
   output "Not found"
end if
```

#### Wrinkle - how many are between -1 and 1?

```
HOWMANY = 0
loop while NUMBERS.hasNext()
    VALUE = NUMBERS.getNext()
    if VALUE >= -1 and VALUE <= 1 then
      HOWMANY = HOWMANY +1
    end if
end loop

output HOWMANY
```

#### Wrinkle - average values in a collection

```
SUM = 0
COUNT = 0
loop while NUMBERS.hasNext()
    COUNT = COUNT + 1
    SUM = SUM + NUMBERS.getNext()
end loo

output SUM / COUNT
```

### Output all elements in an array or collection

For arrays, you HAVE to know the length of the array from context.

```
loop I from 0 to N-1
    output ARR[N]
end loop
```

For collections, though, no need!

```
COLLECTIOn.resetNext()
loop while COLLECTION.hasNext()
    output COLLECTION.getNext()
end loop
```


## Convert a collection to an array or vice versa

### Collection -> Array

You will always be given a name that holds a collection, e.g., `NAMES`

You will be told that an array exists that is large enough to hold the collection, e.g. `ARR`

```
COUNTER = 0
NAMES.resetNext()
loop while NAMES.hasNext()
    ARR[COUNTER] = NAMES.getNext()
    COUNTER = COUNTER + 1
end loop

// COUNTER now holds how many elements you added to the array
// a.k.a. It is basically Arr.length
```

### Array -> Collection

You will be given an empty collection with a name, e.g. `COLL`

You will be given an array, e.g. `ARR` and you will know how many elements are in the array, e.g. `N`

```
loop COUNTER from 0 to N - 1
    NAMES.add(ARR[COUNTER])
end loop
```

## Binary search an array

Assumptions: array NUMBERS is sorted from lowest to highest

Recall that binary search is about looking at a middle value and using that to decide if our search value is in the top half or the bottom half. Then repeating that until we find the value or run out of elments to examine.

With arrays, we keep track of the "halves" using variables that point to the beginning and end of the array we care about

```
HI = ARR.length //usually provided actually
LO = 0
FOUND = false //flag to let us end the loop

loop while FOUND = false and HI >= LO
    //this loop will end if we find the element OR 
    //if we run out of array to search, which happens when HI < LO

    MID = (LO + HI) div 2 //integer division
    if ARR[MID]=S then
        FOUND=true
    else if ARR[MID] < S then
        LO = MID + 1
    else if ARR[MID] > S then
        HI = MID - 1
    end if
end loop

if FOUND then
    output "Result found at location " + MID
else
    output "Not found"
end if
```

## Selection sort of an array

Sorts the array by searching for the lowest (or highest) value and swapping it to the front of the unsorted part of the array

given `ARR` and length `N`

```
SORTPOS = 0

// selection sort works by finding the smallest item and swapping it to the front
// then finding the smallest REMAINING item and swapping it to position 2
// and so on

//the outer loop keeps track of 'where am I swapping TO'
loop SWAPPOS from 0 to N-2 

    // start by assuming the smallest (remaining) item is in out swap spot
    SMALLESTVAL = ARR[SWAPPOS]
    SMALLPOS = SWAPPOS
    
    //the inner loop searches the rest of the array for a smaller item
    loop SEARCHPOS from SWAPPOS+1 to N-1
        if ARR[SEARCHPOS] < SMALLESTVAL then
            SMALLESTVAL = ARR[SEARCHPOS]
            SMALLPOS = SEARCHPOS
        end if
    end loop

    // swap the elements in SMALLPOS and SWAPPOS

    TEMP = ARR[SORTPOS]
    ARR[SORTPOS] = ARR[SMALLPOS]
    ARR[SMALLPOS] = TEMP
end loop
```

## Bubble Sort of an Array

Bubble sort works by going through the array and constantly comparing two elements at a time, swapping them if they are out of order. 

This results in the largest value "bubbling up" to the end, so the next time through we can assume that last value is sorted.

Assume `N` is the length of the array

```
//each loop will bubble up one element to the top, so we need as many loops as elements
// minus one, because once the second-to-last one bubbles up we are good!
loop I from 0 to N - 1
    //END represents the last unsorted element
    END = N - I
    loop J from 0 to END-1
        //if our element is greater than the one after, swap them
        if ARR[J] > ARR[J+1] then
           TEMP = ARR[J]
           ARR[J] = ARR[J+1]
           ARR[J+1] = TEMP
        end if
    end loop
    //after each run of this inner loop, one element has bubbled up
end loop
// N - 1 elements have bubbled up, leaving the array sorted!
```