# Welcome to IB Computer Science HL

## An Overview

**Computer science** is the study of computers - how they work, how they think, and how they interact.

The **hardware** :star: of a computer is its body, and its brain. All of the physical bits and pieces that turn electricity into math, and turn math into, well, Instagram. The **software** :star: is the actual *mind* of the computer - all of the things the computer "learns," or is taught, that make the hardware bits actually work and do their thing.

We will start the year by studying computer software - specifically we will work on understanding how software is created, or **programmed**. :star: You may already have some experience with computer programming (also called coding).

## Working as a Team

The “Computer Guy” who knows everything about computers does not really exist anymore. Perhaps the last person to completely design and create all of the hardware and software for a commercially viable computer, the Apple II, was Steve Wozniak in 1977, and even he had to use circuit boards that were made in lab by IBM or another electronics company. Today, information technology professionals work within areas of expertise because now there is simply too much hardware and software technology for someone to master it all. At some point everyone must depend on some computer hardware and/or software to work, without knowing how it works. How it works is left as an **abstraction** :star:. As such, people working in computer science fields must be comfortable working with various levels of abstraction so they can focus more fully on their assigned tasks.

The “Lone Genius” who writes programs from scratch has largely disappeared along with the “Computer Guy”. Yes, learning to program does require a certain level of quiet concentration, however, cooperating with and building upon the work of other programmers is an essential skill. The computer software and hardware you use today is the result of teams of experienced and motivated people, working together, to create commercially viable products. Much of the work you do in this course, especially in this first year, will involve working with other programming students face-to-face and also expanding upon existing computer programs written by other programmers. The year will culminate in work toward your individual IA, but to get ready you need to trust, and work with, others.

## Layers of Abstraction

Modern digital computers are extremely complex devices. No single person can possibly understand, completely, every level of their operation.

Computers, at their core, are made up of trillions of tiny circuits called *transistors,* as well as other circuits that hold data called *memory*. The people who design transistors and memory are basically *physical enginers* - at that level, computer science is essentially physics!

The transistors are typically combined in groups of two or three into small circuits called *logic gates*. Those individual logic gates are then combined into larger, combined circuits that do more complicated things, such as add two numbers or read and write data from memory. These larger circuits create the *fundamental operations* of a computer processor and are usually hardwired directly into the computer processor. People who think about how these logic gates should be combined in a given computer, and how many of each type of circuit to make, and how to wire them together, are called *microprocessor designers* or *processor engineers*.

These fundamental operations can then be controlled by sending a signal to a computer in *machine language* (a direct stream of carefully configured `0`'s and `1`'s or *assembly language* (a slightly more human-readable way of writing these signals). Below is a short example of an assembly language:

```nasm
_start:
	mov eax,4            ; 'write' system call = 4
	mov ebx,1            ; file descriptor 1 = STDOUT
	mov ecx,hello        ; string to write
	mov edx,helloLen     ; length of string to write
	int 80h              ; call the kernel

	; Terminate program
	mov eax,1            ; 'exit' system call
	mov ebx,0            ; exit with error code 0
	int 80h              ; call the kernel
```

