# Inheritance and Polymorphism

Recall that in [prior notes](01_Programming_with_objects.md) we discussed the idea of *objects* as collections of information and actions under a single connected name, and we also discussed the idea of *classes*, which work as blueprints from which we can create specific objects.

But what if you want to start with a blueprint, and use it to make a *different* blueprint?

![Note Inheritance Diagram](media/04/Note&#32;Inheritance.svg)
{: .image-right style="border:1px black solid; padding:5px;"}

The diagram at right demonstrates the idea of **inheritance**. The `Todo` class inherits from (or *extends*) the `Note` class. You can create new `Note`s or you can create new `Todo`s. We say that `Note` is a **superclass** and Todo is a **subclass**. If you make a `Todo`, it has several interesting properties:

* It inherits all of the instance variables and methods from `Note`.
  
* It counts as both a `Todo` and a `Note` - in the code shown, we have added it to an array of `Note` objects called `notes`, which is allowed!
  
* It is possible to rewrite the methods from `Note` inside `Todo` but keep the same name. We will see that `getContents()` actually works a bit differently in `Todo` objects than it does in `Note` objects.

Let's check out the actual code for these classes. There are several interesting things in this code, so please read it carefully!

## Example Code for Inheritance

```ts
class Note {
    // These private variables can only be accessed within this class. Even subclasses can't touch them!
    // Todo methods will need to edit these variable using accessors and mutators.
    private color:string;
    private contents:string;

    constructor(contents:string, color:string) {
        this.contents = contents;
        this.color = color;
    }
    // accessors and mutators
    public changeColor(c:string) { this.color = c; }
    public setContents(c:string) { this.contents = c;}
    public getContents() { return this.contents; }
    public getColor() { return this.color; }
}

// the keyword `extends` tells us that "a Todo IS a Note"
// this is the word for inheritance!
class Todo extends Note {
    private isCompleted:boolean;

    constructor(contents:string, color:string, complete:boolean = false) {
        // the super() command calls the constructor from the superclass, setting the
        // appropriate instance variables that were inherited fron Note.
        // You must ALWAYS call `super()` inside an inherited constructor.
        super(contents, color);
        this.isCompleted = complete;
    }

    public toggleComplete() {
        this.isCompleted = ! this.isCompleted;
    }

    // Look! This has the same name as the Note version of getContents, but works
    // a little differently. This is called polymorphism.
    // The use of `super.getContents()` is a special command that tells the function
    // to use the version of getContents from the `Note` class for that line.
    public getContents() {
        if (this.isCompleted) {
            return "[x] " + super.getContents();
        }else {
            return "[ ] " + super.getContents();
        }
    }
}

let notes:Note[] = [];
notes[0] = new Note("What's up?", "blue");
notes[1] = new Todo("Eat cookies", "orange");

let todo1:Todo = new Todo("Go to work", "purple");

console.log(notes[0].getContents()) ;
console.log(notes[1].getContents());
console.log(todo1.getContents());
notes[1].toggleComplete();
todo1.toggleComplete();
console.log(todo1.getContents());
```

### Questions about the code

Try to predict these answers these questions BEFORE reading on (the answers come later in these notes). It may take you some serious careful reading and thinking, but it will pay off!

1. One of the last five lines will cause an error. Can you figure out which one?

2. What do you think the three `console.log` lines will print out (if you first remove the line with an error)? Read the code carefully and try to figure it out!

## Polymorphism

**Polymorphism** means of using one symbol across multiple different types, so that the symbol can behave differently in different contexts. 

One example of polymorphism is *operator overloading*, where an operator behaves differently with different types. we have seen this with the `+` operator in Typescript. The same symbol adds two numbers together if you have two numbers, or concatenates if you have two strings or one string and one number. Different behaviors, same symbol - this is polymorphism!

More commonly, polymorphism in object-oriented programming means using the same name for a method on a subclass as the method on its superclass. In our example, the `getContents()` function will work differently for `Todo` objects than it will for `Note` objects, making it a polymorphic method. If an object is a `Todo`, it will always run the `Todo` version of the method, *even if Typescript didn't know it was a Todo when the code was written*.

You can see this on the last few lines of example code above.

```ts
console.log(notes[0].getContents()); // prints "What's up?"
console.log(notes[1].getContents()); // prints "[ ] Eat cookies"
console.log(todo1.getContents());    // prints "[ ] Go to work"
notes[1].toggleComplete();        // gives an error "toggleComplete() does not exist on type Note"
todo1.toggleComplete();           // runs fine
console.log(todo1.getContents()); //prints "[x] Go to work"
```

The fourth line gives an error, because Typescript doesn't know that `notes[1]` is a Todo object. Since `notes` was declared as an array of `Note` objects, Typescript doesn't know that the object has a `toggleComplete()` method (even though it does!)

The second line, however, is fine. `Note` objects and `Todo` objects BOTH have `getContents()` methods, and so there is no error here. When the code is actually RUN, however, the code that runs is the `Todo` version of `getContents()`, returning the line `[ ] Eat cookies`. This is what polymorphism is all about. It means we can make an array that contains all of our notes and not worry about which ones are `Todo`s and which ones aren't - the `getContents()` function will work, correctly, either way, since the method is associated with the specific *instance*.

## Advantages and Disdvantages of inheritance + polymorphism

### Advantages

* Less repeated code - the subclass can often reuse many of the methods of the superclass, saving typing and making it easy to change if need be. `Todo` didn't need to re-implement the accessors and mutators for example since they came from `Note`.
  
* Simplifies work from the outside. Outside code doesn't need to treat the superclasses and subclasses as totally separate things - most of the time, the outside code only cares that we have a bunch of `Note`s and doesn't need to keep `Notes` completely separate from `Todo`s. It only needs to worry about it when it's using a special `Todo` feature.
  
* Potentially makes code more *modular*, increasing reusability in some cases. If a certain project only needs Notes, not Todos, the Todo class can be removed from the project, saving memory, without affecting the Note class.

### Disadvantages

* In some cases it actually makes code *less* modular. Since the `Todo` class won't work without the `Note` class, you can't take the `Todo` class to another project without also taking the `Note` class.

* In a similar vein, it can make code harder to figure out, especially if there are multiple layers of inheritance. If `Square` inherits from `Rectangle` which itself inherits from `Quadrilateral` which itself inherits from `Polygon`, a call to `square.getPerimeter()` would use a `getPerimeter` method that might be found in any of four files. That can make it challenging to understand the code. 

* Using inheritance makes the decision of whether to make a property `private`, `protected`, or `public` significantly more complicated, often resulting in properties being made public just for ease. This causes issues with encapsulation, one of the other foundations of object oriented programming!

--- 

A good rule of thumb is that you shouldn't use inheritance unless the subclass is at least 75% the same as the superclass. If you need to add or overwrite more than two or three methods, or add more than one or two instance variables, it's probably a good idea to make separate classes. 

Most object-oriented languages provide other tools (such as abstract classes and interfaces) that allow you to get some of the advantages of inheritance and polymorphism without going "all in", but learning about those is beyond the scope of our class.

## Check your Understanding

1.  What keyword is used to make a class inherit from another class?
   
    ```
    extends
    ```
    {: .spoiler}

2.  Describe what the keyword `protected` does.

    > It makes a method or instance variable accessible from subclasses but not the outside world
    {: .spoiler}

3.  Imagine you have a `Ball` subclass that inherits from a `Circle` superclass. The `Ball` class has a `bounce()` method, but the `Circle` method does not. Both of them have a `draw()` method.

    1.  Which of the lines below would create an error? (there may be more than one):
        
        ```
        let b1:Ball;            // line 1
        let b2:Ball;            // line 2
        let c1:Circle;          // line 3
        let c2:Circle;          // line 4
        
        b1 = new Ball();        // line 5
        b2 = new Circle();      // line 6
        c1 = new Ball();        // line 7
        c2 = new Circle();      // line 8

        b1.draw();              // line 9
        b2.draw();              // line 10
        c1.draw();              // line 11
        c2.draw();              // line 12

        b1.bounce();            // line 13
        b2.bounce();            // line 14
        c1.bounce();            // line 15
        c2.bounce();            // line 16
        ```

        <div class="spoiler">
            <ul>
                <li>Line 6 would create an error because a Circle is not a Ball (but a Ball is a Circle so line 7 is ok)</li>
                <li>Lines 9-12 would all be fine since the draw() method exists everywhere.</li>
                <li>Lines 15-16 would both cause errors since bounce() only exists on Balls, and Typescript thinks c1 and c2 are circles (even though c1 is actually a Ball, TS doesn't know that!)</li>
            </ul>
        </div>

    2.  Imagine the `draw()` method for `Ball` object draws a filled in circle, but the `draw()` method for `Circle` objects only draws the border. What is it called when we duplicate a method name like this? And which of lines 9-12 will draw a filled in circle?
   
        > This is called **polymorphism**. Lines 9 and 11 will draw filled-in circles, since b1 and c1 are both ball; even though TypeScript only knows for sure that c1 is a Circle, the actual instances are balls and that's what matter when the method is run. Line 10 won't do anything because of the error on line 6. Line 12, which both **is** and **looks like** a circle, only the border will get drawn.
        {: .spoiler}

4. Describe some advantages and disadvantages of inheritance and polymorphism.

## Key Terms and phrases

* inheritance
* superclass
* subclass
* `extends`
* `super()`
* `super.methodname()`
* `protected`
* 


        
