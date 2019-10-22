# The Standard Search Algorithms
There are a number of algorithms the IB course will assume you know by memory. These are the “standard algorithms”.

* Sequential search
* Binary search
* Bubble sort
* Selection sort

This notes page only discuss the first two - we will save sorting algorithms for a later unit.

## Sequential search
Search through a set of data sequentially until you find the item you are looking for. 

The basic pseudocode of this algorithm is:

```python
best_answer="not found" #usually a symbol, not a string
loop through each element in our collection
    if the current element is better than best_answer then
        replace best_answer with the current element OR
        return this element if it is perfect
    end if
end for
return best_answer
```

The very simple Typescript version below makes three assumptions: 
1) The collection we are using is an array of numbers
2) The function needs to return the INDEX of the search value
3) If the exact value is not found, the function will return -1 as a signal that the needle is not in the haystack.

```ts
function sequential(haystack:number[], needle:number ):number {
    for (let i=0; i < haystack.length; i++) {
        if (needle == haystack[i]) {
            return(i);
        }
    }
    return(-1);
}
```

The more complicated version below is similar, but returns the index of the "closest" value to the answer if the exact value isn't found. This means it will ALWAYS return a real index, so there's no need to worry about returning -1. It is also in java rather than typescript.

```java
public int sequentialClosest(int[] haystack, int needle) {
    int bestIndex = 0;
    for (int i = 1; i < haystack.length; i++) {
        if (needle == haystack[i]) {
            return i;
        // Math.abs() calculates the absolute value
        }else if (Math.abs(needle - haystack[i]) < Math.abs(needle - haystack[bestIndex])) {
            bestIndex = i;
        }
    }
    return bestIndex;
}
```

Finally, the pseudocode version below uses IB collections rather than arrays. It will return the position of the first exact match, with the first element having position 0.

```python
def method sequential(HAYSTACK, NEEDLE)
    INDEX=0
    HAYSTACK.resetNext()
    loop while HAYSTACK.hasNext()
        if needle = HAYSTACK.getNext()
            return INDEX
        end if
        # have to manually keep track of INDEX
        # since collections don't have length etc.
        INDEX = INDEX + 1
    end loop
    # if we get here, we didn't find it.
    return -1
end def
```
One interesting thing to note with the sequential search is it does not require your data to be sorted ahead of the search. This could save a lot of processing time. If, however, your data is already sorted, you can include within your sequential search a test to see if we have already gone past the point at which the record we are looking for would exist. In that case, we can abort the remainder of the search and return a “not found” result.

## Binary search
A binary search divides a range of values into halves, and continues to narrow down the field of search until the unknown value is found. It is the classic example of a “divide and conquer” algorithm. **Your data must be pre-sorted!**

The version below only returns an index if it finds an exact match.

```ts
function binary(haystack:number[], needle:number ) {
    var max = haystack.length;
    var min = 0;
    while (max >= min) {
        var mid = Math.floor((min+max)/2);
        if (haystack[mid] == needle) {
            return mid;
        }
        if (haystack[mid] > needle) {
            max = mid - 1;
        }
        if (haystack[mid] < needle) {
            min = mid + 1;
        }
    }
    return (-1);
}
```
## Why choose one search of another?

The main advantage of a binary search is SPEED.  Consider an array with, say, 10 million elements. A sequential search will take millions of steps to find the needle. But the binary search, since it divides the problem by two each time, takes far fewer. After one step, you're down to 5 million. Then 2.5 million, 1.25 milion, 625000, then 312500, then 156250, then 78125, 39064, 19532, 9770, 4885, 2442, 1221, 610, 305, 153, 77, 38, 19, 10, 5, 3, 2, 1. That's 24 steps to find the needle, at worst. 24! As opposed to 10 million! Wow!

The DISADVANTAGE is that the array needs to be sorted for binary search to work. That is often not realistic, and even the best sorting algorithm is **much** slower than a sequential search. A sequential search is also much easier to implement, and in a small array is fast enough.

So the decision tree for sequential vs binary looks like this:

![Search flowchart](media/04/search_flowchart.svg)

### Search algorithm exercises
1.  Tracing binary search

    Create a trace table on the binary search algorithm above with the following values:

    ```
    haystack = [1, 2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37]
    1st needle = 15
    2nd needle = 5
    ```
    You can use this first line to give you a start.

    | needle | max | min | max >= min? | mid | haystack[mid] | return |
    | ------ | --- | --- | ----------- | --- | ------------- | ------ |
    |        |     |     |             |     |               |        |
    
    | needle     | max     | min     | max >= min?     | mid     | haystack[mid]     | return     |
    | ---------- | ------- | ------- | --------------- | ------- | ----------------- | ---------- |
    | 15         | 13      | 0       | true            | 6       | 13                |            |
    | 15         | 13      | 7       | true            | 10      | 29                |            |
    | 15         | 9       | 7       | true            | 8       | 19                |            |
    | 15         | 9       | 9       | true            | 9       | 17                |            |
    | 15         | 8       | 9       | false           |         |                   | -1         |
    |            |         |         |                 |         |                   |            |
    | **needle** | **max** | **min** | **max >= min?** | **mid** | **haystack[mid]** | **return** |
    | ------     | ---     | ---     | -----------     | ---     | -------------     | ------     |
    | 5          | 13      | 0       | true            | 6       | 13                |            |
    | 5          | 5       | 0       | true            | 2       | 3                 |            |
    | 5          | 5       | 3       | true            | 4       | 7                 |            |
    | 5          | 3       | 3       | true            | 3       | 5                 | 3          |
    {: .spoiler}

    

2. For each of the following scenarios, decide if a binary search would be worth the effort.
   1. You want to implement a spell checker that looks up words in a large dictionary of several hundred thousand words.
   2. You want to find the the highest score in an unsorted array of high scores.
   3. You have an array of Ball objects in a p5.js game and want to search for the ball closest to the mouse

   > a) Yes! This is a perfect binary search scenario. b) nope. Not sorted, go sequential. c) Nope! Not sorted, go sequential.
   {: .spoiler}