# The many layers of a computer

Computers consist of two universes that interact with each other.

The physical objects that can be touched or manipulated are called the **hardware** of a computer. These include things like keyboards, screens, speakers, and processor chips.

The physical objects are made to *do* things through the aid of **software** - the sets of commands and rules that allow us to make a computer work. Software ranges from very simple instructions to do things like "add two numbers" all the way up to giant applications like Microsoft Word or Fortnite.

## Using abstraction to manage complexity

![Steve Wozniak](media/00/apple-ii.jpg){: .image-right}

<small>Steve Wozniak with an Apple II. Image Credit: [TechCrunch](https://techcrunch.com/2014/11/04/nearly-40-years-later-steve-wozniak-still-brainstorms-ways-the-apple-ii-could-have-been-better/)</small>
{: .image-right}

The “Computer Guy” who knows everything about computers does not really exist anymore. Perhaps the last person to completely design and create all of the hardware and software for a commercially viable computer, the Apple II, was Steve Wozniak in 1977, and even he had to use circuit boards that were made in lab by IBM or another electronics company. Today, information technology professionals work within areas of expertise because now there is simply too much hardware and software technology for any one person to master it all. At some point everyone must depend on some computer hardware and/or software to work, without knowing how it works. How it works is left as an **abstraction**:star:. As such, people working in computer science fields must be comfortable working with various levels of abstraction so they can focus more fully on their assigned tasks.

Let's explore the layers of abstraction for just one part of the computer; the "brain", or computer processor. 

## One Abstraction Tower - the computer processor

The *processor* is the "brain" of the computer - the part of computer that does all of the calculations and "work" of the software. It doesn't do much by itself - it needs other hardware to interact with - but it is arguably the key component that makes something a digital computer.

Most people who work with or even write software do not interact directly with the processor - instead, they interact through many, many layers of abstraction. Let's explore some of those layers.

![Abstraction image from Beauty and Joy of Computing](media/00/hardware-abstraction.png)

<small>Image Credit: [The Beauty and Joy of Computing, Berkeley](https://bjc.edc.org/bjc-r/cur/programming/6-computers/1-abstraction/01-abstraction.html)</small>

### ---- The Hardware Layer ----

#### Level 1 - Transistors

![Transistor](media/00/transistor.png){: .image-right}
Computer processors, at their core, are made up of trillions of tiny circuits called *transistors,* as well as other circuits that hold data called *memory* (specifically, at this level, they are called *CPU registers*). The people who design transistors and memory themselves are basically physicists or electrical enginers - at that level, computer science is essentially physics! We will learn more about the details of how memory and transistors communicate in a later unit.
{: .clearfix} 

#### Level 2 - Logic Gates

![Logic Gates](media/00/logic_gates.png){: .image-right}
The transistors are typically combined in groups of two or three into small circuits called *logic gates*. These logic gates allow circuit designers to forget about the electricity itself, and instead think about the flow of data. We will learn more about logic gates, and the math that surrounds them, in Unit 3.

Even though logic gates are built directly in hardware, we tend to THINK of them as purely theoretical objects.
{: .clearfix}

#### Level 3 - Fundamental Operations
 
Individual logic gates are then combined into larger, combined circuits that do more complicated things, such as add two numbers or read data from memory. These larger circuit build the **fundamental operations** of a computer processor, and are usually hardwired directly into the computer processor. People who think about how these logic gates should be combined in a given computer, and how many of each type of circuit to make, and how to wire them together, are called *microprocessor designers* or *processor engineers*. 

### --- The Software Layer ---

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

![Bitmoji Books](media/00/bitmoji_books.png){: .image-right}
Make flash cards OR a deck on [http://quizlet.com](http://quizlet.com) for the following terms from this introduction. On the back, write a 2-3 bullet point summary. We will return to some of these terms later, and you can add more bullet points then.

* hardware
* software
* abstraction
* transistors
* fundamental operations
* machine language
* assembly language
* programming language

We have a quizlet class at <https://quizlet.com/join/S8XGx3k93> and you can add your decks there if you make them, but you REALLY should make your own deck before using those of others. You learn as much from making the flashcards as using them, if not more.