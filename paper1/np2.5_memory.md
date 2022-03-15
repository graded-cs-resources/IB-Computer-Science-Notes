---
title: Paper 1 Lesson 2.5 - Memory and Storage
---

# Memory and Storage

## Memory in a computer

Every computer has multiple places where data - 0's and 1's - can be stored. Each place serves a different purpose.

### CPU Registers

**CPU Registers**:star: are the smallest, fastest pieces of memory in a computer. They are built from transistors directly, and are stored directly inside the computer processor. You can see more about how they are made starting at time 1:30 of the video below (you will not need to know the circuit, but it's exciting to see how you can build memory using logic gates!)

<iframe width="560" height="315" src="https://www.youtube.com/embed/fpnE6UAfbtU?start=90" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
   
### Primary Memory

**Primary memory** is memory that is necessary for the computer to function at all. It has a direct connection to the CPU and enables the CPU to do its work.

There are two main types of primary memory:

1. **ROM**:star: (*Read Only Memory*) is a tiny piece of medium-fast memory built into the main structure of the computer (but not directly into the main processor chip). It is usually small and contains only the tiny bit of software needed to actually start a computer, before the *operating system* takes over. If you've ever "flashed a firmware update" on your computer, router, or phone, you have edited the ROM. This is the *only* part of primary memory that is persistent; that is, it holds information even when power is removed.<sup><small>[2.1.2](../resources/syllabus.md#212)</small></sup>
   
2. **RAM**:star:, or *Random Access Memory* is the part of the computer where data is stored that is being actively used by running programs. When somebody says "primary memory" they USUALLY mean the RAM! The RAM has a pipe, called a *bus* that connects it directly to the CPU, and information is constantly moving back and forth between the CPU registers and the RAM. We will see more about this in the next lesson. <sup><small>[2.1.2](../resources/syllabus.md#212)</small></sup>
   
   1. **Cache**:star: is an even faster and smaller section of memory that is used by the computer to store things it knows it may need again really soon. It is usually built in to the same chip that holds the CPU. From the perspective of a *programmer*, the cache and RAM are essentially interchangeable, but they make a huge difference at the low level; computer processor designers spend lots of time optimizing cache usage, since the cache can be up to 100 times faster than the RAM!. It is very expensive, however, so most computers have less than a gigabyte of cache total, and often significantly less of the fastest level 1 cache.<sup><small>[2.1.3](../resources/syllabus.md#213)</small></sup>

![The hierarchy of memory](media/memory_heirarchy.jpg)  
<small>Image credit: <https://www.slideshare.net/rahulbandhe/basics-of-semiconductor-memories-presentation></small>
{: .image-right style="width:50%;border:.5px solid black;"}

{: .clearfix}

### Secondary Memory

**Secondary Memory**:star: or **secondary storage** is the part of a computer where data lives when it's not being directly used. In most computers this will be a *hard drive* or *solid-state storage.* This could also be exterior storage such as CDs, DVDs, USB Flash drives, SD Cards, video game cartridges, and so forth. This memory is slow, but usually cheap (relatively), and is **persistent**:star:, which means that it will continue to hold data even when power is disconnected. <sup><small>[2.1.5](../resources/syllabus.md#215)</small></sup>

## What goes in the memory?

Though the different storage types all works very differently at a physical or chemical level (hard drives use magnets, dvds use lasers, etc), for a programmer it is reasonable to think of memory as holding a giant series of `0`'s and `1`s. This is another example of an [**abstraction**!](../np1.1_abstraction.md)<sup><small>[4.1.17](../resources/syllabus.md#4117)</small></sup>

Each `0` or `1` is called a **bit**:star:.<sup><small>[2.1.9](../resources/syllabus.md#219)</small></sup> By itself, a bit can't convey a lot of meaning, since there are only two options. But if you combine the `0`s and `1`s into groups, you can get more interesting combinations. A group of 8 bits is called a **byte**:star: and provides $$2^8=256$$ possible values, from `0000 0000` to `1111 1111`. 

Given a single byte (or more than one) we can train our programs to *interpret* it in different ways. For example, the byte `0011 1011` might be interpreted as the integer `59`, or the text character `a`, or the percentage `23.13%`, depending on the interpretation instructions we are using. Later in this course we will explore some of these encoding schemes in detail.

## Virtual Memory

Occasionally, a computer will completely run out of available cache and RAM to keep track of all of the running programs. In that situation, the **operating system**, which is the primary software that controls how the computer works, may allow programs to use **virtual memory**, or *swap space*, which allows the programs to use space on persistent storage in the same way they might use RAM.

The advantage of this is that the computer can continue to run all of the programs on the computer without causing any sort of error caused by insufficient RAM, and extremely large programs can run even on devices with less RAM.

The disadvantage is that persistent storage solutions are MUCH slower than RAM (often by 50 or 100 times or more!) so the computer will run the programs much more slowly. Faster secondary storage options, such as modern Solid State Drives, are much faster than older drives and make virtual memory more feasible, but RAM is still significantly more efficient.

# Study Materials

## Check your Understanding

1. What is the difference between RAM and ROM?
   
    <details markdown="1"><summary>Click to expand answer</summary>
    RAM means Random Access Memory, and it is the section of primary memory that holds the data the computer is using as it works. ROM stands for Read Only Memory, and is the special part of primary memory that holds the important information needed to get the computer started, sometimes called the firmware. Other than their acronym, they have almost nothing in common!
    </details>
   
2. How many bits are in one byte?
    <details markdown="1"><summary>Click to expand answer</summary>
    8
    </details>
   
3. What are some types of primary memory?
    <details markdown="1"><summary>Click to expand answer</summary>
    ROM, RAM, Cache, and CPU Registers
    </details>

4. Why is it important that we have some forms of persistent memory?
    <details markdown="1"><summary>Click to expand one possible answer</summary>
    Without persistent memory, the computer would have to start over from scratch every time its power was removed! Things like documents, photos, settings, and so forth require persistent storage to exist in a digital world.
    </details>

5. What is the only type of primary memory that is persistent?
    <details markdown="1"><summary>Click to expand answer</summary>
    The ROM is persistent; it has to exist between power cycles or else the computer won't be able to start.
    </details>

6. **May 2019, problem 15, SL**  
   A company that provides training for teachers plans to set up a training room in its offices with a network of 15 computers. Each computer is 1 TB of storage and 16 GB of RAM. 
   1. Identify two characterists of RAM

   2. State the purpose of persistent storage on the computers.

   <details markdown="1"><summary>Click to expand official IB markscheme</summary>
   1. *Award [2 max]*  
      RAM is volatile / contents erased when power is switched off;  
      Access speed is fast / faster than hard drive;  
      Data / instructions can be read from and written to it / /RAM can be overwritten;  
      Size is limited;
   2. *Award [1 max]*  
      To store programs / files / data in a non-volatile device so it isn't lost;  
      Stores more data as is has more capacity; 
   </details>

7. **May 2019, problem 5, HL**  (HL only!) 
   Outline one advantage and one disadvantage of using virtual memory.
   
   <details markdown="1"><summary>Click to expand the official IB markscheme</summary>
    Award [1] for an advantage, [1] for a disadvange, and [1] EACH for outlines (additional details)
    4 marks total

    **Potential Advantages**

    Allows more applications to run than there is available physical memory; 
    By the use of page/swap files/part of hard disk as primary memory; 

    Larger application can run 
    With less real RAM; 

    **Potential Disadvantages**
    
    Applications run more slowly;  
    Uses hard drive memory as primary memory / takes more time to switch between 
    applications;  
    
    When a computer's virtual memory resources are overused /Reduced amount of 
    hard drive space available for your use;  
    programs lock-up/do not run/disk thrashing;
   </details>

## Terms

![Bitmoji Books](media/bitmoji_books.png){: .image-right}
Create flash cards or a [quizlet](http://quizlet.com) deck with the following words on one side and a quick summary on the other.
* primary memory
* secondary memory
* persistent memory
* RAM
* ROM
* cache
* registers
* bit
* byte
* operating system (HL only)
* virtual memory (HL only)

## Related External resources

* [Mr. Wachs Workbook - Computer Organization](https://drive.google.com/file/d/1YLGWShcZZNXQWOYYcuGRUxZ-EAc3xF3F/view?usp=sharing) - These very comprehensive notes by computer science teacher [Mr. Wachs](https://mrwachs.wordpress.com/current-classes/computer-science-i-b/) include notes on all of Topic 2. He includes some information that I don't think is necessary, but its an interesting and complete read.
* [Mr. Wachs Videos](https://www.youtube.com/playlist?list=PLZbVESc4rBHlBi2gwdlppxQJX4EOmsSxx) - Discussion of memory (this page) begins about halfway through the Computer Organization - Part 2 video.
* [IB CompSciHub Topic 2](https://ib.compscihub.net/paper-1/topic-2) - Look at the linked PDF notes from 2.1.2, 2.1.3, and 2.1.5 for notes related to this page.
* [Paul Baumgarten's Topic 2 Notes](https://pbaumgarten.com/ib-compsci/unit-2/unit-2-computer-architecture.pdf) - The Memory topic is part 5 of these notes, a little more than halfway down.