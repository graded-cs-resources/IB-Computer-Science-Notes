# Access Modifiers - private, public, static, readonly, and const

Consider this Typescript class, which we might use in p5. You'll notice some new words
in front of the properties and methods.

```ts
class Snowflake {
  private size: number;
  private x: number;
  private y: number;

  public color: p5.Color;

  /** Construct a new snowflake. Anything not given will be random */
  constructor(x: number = random(width),
    y: number = random(height),
    size: number = random(10, 50),
    color: p5.Color = Snowflake.randomColor()) {
    this.size = size;
    this.x = x;
    this.y = y;
    this.color = color;
  }

  /** draws a snowflake once. Call using Snowflake.draw(...).
      If no color parameter is provided, will leave color undefined
      and will not change the color on drawing
  */
  public static drawOne(x: number, y: number, size: number, color?: p5.Color) {
    if (color != undefined) stroke(color);
    /* implementation not included  for space */
  }

  /** draws this PARTICULAR snowflake. Call using *flakename*.drawThis() */
  public drawThis() {
    if (this.color != undefined) stroke(this.color);
    Snowflake.drawOne(this.x, this.y, this.size);
  }

  public moveDown(n: number) {
    this.y = this.y + n;
  }

  /** Pick a random color. Not available outside the class. */
  private static randomColor() {
    return color(random(255), random(255), random(255));
  }

}
```

Let's break down some of the words we see here.

## public vs private properties and methods

Public properties and methods are available OUTSIDE the class itself, while private methods can only be called from other methods INSIDE the class.[D.3.3](../unit0/syllabus.md#D33){: .syl} Consider the following code, which we might use from setup or draw:

```ts
s = new Snowflake();
console.log(s.color); // prints out the color
console.log(s.x); // ERROR, x is a private property
s.drawThis(); // draws the snowflake
console.log(s.randomColor()); // ERROR randomColor() is private
```

Private properties are an important of **encapsulation**:star:[D.2.1](../unit0/syllabus.md#D21){: .syl}, one of the key ideas of object-oriented programming. Encapsulation is the idea that data should be bundled together by its purpose, and data should be hidden inside that bundle (or object) whenever possible. Encapsulation is a valuable tool in adding abstraction to your code, as well as reducing the connections between code, reducing side-effects.[D.2.4](../unit0/syllabus.md#D24){: .syl}

## static vs. instance properties and methods

Properties and methods can also be defined as *static* or *instance* values. In the above code, we have only instance properties, but we have one static method, marked with `static`, and two instance methods that aren't marked with that word.

### Static methods and properties

**Static methods and properties**:star:[D.3.3](../unit0/syllabus.md#D33){: .syl} are defined for the entire CLASS and can be used even if you don't have any specific instances of the object. They are essentially just normal functions that we stick in a class for organization reasons; they don't depend on the property values of the specific object. You call a static method by using the name of the entire CLASS (generally capitalized), followed by the dot operator, followed by the method name.

```ts
Snowflake.drawOne(20, 50, 50, color("blue"));
stroke(Snowflake.randomColor()); 
// the second line would give an error if used outside the class since randomColor() is private
// but would work just fine if used inside the class, as it is in the constructor.
```

In this case, `Snowflake.drawOne()` is essentially the same as the `snowflake()` function we defined in an earlier activity, just stored inside the Snowflake class to make it easier to find it.

#### Static vs const / readonly / final

These four keywords are often confused, but they do very different things! It is important to keep them straight.

* `static` is used ONLY in classes, to declare properties or methods that are associated with the object type but don't belong to any particular instance. However, they can still be changed! The change simply applies to the static property.

  ```ts 
  class Bob {
      static a:number = 3;
  }

  Bob.a = 4;
  console.log(Bob.a) // 4 prints out
  b = new Bob();
  console.log(b.a) // error, a is static
  ```

* `const` (typescript) is used to declare VARIABLES (not object properties!) that should not be reassigned to a new value. 

  ```ts
  const a = 3;
  a = 4; //error, cannot change constants
  ```

* `readonly` (typescript) and `final` (java) are used to declare object properties that should not be reassigned to a new value. These words can be used with static or instance variables within a class.

  ```ts
  class Bob {
      readonly a:number = 3;
  }

  Bob.a = 4; // error, Bob.a does not exist, a is an instance property
  let b = new Bob();
  b.a = 4; // error, a is read-only, cannot be edited.
  ```

### Instance methods and properties

**Instance methods and properties**:star:[D.3.3](../unit0/syllabus.md#D33){: .syl} are the most common type of element in a class. In our example, they include `x`,,`color`, `moveDown()` and `drawThis()`. These assume you are working with a SPECIFIC snowflake. The methods, like `moveDown()`, will use the keyword `this` to refer to the specific object they are being called from.

```ts
let s = new Snowflake(); //uses constructor to make a random flake
let s2 = new Snowflake();
s.drawThis() // draws snowflake s
s.moveDown(10); // moves snowflake s down ten pixes
s.drawThis() // draws snowflake s again, now 10 pixels lower
s2.drawThis(); // draws snowflake s2

s.drawOne(10,10,10) // doesn't work! drawOne is static, so needs to be called like
                    // Snowflake.drawOne() . You will get an error.
```

Whenever you are making a new property or method in an object, you have to think about whether it should be `static` or left as instance, and whether it should be `public` or `private`. In java, you have to declare `public` or `private` for EVERY VARIABLE. In typescript, `public` is the default unless specified. In both languages, instance is the default but `static` must be declared.


## Check your Understanding

1. In the `Snowflake` class defined above, what does it mean that `randomColor()` is private and static?
   
   > Since it is private, you can only call the function within the class.  
   > Since it is static, you call it from the class name, like Snowflake.randomColor()
   {: .spoiler}

2. Write code for a class `Dog` with three string properties: `species`, `furColor`, and `name`. `name` should be available and changeable outside the class (we can change a dog's name!) but `furColor` should only be available internally since it can't be changed. `species` should be shared among all instances of the Dog class (give it the value `"Canis familiaris"`) and also declared as a `const` so it can't be edited. Do not include any methods (not even a constructor for now).
   
   ```ts
   class Dog {
       private static const species = "Canis familiaris";
       public name:string;
       private furColor:string;
   }
   ```
   {: .spoiler}

3. Several lines of code in Typescript are shown below. Identify where errors would occur and explain each error.
      
   ```ts
      const NUM_COOKIES=7;
      
      class Cookie {
          const SHAPE:string = "circle";
          private flavor:string = "chocolate chip";
          temperature:number = 35;
          
          constructor(flav:string,temp:number) {
              this.temperature = temp;
              this.flavor = flav;
          }
      }

      Cookie.SHAPE = "obloid";
      console.log(COOKIE.SHAPE);
      NUM_COOKIES = 5;
      let c = new Cookie("oatmeal",40);
      console.log(c.flavor);
      console.log(c.temperature);
   ```
   
   ```ts
      const NUM_COOKIES=7;
      
      class Cookie {
          const SHAPE:string = "circle";
          // ERROR. cannot use `const` in an object, need `readonly` or `static` depending
          private flavor:string = "chocolate chip";
          temperature:number = 35;
          
          constructor(flav:string,temp:string) {
              this.temperature = temp;
              // ERROR. type mismatch. temp is a string, this.temperature is a number.
              this.flavor = flav;
          }
      }

      Cookie.SHAPE = "obloid";
      // ERROR. SHAPE does not exist on Cookie unless you add the static keyword.
      NUM_COOKIES = 5;
      // ERROR. cannot edit the value of constants.
      let c = new Cookie("oatmeal",40);
      console.log(c.flavor);
      // ERROR. flavor is a private property and cannot be accessed outside the class.
      console.log(c.temperature);
   ```
   {: .spoiler}
      

