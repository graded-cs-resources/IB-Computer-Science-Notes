---
title: Non-Programming 5.1 - Dynamic, static, and linked lists
---

#  Dynamic vs Static Data structures

The term **data structure** is used for any collection of related items in a computer program or memory, usually connected or accessible through a single reference.

We have talked about two kinds of data structures in [Topic 4 - Collections and Arrays](p4.3_data_structures) - **arrays** and **IB Collections**.

An array is an example of a **static data structure** because it is fixed in size - once you make the data structure you can't make it bigger or smaller. An IB collection is an example of a **dynamic data structure** because you can keep adding elements to it forever - it is not fixed in size.

In topic 5 we will learn about several other data structures, some of which are dynamic (such as *linked lists* and *trees*), some of which are static (like *two-dimensional arrays*), and some of which can be static OR dynamic (like *stacks* and *queues*) depending on how they are implemented. In general, a static data structure will be faster and more space-efficient, while a dynamic structure will be more flexible, with no maximum size and often making it easier to do things like insert, remove, or re-order elements.

# Linked Lists - the simplest dynamic data structure

Here is a quick video that explains the basics of what a *linked list* is and how it works.

<iframe width="560" height="315" src="https://www.youtube.com/embed/KkTzaECSppE" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Here is the IB syllabus section for [Linked Lists](../resources/syllabus.md#linked-lists)

<table>
<thead>
<tr class="header">
<th></th>
<th><strong>Assessment statement</strong></th>
<th><strong>Obj</strong></th>
<th><strong>Teacher’s notes</strong></th> 
<th><strong>Units / Lessons</strong></th>
</tr>
</thead>
<tbody>
<tr class="even">
<td id="5111">5.1.11</td>
<td>Describe the features and characteristics of a dynamic data structure.</td>
<td>2</td>
<td>Students should understand the concepts of nodes and pointer.</td>
<td></td>
</tr>
<tr class="odd">
<td id="5112">5.1.12</td>
<td>Describe how linked lists operate logically.</td>
<td>2</td>
<td><strong>LINK</strong> Logical thinking.</td>
<td></td>
</tr>
<tr class="odd">
<td id="5113">5.1.13</td>
<td>Sketch linked lists (single, double and circular).</td>
<td>3</td>
<td>Students should be able to sketch diagrams illustrating: adding a data item to linked list, deleting specified data item, modifying the data held in the linked list, searching for a given data item.</td>
<td></td>
</tr>
</tbody>
</table>

You also need to be able to describe the basic operations of *adding an item*, *deleting an item*, *retrieving an item*, *traversing*, *seraching*, and *sorting* a linked list. 

## Adding an item to a linked list

To insert an item NEW after a known item called NODE...

1. Point NEW.next to NODE.next
2. Point NODE.next to NEW

To insert a new item at the FRONT of a linked list...

1. Point NEW.next to head
2. Make the head point to NEW

## Removing an item from a linked list

To remove an item called NODE, you need reference to the one before it. Call that PREV.

1. Point PREV.next to NODE.next
2. Point NODE.next to null

To remove the head...

1. Point head to head.next

...done!
   
## Searching a linked list

1. Create a temporary variable TEMP pointing to the head
2. If TEMP.value = searchVal, then return TEMP. Otherwise make TEMP = TEMP.next
3. Repeat step 3 until you find the value OR TEMP.next doesn't exist (list ended)

## Sorting a linked list

It is possible to implement selection sort OR bubble sort on a linked list, because swapping two elements is possible as long as you have references to the two values before them. I've implemented both of them below in pseudocode. You don't technically NEED to write lists for pseudocode, but for sorting, it's easiest to describe in pseudocode!

### Bubble Sort

```none

// first find the end
end = head
loop while end.next != null
    end = end.next
end loop

first = head
prev = null
loop while first != end
    loop while first != end
        if first.val > first.next.val then
            n = first.next
            if (prev != null) then 
                prev.next = n
            end
            first.next = n.next
            n.next = first
            prev = n
        else
            prev = first
            first = first.next
        end if
    end loop
end loop
```


