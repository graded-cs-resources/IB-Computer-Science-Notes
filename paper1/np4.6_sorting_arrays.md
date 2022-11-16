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
                arr[i+1] = temp;
            }
        }
    }
}
```


### Important theory about Bubble Sort

Bubble sort is very slow, because it needs to iterate through the entire array over and over again. Each time the "run" gets a little smaller, but it still has to compare numbers about $n^2/2$ times, which is a lot for big arrays with 1000+ elements. If the array is badly out of order (for example completely reversed), then it also has to swap elements many many times, which can be very slow as well. On average, for random elements, bubble sort is the slowest sorting algorithm!

You can use the animation linked below to visualize bubble sort (as well as others!)

<a href="https://www.cs.usfca.edu/~galles/visualization/ComparisonSort.html">Cool sorting animations!</a>

#### Bubble sort - more efficient version

Because bubble sort checks every single element in the array every time it loops through, it can actually identify if the array is sorted - if it never has to swap any element on ANY loop, then that means everything was in order and the sort can stop! This means that if an array is *nearly* sorted, an efficient version of bubble sort will be able to stop early. The efficient version is shown below.

```python
FINAL = ARR.Length() - 1
loop while FINAL >= 1
    SWAPPEDSOMETHING = FALSE
    loop I from 0 to FINAL - 1
        if ARR[I] > ARR[I+1] then
            //swap
            TEMP = ARR[I]
            ARR[I] = ARR[I+1]
            ARR[I+1] = TEMP
            SWAPPEDSOMETHING = TRUE
        end if
    end loop
    if SWAPPEDSOMETHING = FALSE then
        # this means the array is already sorted!
        break #so exit the loop
    end if
    FINAL = FINAL - 1
end loop
```


## Selection sort

### General pseudocode for the overall process

```
Look through the array and find the smallest value, then swap it into index 0
Then look through the array starting at 1, find the smallest remaining value, and swap it into 1
Repeat this until you have swapped the second-biggest element into the second-to-last slot. Done!
```


### IB Pseudocode with Arrays

The code below assumes you are sorting an array called `ARR`.

```python
loop BEGIN from 0 to ARR.Length() - 2
    MINPOS = BEGIN
    loop I from BEGIN + 1 to ARR.Length() - 1
        if ARR[I] < ARR[MINPOS] then
            MINPOS = I
        end if
    end loop
    if MINPOS != BEGIN then
        TEMP = ARR[BEGIN]
        ARR[BEGIN] = ARR[MINPOS]
        ARR[MINPOS] = TEMP
    end if 
end loop
```

### A java equivalent

```java
void selectionSort(int[] arr) {
    for (int begin = 0; begin < arr.length() - 1; begin++) {\
        int minpos = begin;
        for (int i = begin + 1; i < arr.length(); i++) {
            if (arr[i]<arr[minpos]) {
               minpos = i;
            }
        }
        if (minpos !== begin) {
            int temp = arr[begin];
            arr[begin] = arr[minpos];
            arr[minpos] = temp;
        }
    }
}
```


### Important theory about Selection Sort

Selection sort is AlSO very slow, because it needs to iterate through the entire array over and over again. Each time the "run" gets a little smaller, but it still has to compare numbers about $n^2/2$ times, which is a lot for big arrays with 1000+ elements. Unlike bubble sort, however, it will only need to swap values a maximum of one time per element, so a max of about $n$ times - this can make it MUCH faster than bubblesort in situations where there will be a lot of swapping. Unlike bubble sort, however, selection sort can never "know" if an array is already sorted, and so it will never be able to end early in the case of an almost sorted array - for those arrays, bubble sort will be faster.

You can use the animation linked below to visualize selection sort (as well as others!)

<a href="https://www.cs.usfca.edu/~galles/visualization/ComparisonSort.html">Cool sorting animations!</a>