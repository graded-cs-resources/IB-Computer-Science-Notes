# Welcome to IB Computer Science HL

## An Overview

**Computer science** is the study of computers - how they work, how they think, and how they interact.

The **hardware** :star: of a computer is its body, and its brain. All of the physical bits and pieces that turn electricity into math, and turn math into, well, Instagram. The **software** :star: is the actual *mind* of the computer - all of the things the computer "learns," or is taught, that make the hardware bits actually work and do their thing.

We will start the year by studying computer software - specifically we will work on understanding how software is created, or **programmed**. :star: Hopefully you already have some experience with computer programming (also called coding).

## Working as a team

The “Computer Guy” who knows everything about computers does not really exist anymore. Perhaps the last person to completely design and create all of the hardware and software for a commercially viable computer, the Apple II, was Steve Wozniak in 1977. Today, information technology professionals work within areas of expertise because now there is simply too much hardware and software technology for someone to master it all. At some point everyone must depend on some computer hardware and/or software to work, without knowing how it works. How it works is left as an **abstraction** :star:. As such, people working in computer science fields must be comfortable working with various levels of abstraction so they can focus more fully on their assigned tasks.

The “Lone Genius” who writes programs from scratch has largely disappeared along with the “Computer Guy”. Yes, learning to program does require a certain level of quiet concentration, however, cooperating with and building upon the work of other programmers is an essential skill. The computer software and hardware you use today is the result of teams of experienced and motivated people, working together, to create commercially viable products. Much of the work you do in this course, especially in this first year, will involve working with other programming students face-to-face and also expanding upon existing computer programs written by other programmers. The year will culminate in work toward your individual IA, but to get ready you need to trust, and work with, others.

## Discuss and Answer - Programming Languages

Computers don't understand English. In fact, computers really only understand one thing; tiny bits of electrical signals that can be interpreted as "ons and offs" or "0's and 1's". Every type of computer 'brain', or **Central Processing Unit (CPU)** :star: has its own language of 0's and 1's. However, humans rarely or never write direct machine code. Instead, they use a **programming language** :star: to help them translate from their own understanding of the world to the language of machines. There are MANY programming languages to choose from, with a variety of different syntaxes (words and symbols), philosophies, and goals.

1. What programming languages have you worked with before, if any? Have a brief conversation with your neighbors about what you have done before this class and be ready to share with your teacher. (Yes, things like Scratch and MIT App Inventor count as programming languages!)

Because there are so many programming languages, you'll see a lot of arguments about whch one is **BEST**. Many of these arguments are as silly as a surgeon and lumberjack arguing over which cutting tool is the **BEST**, a scalpel or a chainsaw. Each tool is effective in what it was designed to do; the scalpel and chainsaw are simply designed for different purposes.

```bash
laser                <== MOST PRECISE
scalpel
razor
hand saw
circular saw
axe
acetylene torch
chainsaw
bulldozer            <== MOST POWERFUL
```

Many tasks or tools can be arranged in an order from most precise to most powerful. Consider this list of ways to travel. Is one of these really the **best**?

```bash
walk                <== MOST PRECISE, MORE TEDIOUS
run
bike
car
bus
train
helicopter
prop plane  
jet liner
space shuttle      <== MOST POWERFUL, LESS FLEXIBLE
```

2. Here is a list of ways to move liquids, in no particular order:
  
    `pipeline, garden hose, spray bottle, watering can, canal, syringe, tanker truck, bucket, fire hose`
  
    Discuss with your team how they would be arranged from most precise to most powerful. Is there a **best** way to move all liquids? Be ready to share your order and reasoning with the class.

3. Consider many of the ways people have to communicate. Try placing 7 to 10 examples into the same kind of spectrum. Is there a type of communication that is always the BEST?

4. Brainstorm with your team and come up with another process that can be placed upon a precision versus power spectrum and write the items down in order. Be ready to share with the class.

#### So... programming?
Programming languages can also arguably be placed on a spectrum of precision and power. Here is a short list containing a few well recognized programming languages ordered from more precise to more powerful. You probably won't understand a lot of these words right now, but read them anyway to get some vocabulary churning in your brain.

|Language | Description|
|---|---|
|Machine Language|The computer's only native language. Very difficult for humans to write and understand.|
|Assembly|Super fast executing and capable of direct hardware and memory manipulation. Very hard to write.|
|C|Fast executing procedural language. Requires good understanding of hardware to use well. Good for creating operating systems & game engines|
|C++|General purpose, object oriented version of C, fast but with some modern features.|
|java|General purpose, object-oriented from the ground up, and can run on multiple platforms. Does not require as deep an understanding of hardware as C or C++. Not as fast as C or C++, but still a fast compiled language.|
|Python| General purpose, flexible, *interpreted* language. This means that it is changed into machine language every time it is run, rather than only one time, at the beginning. Python is not as fast as earlier languages int his list, but it is easy to use and powerful.|
|javascript, TypeScript| Originally designed for running on the web, Javascript is designed to be quick and easy, flexible, and powerful (but not necessarily fast). Interpreted, like Python. TypeScript is a layer on top of javascript that adds some more powerful features.|
|SQL|	The language of, specifically, databases, is very powerful but very special-use|
|R| A programming language designed almost exclusively for manipulating data quickly and efficiently.

5. Have you heard of any other programming languages? 
    
6. What factors should a software engineer consider when choosing a language?

## Why TypeScript and java?

In this course, we will actually use *three* languages: TypeScript, java, and IB's *pseudocode*.

**TypeScript** is well-suited to making web-based apps that can run on computers or phones. For many of you, a web-based app will likely be the easiest way to start your IA, so I think it is important to learn a web-based language first. TypeScript is a better fit for the IB curriculum than pure javascript because of its object-oriented nature and its static typing, which make it behave more like java.

The **java** language is widely used and offers a good blend of precision and power. Java and TypeScript share a lot of their syntax, so it should be fairly straightforward to move between them. Java runs on most computers and is a relatively safe language for beginners. While running within its own Java Virtual Machine (JVM), a computer simulator essentially made from software, java provides a layer of protection so a new programmer is unlikely to accidentally harm actual system software or hardware components. Java is also the official language of the Object-Oriented "Option" of the IB, which will be we be pursuing in this course.

Finally, the IB itself uses a **pseudocode** :star: in Paper 1 and Paper 2 exams. Pseudocode is a 'fake' computer langage designed to be easy to read by humans and write by hand. We will spend time reading code in pseudocode, as well as TypeScript and Java, to think about the problem-solving part of writing computer programs.