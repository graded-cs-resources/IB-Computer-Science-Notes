# Introduction to Objects and Classes

Imagine you are writing a simple note-keeping app. You want to be able to use the app to create notes with different content and background colors.

One way to approach this would be using *arrays*, as shown below:

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

An object is simply a collection of **properties**:star: (basically variables) and **methods**:star: (basically functions) that are collected under one name. 

In TypeScript you can make SINGLE objects like this:

```ts
let note1 = {
    // the first two values are properties of the object
    contents: "This is my first note",
    color: "red",
    // this value is a method
    change_color: function(color:string) {
        this.color = color; // `this` is a keyword that means the current object itself.
    }
}
// We access the properties and methods of an object using the dot . operator
console.log(note1.color) // "red"
console.log(note1.contents) // "This is my first note",
note1.change_color("green");
console.log(note1.color) // "green"
```

This helps us group information about `note1` together, but it doesn't really help us make new notes or take advantage of the fact that all notes have the same properties. So for that, let's add a new idea: *classes*.

## Classes

A **`class`**:star: is essentially a DESCRIPTION of an object. It describes what types of information we will hold about the object, what types of methods will be done to or by the object, and how to create a new **`instance`**:star:, or specific case, of the object. Let's look at code.

```ts
class Note { //classes are, by convention, capitalized
    // These are *properties*. They are not declared with a `let`.
    // They are instead declared as *private* (only accessible inside the class)
    // or they are delcared as *public* (accessible outside the class)
    public contents = string;
    public color = string;

    // Below we have the methods. They are ALSO declared using `public` or `private`.
    
    // This special method, called a CONSTRUCTOR, is a special one that is used
    // whenever we create a new Note. The `="yellow"` part is called a default
    // value, so that if somebody doesn't set the color it is automatically yellow.
    public constructor(in_contents:string, in_color="yellow") {
        this.contents = in_contents;
        this.color = in_color; 
    }
    // the method below does what it sounds like - it changes the color!
    public change_color(color:string) {
        this.color = color;
    }
}

// we use the "new" command to call the constructor and get a new note
// every time the "new" command is called it creates a new object then runs the 
// constructor method on the object.
let note1:Note = new Note("This is my first note", "red");
let note2:Note = new Note("This is my second note","blue");
let note3:Note = new Note("This is my third note. It is yellow by default!");
```

You now have three new notes! The diagram below provides a visual of what we've got.

![class diagram](media/01/Class&#32;Instance&#32;diagram.png)

You could still use arrays to help you keep track of an unknown number of notes, but now you only need ONE array - an array of Note objects - instead of multiple arrays.

```ts
let notes:Note[];
// the "push" method used below adds a new item to the end of an array in TypeScript
// in java, you would need to use an ArrayList or LinkedList 
// and the .add() method to do this.
notes.push(new Note("first note!"));
notes.push(new Note("second note!","green"));
notes.push(new Note("third note","purple"));
notes.push(new Note("oh my god how many notes????","orange"));
```

## Check your Understanding

1. What is an object property?
   
   ```
   A variable that is associated with a specific object, accessed with the `.` operator.
   ```
   {: .spoiler}

2. What is an object method?
   
   ```
   A FUNCTION that is associated with a specific object, accessed with the `.` operator.
   ```
   {: .spoiler}
   
3. What is a constructor method?
   
   ```
   A special method that is used to make a new *instance* of an object when you use the new command.
   ```
   {: .spoiler}
   
4. If I have an object called named `ball`, how would I access its `color` property, if it has one?
   
   ```
   ball.color
   ```
   {: .spoiler}

5. If I have an object named `ball`, how would I call its `changeColor` method if it has one?
   
   ```
   ball.changeColor("red");
   ```
   {: .spoiler}

6. If I have a class named `Ball`, how can I create a new instance of that class named `ball1` (assume I don't need any arguments in the constructor)
   
   ```
   ball1 = new Ball();
   ```
   {: .spoiler}

7. Create a class for `Cookie` objects with three properties: `flavor` is a string, `size` is a number, and `temperature` is also a number. Include a constructor function to make a new `Cookie`.
   
   ```ts
   class Cookie {
       public flavor:string;
       public size: number;
       public temperature: number;

       constructor(flavor:string, size:number, temp: number) {
           this.flavor = flavor;
           this.size = size;
           this.temperature = temp;
       }
   }
   ```
   {: .spoiler}

## Flash Cards
* object
* property
* method
* constructor
* dot operator
* class
* instance
* new (command)