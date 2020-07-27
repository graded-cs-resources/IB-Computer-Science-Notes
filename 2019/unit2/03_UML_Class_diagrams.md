# UML Class Diagrams

It is very common in paper 2 of the IB CS exam to be asked to create *UML diagrams* of object clases. In these notes, we will learn how to do that.

## A simple example - one class

<table style="margin-left:2em;vertical-align:top"><tbody style="width:100%"><tr style="width:100%">
<td markdown="1" style="vertical-align:top">

### Code
{: style="text-align:center"}

```ts
class Snowflake() {
    public speed:number = 1;
    public color:string = "white";

    private x:number;
    private y:number;
    private size:number;

    // pretend the constructor() is here

    public moveFlake() {
        this.y += this.speed;
    }
    public increaseSize(amount:number) {
        this.size += amount;
    }
   
    private offScreen():boolean {
        return (y < 0  || y > height);
    }
}
```
{: style="margin-left:0"}

</td>
<td markdown="1" style="vertical-align:top">

### Diagram
{: style="text-align:center"}

![snowflake UMl diagram](media/03/snowflake&#32;class&#32;diagram.svg){: style="margin:auto;display:block;width:15em"}
</td>
</tr></tbody></table>

The diagram contains four important parts:

1. The name of the class at the top
2. The instance variables and their types, listed Typescript-style
3. The methods, with parameters and return type if not void
4. The `+` and `-` signs tell whether each element is private (`-`) or public (`+`)

This diagram describes all of the important features of the class without taking up nearly as much space as the full code, and is easier to interpret. Note that the constructor is NOT included - since every class includes a constructor, that wouldn't provide any useful information.

## A more complicated example - multiple connected classes.

![Flight class diagram](media/03/flight&#32;class&#32;diagram&#32;example.svg){: style="width:100%"}

The image above shows three classes that are interconnected. Here are some things to notice:

1. In all three classes, all of the instance variables are private. In TypeScript, this is pretty common. In java, it is almost ALWAYS true - instance variables are private, and methods are provided to change them if need be. We will talk more about this later.
2. There are probably properties and methods that are not shown. It is not always required to show ALL of the instance variables and methods in large classes, just the most important ones to give an idea of how the class works.
3. The arrows connecting them show a relationship. Notice the text on each side of the arrow. It shows how many of the nearby objects you could expect to see in a relationship. `0..n` means "0 or more". So you expect 2 or more employees for each flight, but only one airplane for each flight. However, an airplane can be associated with many future flights, or as few as none (perhaps if it is under maintenance). The arrows do not show you how the relationship is IMPLEMENTED, only that the relationship exists.

## Check your Understanding
1. Create potential UML diagrams to represent a `Snowman` class and a `Circle` class. The `Snowman` object should contain AT LEAST multiple instance variables of type `Circle` (e.g. `head`, `body`, `buttons`), public method `draw()` and private methods to draw the head, body, and buttons.

2. Look back at the [Object Anatomy practice problems](../unit2/02a_object_anatomy_practice_problems.md) and make UML diagrams for every class in those problems.