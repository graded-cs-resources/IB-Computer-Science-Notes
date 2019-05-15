# Programming Languagues, Variables, and Functions

These notes are associated with the "First Typescript Lesson" activity your teacher will provide you.

Your teacher will make a Github Classroom link available to you via your normal school LMS or e-mail. Please use that link to access the assignment and read the instructions there to complete and submit the assignment.

## Programming Languages

A **programming language**:star:, like any language, consists of a vocabulary, syntax, and a set of grammar rules for instructing a computer to perform tasks. Unlike a human language, in a programmign language these all need to be unambiguous, consistent, and predictable; computers don't understand emotion or sarcasm!<sup><small>[4.3.3](../unit0_resources/syllabus.md#433)</small></sup>

Computers don't speak the programming languages directly; computers only understand a very small number of very specific instructions and all programming languages must be translated to that **machine language**:star:<sup><small>[4.3.5](../unit0_resources/syllabus.md#435)</small></sup>. 

Programming languagues come in LOTS of different shapes and sizes, with different purposes and capabilities. 

#### Some key languages for this class
* **HTML**:star: file is the primary programming language used for the web, though some say it is not a programming language but a *markup* language.  This means it doesn't tell the computer what to DO, it instead tells the computer what things MEAN. It provides the basic structure of the page and tells the web browser what other files to open. We will learn only a little HTML in this course.
  
* **javascript**:star:, also known as *ECMAScript*, is the native programming language of the web. Javascript files tell a web browser to DO things (like do a calculation, process some data, make an animation, or change something about the page dynamically). Javascript is a *dynamically typed*, *scripting* language that is built directly into browsers. This means it is flexible and quick to write, but not as efficient to run as some other languages, like java. In recent years, technologies have become available that let javascript programs run on desktop computers as well as the browser.
 
* **TypeScript**:star: is a language that is built on top of javascript that provides some more structure, powerful apps without as many bugs. TypeScript cannot be run directly; it has to be converted into javascript first. This process of changing from one programming language to another is called **compiling**:star:. As javascript apps have grown, TypeScript has become more popular; in fact, Visual Studio Code and the Github Desktop app you installed are BOTH written in TypeScript! We will start this course working primarily in TypeScript.

* **java**:star: is an older language that works best for making desktop applications and applications that run on network servers. It contains even more structure than TypeScript and is therefore suitable for large, multi-developer development projects. Unlike javascript and TypeScript, java has to be converted into *machine language*, an unreadable collection of `0`'s and `1`'s to be run; this is also called *compiling*. The machine language is then interpreted by a special piece of software called the *Java Virtual Machine*. This keeps it portable, so java apps can, for example, usually run on Window, Linux, and Macs. We will discuss java throughout this course, and switch our primary focus to java down the line.
  
### Some language features
* In Typescript and java, multi-line **comments**:star: start with a `/*` symbol and end with a `*/` symbol. Anything between those symbols will be ignored by the program and are only for humans, to add readability.
  
* A single-line comment begins with a `//` symbol and lasts to the end of the line.
  
* A **variable**:star: is a named place in memory that can hold a piece of data.<sup><small>[4.3.6](../unit0_resources/syllabus.md#436)</small></sup> In TypeScript (and java), variables are **staticly typed**:star: which means a particular variable name can only be associated with one *type* of data - for example a **number**, **string** (word, usually written in quotes), or **boolean** (true/false) value. In javascript (and other languages, like Python) variables are **dynamicly typed**":star: and can be associated with any type of data. 
  
* A **function**:star: is a named "section" of code that can be run as many times as you want. A functio takes one or more *inputs* (also known as **parameters**:star:) inside of parentheses and sends back one *output* (also known as the **return value**:star:). For example, the function below will add two numbers and return the result as a number. Sometimes we think of functions as "sub-programmes" - little programs that run inside the main one and make it easier to understand the code.<sup><small>[4.3.12](../unit0_resources/syllabus.md#4312)</small></sup>
    ```ts
    function addTwoNumbers(num1:number, num2:number):number {
        return num1 + num2;
    }

    let s = addTwoNumbers(2, 3); // The variable s now has the value 5
    ```

    The java equivalent (which will only work with integers, not any number) would look like:

    ```java
    public int addTwoNumbers(int num1, int num2) {
        return num1 + num2;
    }
    public int s = this.addTwoNumbers(2, 3); // The variable s now has the value 5
    ```

    While the javascript version would look a lot like the TypeScript one, but with no mention of types:
    ```js
    function addTwoValues(val1, val2) {
        return val1 + val2;
    }
    let s = addTwoValues(2,3); // the value s now has the value 5
    let j = addTwoValues("Bob","Smith"); // the value j now has the value "BobSmith"
    ```
