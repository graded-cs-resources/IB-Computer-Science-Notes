# Programming Languages, Variables, and Functions

These notes are intended to be used AFTER the "myFirstFunction Typescript" assignment. 

<small>If you want to print this page or any other page here, I recommend the [Github Markdown Printer Chrome extension](https://chrome.google.com/webstore/detail/github-markdown-printer/fehpdlpmcegfpbkgcnaleindodeegapk)</small>

## Programming Languages

A **programming language**:star:, like any language, consists of a vocabulary, syntax, and a set of grammar rules for instructing a computer to perform tasks. Unlike a human language, in a programming language these all need to be unambiguous, consistent, and predictable; computers don't understand emotion or sarcasm!<sup><small>[4.3.3](../unit0_resources/syllabus.md#433)</small></sup>

Computers don't speak the programming languages directly; computer processors only understand a very small number of very specific instructions and all programming languages must be translated to that **machine language**:star:<sup><small>[4.3.5](../unit0_resources/syllabus.md#435)</small></sup>. 

Programming languagues come in LOTS of different shapes and sizes, with different purposes and capabilities. 

### Some key languages for this class
  
* **javascript**:star:, also known as *ECMAScript*, is the native programming language of the web. Javascript files tell a web browser to DO things (like do a calculation, process some data, make an animation, or change something about the page dynamically). Javascript is a *dynamically typed*, *scripting* language that is built directly into browsers. This means it is flexible and quick to write, but not as efficient to run as some other languages, like java. In recent years, technologies have become available that let javascript programs run on desktop computers as well as the browser.
 
* **TypeScript**:star: is a language that is built on top of javascript that provides some more structure, making it easier to write large, powerful apps without as many bugs. TypeScript cannot be run directly; it has to be converted into javascript first. This process of changing from one programming language to another is called **compiling**:star:. As javascript apps have grown, TypeScript has become more popular; in fact, Visual Studio Code and the Github Desktop app you installed are BOTH written in TypeScript, then compiled to javascript! We will start this course working primarily in TypeScript.

* **java**:star: is an older language that works best for making desktop applications and applications that run on network servers. It contains even more structure than TypeScript and is therefore suitable for large, multi-developer development projects. Unlike javascript and TypeScript, java has to be **compiled** into *machine language* to be run. The machine language is then interpreted by a special piece of software called the *Java Virtual Machine*. This keeps it portable, but also very fast, so java apps can, for example, usually run on Window, Linux, and Macs. We will discuss java throughout this course, and switch our primary focus to java down the line (probably next year, though some may do their IAs with it).
  
### Language Features

* Multi-line **comments**:star: start with a `/*` symbol and end with a `*/` symbol. Anything between those symbols will be ignored by the program and are only for humans, to add readability.
  
* A single-line comment begins with a `//` symbol and lasts to the end of the line.
  
* A **variable**:star: is a named place in memory that can hold a piece of data.<sup><small>[4.3.6](../unit0_resources/syllabus.md#436)</small></sup> In TypeScript (and java), variables are **statically typed**:star: which means a particular variable name can only be associated with one *type* of data - for example a **number**, **string** (word, usually written in quotes), or **boolean** (true/false) value. In javascript (and other languages, like Python) variables are **dynamically typed**:star: and can be associated with any type of data. 
  
* A **function**:star: is a named "section" of code that can be run as many times as you want. A function takes one or more *inputs* (also known as **parameters**:star:) inside of parentheses and sends back one *output* (also known as the **return value**:star:). For example, the function below will add two numbers and return the result as a number. Sometimes we think of functions as "sub-programmes" - little programs that run inside the main one and make it easier to understand the code. They are also called *methods*.<sup><small>[4.3.12](../unit0_resources/syllabus.md#4312)</small></sup>

    The example below is a function in TypeScript
  
    ```ts
    function addTwoNumbers(num1:number, num2:number):number {
        return num1 + num2;
    }

    let s:number = addTwoNumbers(2, 3); // The variable s now has the value 5
    ```

    The java equivalent (which will only work with integers, not any number) would look like:

    ```java
    public int addTwoNumbers(int num1, int num2) {
        return num1 + num2;
    }
    public int s = this.addTwoNumbers(2, 3); // The variable s now has the value 5
    ```

    While the javascript version would look a lot like the TypeScript one, but with no mention of numbers (so it would even work for words!)
    
    ```js
    function addTwoValues(val1, val2) {
        return val1 + val2;
    }
    let s = addTwoValues(2,3); // the value s now has the value 5
    let j = addTwoValues("Bob","Smith"); // the value j now has the value "BobSmith"
    ```

## Check your Learning
Try to answer these in your head WITHOUT looking back, then check your answers. This is called *recall practice* and has been shown in many, many studies to be a far more efficient way of learning than if you skip the attempt to recall.

1. What are the features of a programming language?

2. What does it mean to *compile* a program?

3. What does it mean that TypeScript and java have *static variable types*?

4. What is the output value of a function called in programmer speak?

5. Can you write a function in TypeScript or java that accepts two numbers (integers) as input variable, and returns the difference between them?

## Preparing Study Materials

![Bitmoji Books](media/00/bitmoji_books.png){: .image-right}
Create flash cards or a <quizlet.com> deck with the following prompts on the front, then write brief bullets or summaries to put on the back that include what they are for and (if applicable) what they might look like in TypeScript and java:

* programming language
* machine language
* comment
* variable
* compile
* function
* parameter
* return value
* variable type

We have a quizlet class at <https://quizlet.com/join/S8XGx3k93> and you can add your decks there if you make them, but you REALLY should make your own deck before using those of others. You learn as much from making the flashcards as using them, if not more.