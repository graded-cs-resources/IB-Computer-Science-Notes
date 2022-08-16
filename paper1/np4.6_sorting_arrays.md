---
title: Search Algorithms
---

# Sorting Algorithms

There are a many different algorithms that can be used to sort arrays, as well as other data structures. The IB expects you to be able to use two and explain different sorting algorithms.

* Bubble sort
* Selection sort

## Bubble Sort

This algorithm iterates through the array many times, in each time making sure the biggest value "bubbles" to the end of the array. Since only one element is guaranteed to be sorted at the end of this bubbling, it has to bubble as many times as there are elements in the array.

### General pseudocode for the overall process

```
Label the final position we are bubbling to as the end of the array
loop from the beginning of the array to the end of the array
    at each step of the loop, compare the element with the one after it. If they are out of order, swap them.
now that we know we have bubbled the biggest to the top, subtract one from the "final" position.
Repeat until all elements have been bubbled.
```


### IB Pseudocode with Arrays

The code below assumes you are sorting an array called `ARR`.

```python
FINAL = ARR.Length() - 1
loop while FINAL >= 1
    loop I from 0 to FINAL - 1
        if ARR[I] > ARR[I+1] then
            //swap
            TEMP = ARR[I]
            ARR[I] = ARR[I+1]
            ARR[I+1] = TEMP
        end if
    end loop
    FINAL = FINAL - 1
end loop
```

### A java equivalent

```java
void bubbleSort(int[] arr) {
    for (int final = arr.length - 1; final >=1; final--) {
        for (int i = 0; i < final; i++) {
            if (arr[i]>arr[i+1]) {
                int temp = arr[i];
                arr[i] = arr[i+1];
                arr[i+1] = arr;
            }
        }
    }
}
```


### Important theory about Bubble Sort

Bubble sort is very slow, because it needs to iterate through the entire array over and over again. Each time the "run" gets a little smaller, but it still has to compare numbers about $n^2/2$ times, which is a lot for big arrays with 1000+ elements. If the array is badly out of order (for example completely reversed), then it also has to swap elements many many times, which can be very slow as well.

You can use the animation linked below to visualize bubble sort (as well as others!)

<a href="https://www.cs.usfca.edu/~galles/visualization/ComparisonSort.html">Cool sorting animations!</a>

## Selection sort

coming soon!