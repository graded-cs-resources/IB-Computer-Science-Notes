# P5.js - A Javascript / TypeScript Drawing Library
 
For our next several assignments, we will use the p5js library. This is a set of functions that make it very easy to draw and animate shapes on a web site using javascript / TypeScript, which will help us learn programming techniques in a visual way. This will serve as a short introduction to the library.

## The setup

I will be providing fully setup assignments for you. All you need to know, really, is that every p5 program contains two functions:

* The `setup()` function runs when the program first starts. Use it to build your drawing canvas and initialize any variables or settings.
* The `draw()` function then runs OVER AND OVER AND OVER again, in a loop, approximately 60 times per second (unless your computer is being slow today). This is used to animate and make games, etc.

## Drawing with p5
Take a look at the very simple code example below (click `Run Pen` to load it)

<p class="codepen" data-height="265" data-theme-id="light" data-default-tab="js,result" data-user="DavidGriswoldTeacher" data-slug-hash="ExYvPOO" data-preview="true" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="ExYvPOO">
  <span>See the Pen <a href="https://codepen.io/DavidGriswoldTeacher/pen/ExYvPOO/">
  ExYvPOO</a> by David Griswold (<a href="https://codepen.io/DavidGriswoldTeacher">@DavidGriswoldTeacher</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

The comments should make it clear what is happening. When you move your mouse over the drawing area at the right, it draws a circle (a.k.a an ellipse with the same width and height).

- [ ] Click the "Edit on CodePen" button in the upper right to open the code in a separate tab (put it in a separate window or desktop if you want). You can ignore (or minimize) the HTML and CSS sections.
- [ ] In the JS section, change the word `ellipse` to the word `rect`. You can't save without making an account (unnecessary, we don't need to save this after this exploration) but after a second the bottom should reload. Test out your code now: what changes?
- [ ] Add a line before the `rect` command that says `fill("pink");`. What changes?
- [ ] Add a line before the `fill` command that says `stroke("green");`. What changes?
- [ ] Change `rect` back to `ellipse` and change ONE of the two 30s to a larger number like 60. What changes?
- [ ] At the top of the `draw` function, make a new number variable called `w`. Set its initial value to `random(20,100)`. This will pick a random number between 20 and 100 (note this is a p5 function, not a built in TypeScript one). In the ellipse function, change the first of the two numbers to `w`. What changes?
- [ ] Look back at the code I used to make a random background color in setup. Copy that code and replace the `fill` color with that code. What changes?
- [ ] Surround the `draw` function with an `if` statement in the form `if (mouseIsPressed) {...}`. What changes?

As this very simple demo should make clear, p5js adds a lot of features to TypeScript that make it easy to do basic drawing and interaction. 

If there is something you think p5 should be able to do (draw a line? A triangle? detect a keyboard press?) you can proably learn about in the ![p5 documentation](https://p5js.org/reference/) - go there when playing with p5! The code examples there are in normal javascript, but modifying them for TypeScript is usually a very minor thing to do.