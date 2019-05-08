# Variables, Functions, and Types - Lesson 1

For your first activity, you will read, explore, run, and test a TypeScript program. 

Your teacher will make a Github Classroom link available to you via your normal school LMS or e-mail. Please use that link to access the assignment and read the instructions there to complete and submit the assignment.

## Notes from this assignment
* An **HTML** file is the primary file read by a web browser when it starts to build a webpage. It provides the basic structure of the page and tells the web browser what other files to open.
  
* **javascript** :star: is the native programming language of the web. TypeScript is a language that is built on top of javascript, but it cannot be run by itself; it has to **compile** into javascript first.
  
* In Typescript, multi-line **comments**:star: start with a `/*` symbol and end with a `*/` symbol. Anything between those symbols will be ignored by the program and are only for humans.
  
* A single-line comment begins with a `//` symbol and lasts to the end of the line.
  
* A **variable**:star: is a named place in memory that can hold a piece of data. In TypeScript (and java) variables are **static**, which means a particular variable name can only be associated with one *type* of data - for example a **number**, **string**, or **boolean** (true/false) value. In javascript (and other languages, like Python) variables are **dynamic** and can be associated with any type of data.
  
* A **function** is a named "section" of code that can be used to take one or more *inputs* (also known as **parameters** :star:) inside of parentheses and can send back one or more *outputs* (also known as **return values**). For example, the function below will add two numbers and return the result.
    ```ts
    function addTwoNumbers(num1:number, num2:number):number {
        return num1 + num2;
    }

    var s = addTwoNumbers(2, 3); // s now has the value 5
    ```
