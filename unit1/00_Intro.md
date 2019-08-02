---
title: Introduction
layout: default
---

# Welcome to IB Computer Science

## An Overview

**Computer science** is the study of computers - how they work, how they think, and how they interact.

The **hardware**:star: of a computer is its body, and its brain. All of the physical bits and pieces that turn electricity into math, and turn math into, well, Instagram. The **software**:star: is the actual *mind* of the computer - all of the things the computer "learns," or is taught, that make the hardware bits actually work and do their thing. We will learn a good bit about hardware this year, though we will spend more time working with software, specifically learning how to **program**:star:, or code, our own software to solve problems.

## Working as a Team

 The computer software and hardware you use today is the result of teams of experienced and motivated people, working together, to create commercially viable products. Much of the programming work you do in this course, especially in this first year, will involve working with other students face-to-face and also expanding upon existing computer programs written by other programmers. The year will culminate in work toward your individual IA, but to get there you need to be ready to work with, and trust, others. We will spend at least some time every single day in study teams, which will be changed occasionally; sometimes randomly, sometimes not. Please be ready for that, and embrace the chance to learn from different people.

## Layers of Abstraction

The “Computer Guy” who knows everything about computers does not really exist anymore. Perhaps the last person to completely design and create all of the hardware and software for a commercially viable computer, the Apple II, was Steve Wozniak in 1977, and even he had to use circuit boards that were made in lab by IBM or another electronics company. Today, information technology professionals work within areas of expertise because now there is simply too much hardware and software technology for any one person to master it all. At some point everyone must depend on some computer hardware and/or software to work, without knowing how it works. How it works is left as an **abstraction**:star:. As such, people working in computer science fields must be comfortable working with various levels of abstraction so they can focus more fully on their assigned tasks.

Let's explore the layers of abstraction for just one part of the computer; the "brain", or computer processor. 

### Layers of Abstraction in a computer processor

![Abstraction image from Beauty and Joy of Computing](media/00/hardware-abstraction.png)

<small>Image Credit: [The Beauty and Joy of Computing, Berkeley](https://bjc.edc.org/bjc-r/cur/programming/6-computers/1-abstraction/01-abstraction.html)</small>

#### Level 1 - Transistors

Computer processors, at their core, are made up of trillions of tiny circuits called *transistors,* as well as other circuits that hold data called *memory* (specifically, at this level, they are called *CPU registers*). The people who design transistors and memory themselves are basically physicists or electrical enginers - at that level, computer science is essentially physics! We will learn more about the details of how memory and transistors communicate in a later unit.
  
#### Level 2 - Logic Gates

The transistors are typically combined in groups of two or three into small circuits called *logic gates*. These logic gates allow circuit designers to forget about the electricity itself, and instead think about the flow of data. We will learn more about logic gates, and the math that surrounds them, in Unit 3.
  
#### Level 3 - Fundamental Operations
 
Individual logic gates are then combined into larger, combined circuits that do more complicated things, such as add two numbers or read data from memory. These larger circuit build the **fundamental operations** of a computer processor, and are usually hardwired directly into the computer processor. People who think about how these logic gates should be combined in a given computer, and how many of each type of circuit to make, and how to wire them together, are called *microprocessor designers* or *processor engineers*. 

#### Level 4 - Machine / Assembly language

These fundamental operations can then be controlled by sending a signal to a computer in *machine language* (a direct stream of carefully configured `0`'s and `1`'s) or, much more commonly, *assembly language* (a slightly more human-readable way of writing these signals) that is then turned by a computer into machine language. Below is a short example of an assembly program that adds 3 and 4 and prints the result (you do NOT need to understand this completely or be able to reproduce it!)

```nasm
_start:             ; tell the computer we are starting

mov     eax, 3  	; store the number 3 in register a
mov     ebx, 4		; store the number 4 in register b
add     eax, ebx    ; add the stored 3 and 4 and put the result (7) in register a
add     eax, '0'	; by adding the character '0', the 7 turns into printable '7'

mov     ecx, eax	; put the '7' into register c
mov     edx, 1		; put the length of the message, 1, into register d
mov     ebx, 1      ; put 1 into ebx. This sends a signal that we will want to print on the screen, not elsewhere.
mov     eax, 4      ; put 4 into eax. This tells the processor we want to actually write something.
int     0x80        ; tell the processor to do its thing.
```

Though more readable than machine language, assembly is clearly very hard to understand, and requires that the person writing the code be VERY intimately familiar with the specific computer processor being used. Most people who write in assembly regularly would probably consider themselves to be *computer engineers*, and they write things like operating systems, compilers, and hardware drivers. We will NOT be using any assembly language this course.

#### Level 5 and higher - Higher Level programming

High level *Programming Languages* can be used to abstract the machine language used for sending instructions to computers into a more readable, almost human language. For example, in the language `C`, one of the first high level computer programming languages to gain popularity starting in the 70s and still in use, the same program as above might be written:

```c
#include <stdio.h>
int main()
{
	int a = 3;
	int b = 4;
	printf("%d" , a + b);
	return 0;
}
```

And in the even simpler, even MORE abstracted language of Python, might simply be:

```Python
a = 3, b = 4
print a + b
```

People who work using languages like these are called *computer programmers* or *software developers*. While developing software in these languages, programmers themselves often add even MORE layers of abstraction. We will spend a large portion of this class working on learning how to write and solve problems using these high-level languages.

## Conclusions

The previous exercise doesn't even get into the many OTHER layers of abstraction inherent in working with modern computers. Input devices (keyboards, mice, gamepads), output devices (screens, printers, speakers), and storage devices (hard disks, SD cards, CDs) are ALL necessary for a computer to be useful, and every one of them has multiple layers of abstraction between their physical operation and how a computer programmer might use them.

**Computer Science** concerns itself with all of these layers, but focuses on the abstract over the physical. At the end of this course, you will NOT be ready to get a job as a software developer, nor as an engineer. That takes on-the-job training and a level of specificity this course won't be able to give you. But you'll have a basic understanding of the entire scope of how computers work and communicate, and the beginnings of an ability to mold them to your desires. 

Let's get to it.

## Study Materials

Every reading will include a section like this at the end, with suggestions for things to make to study later. Regularly returning to this content will enable you to remember for a long time - two years!

### Flashcards
Make flash cards OR a deck on [http://quizlet.com] for the following terms from this intro. On the back, write a 2-3 bullet point summary. We will return to some of these terms later, and you can add more bullet points then.

* hardware
* software
* abstraction
* transistors
* fundamental operations
* machine language
* assembly language
* programming language

We have a quizlet class at [https://quizlet.com/join/S8XGx3k93] and you can add your decks there if you make them, but you REALLY should make your own deck before using those of others. You learn as much from making the flashcards as using them, if not more.