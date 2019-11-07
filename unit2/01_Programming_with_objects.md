# Introduction to Objects and Classes

Imagine you are writing a note-keeping app. You want to be able to use the app to create notes with different content and background colors.

One way to approach this would be using *arrays*[D.3.8](../unit0/syllabus.md#D38){: .syl}, as shown below:

```ts
let note_contents:string[] = ["This is my first note.","This is my second."];
let note_colors:string[] = ["red","blue"];
```

As long as you were careful to keep each array in the same order, it would be possible to add new notes by simply adding elements to both arrays, and then you could cycle through them. If you wanted to add an *action* to the notes, you could write functions like this:

```ts
function change_note_color(noteNumber:number, color:string){
    note_colors[noteNumber] = color;
}
```

This would work, but if you wanted to add an additional *property* to your note - for example, `date_created` or `due_date` - you'd need to add additinal arrays and keep track of even more things. This is where the idea of an *object* really starts to become useful and powerful.

## What is an object?

An **object**:star: is a way to organize the data in a program by its purpose and function. It is simply a collection of **properties**:star: (basically variables) and **methods**:star: (basically functions) that are collected under one name. 

In TypeScript you can make SINGLE objects like this:

```ts
let note1 = {
  // the first two values are properties of the object
  // these are also called *instance variables*
  contents: "This is my first note",
  color: "red",
  width: 100,
  // this value is a method
  change_color: function (color: string) {
    this.color = color; // `this` is a keyword that means the current object itself.
  }
}
// We access the properties and methods of an object using the dot . operator
console.log(note1.color) // "red"
console.log(note1.contents) // "This is my first note",
note1.change_color("green");
console.log(note1.color) // "green"
```

This helps us group information about `note1` together, but it doesn't really help us make new notes or take advantage of the fact that all notes have the same properties. We will, mostly, not make single-use objects like this in our course. Instead, we will focus on describing groups of objects, using our next big idea: *classes*.

## Classes

A **class**:star: is a DESCRIPTION of an object, a template or recipe that describes the overall shape and behavior of a type of object.[D.3.1](../unit0/syllabus.md#D31){: .syl} It describes what types of information we will hold about the object, what types of methods will be done to or by the object, and how to create a new **instance**:star:, or specific case, of the object.

When you define a class you are essentially creating your own data type. The class below defines a new object of type `Note`.

```ts
class Note { //classes are, by convention, capitalized
  /*============== PROPERTIES / INSTANCE VARIABLES =======================*/
  // No need for 'let'. These define the STATE or DATA of the object.
  contents:string;
  color:string;
  complete:boolean;

  /*========= CONSTRUCTOR ====================*/
  // The constructor is a special function that defines how to create a new
  // *instance* of an object. Does not need 'function'. Returns a new Note object.
  constructor(contents:string, color = "yellow") {
    // the "this" keyword lets us access the particular object we are creating
    // and save the parameters to its properties.
    this.contents = contents;
    this.color = color;
  }

  /*=============METHODS===================*/
  // methods define the ACTIONS of the object.
  // they do not need the function keyword when in a class.
  check_off():boolean {
    this.complete = true;
  }
} // class over! We have defined our object type. Now we can use it.

// we use the "new" command to call the constructor and get a new note
// every time the "new" command is called it creates a new object then runs the 
// constructor method on the object.
let note1: Note = new Note("This is my first note", "red");
let note2: Note = new Note("This is my second note", "blue");
let note3: Note = new Note("This is my third note. It is yellow by default!");
```

You now have three new notes! The diagram below provides a visual of what we've got. The first box, at the top, is called a *UML class diagram*, and you will be expected to construct them for IB tests.

![class diagram](media/01/Note&#32;Class&#32;Diagram.svg){: style="width:80%;margin:auto;display:block;"}

You could still use arrays to help you keep track of an unknown number of notes, but now you only need ONE array - an array of Note objects - instead of multiple arrays.

```ts
let notes:Note[] = [];
// the "push" method used below adds a new item to the end of an array in TypeScript
// java does not have an equivalent for arrays, but it does have other structures
// that can do this.
notes.push(new Note("first note!"));
notes.push(new Note("second note!","green"));
notes.push(new Note("third note","purple"));
notes.push(new Note("oh my god how many notes????","orange"));
```

## Check your Understanding

1. What is an instance variable, or property?[D.3.1](../unit0/syllabus.md#D31){: .syl}

   <details markdown="1"><summary>Click to expand answer</summary>
   A variable that is associated with a specific object, accessed with the `.` operator.
   </details>

2. What is a method?[D.3.2](../unit0/syllabus.md#D32){: .syl}
   
   <details markdown="1"><summary>Click to expand answer</summary>
   A FUNCTION that is associated with a specific object, accessed with the `.` operator.
   </details>
   
3. What is a constructor method?[D.3.2](../unit0/syllabus.md#D32){: .syl}
   
   <details markdown="1"><summary>Click to expand answer</summary>
   A special method that is used to make a new *instance* of an object when you use the new command.
   </details>
   
4. If I have an object called named `ball`, how would I access its `color` property, if it has one?
   
   <details markdown="1"><summary>Click to expand answer</summary>
   ```ts
   ball.color
   ```
   </details>

5. If I have an object named `ball`, how would I call its `changeColor` method if it has one?
   
   <details markdown="1"><summary>Click to expand answer</summary>
   ```ts
   ball.changeColor("red");
   ```
   </details>

6. If I have a class named `Ball`, how can I create a new instance of that class named `ball1` (assume I don't need any arguments in the constructor)
   
   <details markdown="1"><summary>Click to expand answer</summary>
   ```ts
   ball1 = new Ball();
   ```
   </details>

7. Create a class for `Cookie` objects with three instance variables: `flavor` is a string, `size` is a number, and `temperature` is also a number. Include a constructor function to make a new `Cookie`.
   
   <details markdown="1"><summary>Click to expand answer</summary>
   ```ts
   class Cookie {
      flavor:string;
      size:number;
      temperature:number;

      constructor(flavor:string, size:number, temp:number) {
        this.flavor = flavor;
        this.size = size;
        this.temperature = temp;
       }
   }
   ```
   </details>

## Flash Cards
* object
* property / instance variable
* method
* constructor
* dot operator
* class
* instance
* new (command)