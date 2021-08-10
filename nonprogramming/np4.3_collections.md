---
title: Non-Programming 4.3 (associated with Programming 3.1!) - Introducing IB Collections
---
# Collections in the IB Exam

## What is a collection?

A **collection**:star: or a **data structure** is a general term for a set of MANY values that are connected, so that the entire group can be accessed with a *single* variable name. Collections will ALWAYS provide a way to **add data** and **retrieve data** and will USUALLY provide a way to **iterate through** the data, retrieving ever element one after the other.

Some types of collections that you might see in modern programming languages include *arrays*, *linked lists*, *doubly linked lists*, *stacks*, *queues*, *dictionaries*, and *array lists* - most of these will not be explored in the SL curriculum, with the two exceptions that follow.

## The IB Collection

The IB defines their own *special type* of collection for use in all of their problems that involve *pseudocode*. We will call this special type of data structure the **IB Collection**. It is intentionally very limited, with only a few ways of interacting with it.

An IB Collection works like an class, and the class defines the following methods.

| Method  name  | Brief description                      | Example: <br>HOT, a collection of temperatures | Comment                                                                                                                                                              |
| ------------- | -------------------------------------- | ---------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `addItem()`   | Add item                               | `HOT.addItem(42)`<br>`HOT.addItem("chile")`    | Adds an element to the end of the collection that contains the argument, whether it is a value, String, object, etc.                                                 |
| `getNext()`   | Get the next item                      | `TEMP = HOT.getNext()`                         | `getNext()` will return the first item in the collection when it is first called.<br><br>Note: getNext() does not remove the item from the collection.               |
| `resetNext()` | Go back to the start of the collection | HOT.resetNext()<br>HOT.getNext()               | Restarts the iteration through the collection.  The two lines shown will retrieve the first item in the collection.                                                  |
| `hasNext()`   | Test: has next item                    | `if HOT.hasNext() then`                        | Returns TRUE if there are one or more elements in the collection that have not been accessed by the present iteration: used to see if we are at the end of the list. |
| `isEmpty()`   | Test: collection is empty              | `if HOT.isEmpty() then`                        | Returns TRUE if the collection does not contain any elements.                                                                                                        |

### Important understandings of an IB Collection

Here are some important things to understand about IB collections

* You cannot remove items from an IB collection at all
* You can ONLY access IB collection items in the order they were added - if you want to access the 100th element, you will have to call the `getNext()` method 100 times
* You cannot know the length of an IB collection without counting the items yourself by accessing every element
* An IB collection can be *arbitrarily* long - your program can add items dynamically as long as is necessary, you do not need to know the length of a collection in advance.

### Check Your Understanding 

1. What does the "resetNext()" command do for IB collections?
   
   <details markdown="1"><summary>Click to expand answer</summary>
   It makes it so the next time you call `getNext()` you will get the FIRST element.
   </details> 

2. What will be printed (output) by the following code?

   ```python
   COL.addItem("tree")
   COL.addItem("flower")
   COL.addItem("shrub")
   COL.addItem("grass")

   COL.resetNext()
   COL.getNext()
   output COL.getNext()
   COL.getNext()
   output COL.getNext()
   ```
   <details markdown="1"><summary>Click to expand answer</summary>
   ```
   flower
   shrub
   ```
   </details>

3. What will be printed (output) by the following code?
   ```python
   COL.addItem("tree")
   COL.addItem("flower")
   COL.addItem("shrub")
   COL.addItem("grass")

   COL.resetNext()
   loop while COL.hasNext()
      output COL.getNext()
   end loop
   ```
  
4. Write an algorithm that assumes you already have two collections, START and END. If START is empty, output the sentence "Nothing to copy". If END is *not* empty, output the sentence "Destination not empty" Otherwise, it all of the elements from the collection START into the collection END, then output "Collection copied"

   <details markdown="1"><summary>Click to expand answer</summary>
   ```python
   if START.isEmpty() then
      output "Nothing to copy"
   else if NOT END.isEmpty() then
      output "Destination not empty"
   else
      START.resetNext()
      loop while START.hasNext()
         END.addItem(START.getNext())
      end loop
      output "Collection copied"
   end if
   ```
   </details>

For more practice, visit the IB Pseudocode practice site at https://graded-cs-resources.github.io/CodingBatPseudo/ and looking at the problems under the subheading **Collections**

## Key terms

* collection
* collection method addItem()
* collection method getNext()
* collection method resetNext()
* collection method hasNext()
* collection method isEmpty()
* iterating through a collection