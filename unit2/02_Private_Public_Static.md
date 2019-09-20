# More about classes - private, public, and static

Consider this Typescript class, which we might use in p5.

```ts
class Snowflake {
    private size:number;
    private x: number;
    private y: number;

    public color:p5.Color;

    /** Construct a new snowflake. Anything not given will be random */
    constructor(x:number = random(width), 
                y:number = random(height), 
                size:number = random(10,50), 
                color:p5.Color = Snowflake.randomColor()) {
        this.size = size;
        this.x = x;
        this.y = y;
        this.color = color;
    }

    /** draws a snowflake once. Call using Snowflake.draw(...).
        If no color parameter is provided, will leave color undefined
        and will not change the color on drawing
    */
    public static drawOne(x:number, y:number, size:number, color?:p5.color)) {
        if (color != undefined) stroke(color);
        //draw a snowflake here, not showing details
    }

    /** Draw one random snowflake. Call using Snowflake.drawRandom() */
    public static drawRandom(minSize:number = 10, maxSize:number= 30) {
        stroke(SnowFlake.randomColor());     
        SnowFlake.draw(random(width),random(height),random(minSize,maxSize));
    }

    /** draws this PARTICULAR snowflake. Call using *flakename*.draw() */
    public drawThis() {
        if (this.color != undefined) stroke(this.color);
        Snowflake.draw(this.x, this.y, this.size);
    }

    public moveDown(n:number) { 
        this.y = this.y + n;
    }

    /** Pick a random color. Not available outside the class. */
    private static randomColor() {
        return color(random(255),random(255),random(255));
    }
    
}
```

Let's break down some of the words we see here.

## public vs private properties and methods

Public properties and methods are available OUTSIDE the class itself, while private methods can only be called from other methods INSIDE the calss. Consider the following code, which we might use from setup or draw:

```ts
s = new Snowflake();
console.log(s.color); // prints out the color
console.log(s.x); // gives an error, x is a private property
s.drawThis(); // draws the snowflake
console.log(s.randomColor()); // gives an error, randomColor() is private
```

Private properties are an important of **encapsulation**:star:, one of the key ideas of object-oriented programming. Encapsulation is the idea that data should be bundled together by its purpose, and data should be hidden inside that bundle (or object) whenever possible. Encapsulation is a valuable tool in adding abstraction to your code.

## static vs. instance properties and methods

Properties and methods can also be defined as *static* or *instance* values. In the above code, we have only instance properties, but we have two static methods, marked with `static` and two instance methods that aren't. 

**static methods and properties**:star: are defined for the entire CLASS and make sense even if you don't have any specific instances of the object. They are essentially just normal functions that we stick in a class for organization reasons; they don't depend on the property values of the specific object. You call a static method by using the name of the entire CLASS (generally capitalized), followed by the dot operator, followed by the method name.

```ts
Snowflake.drawOne(20, 50, 50, color("blue"));
stroke(Snowflake.randomColor()); 
// this gives an error if used outside of the Snowflake class, because it is private,
// but works fine when used inside the class
```

is essentially the same as the `snowflake()` function we defined in an earlier exploration, just organized into the `Snowflake` class. You don't need to make a `new` snowflake to use the method.

**instance methods and properties**:star:, which are the default like `moveDown()` and `drawThis()`, assume you are working with a SPECIFIC snowflake; they use the `this` value inside, which doesn't make sense without an actual snowflake to refer to! To use those you would do something like:

```ts
let s = new Snowflake();
s.drawThis() // draws snowflake s
s.moveDown(10); // moves snowflake s down ten pixels
s.drawThis() // draws s again, now 10 lower!

s.drawOne(10,10,10) // also works; you can call static methods
                    // from instances, but it's weird
```

Whenever you are making a new property or method in an object, you have to think about whether it should be `static` or left as instance, and whether it should be `public` or `private`. In java, you have to declare `publi`c or `private` for EVERY VARIABLE. In typescript, `public` is the default unless specified. In both languages, instance is the default but `static` must be declared.
