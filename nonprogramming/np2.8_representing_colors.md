---
Title: Lesson 2.8 - Representing Colors
---

<style>
  .circle {
  width: 10rem;
  height: 10rem;
  border-radius: 50%;
  mix-blend-mode: screen;
  position: absolute;
}

#circle-red {
  background: #ff0000;
  left: 1rem;
  top: 1rem;
}

#circle-green {
  background: #00ff00;
  left: 4rem;
  top: 1rem;
}

#circle-blue {
  background: #0000ff;
  left: 2.5rem;
  top: 3.5rem;
}

.colorbackground {
  width: 15rem;
  height: 14.5rem;
  background-color: black;
  position: relative;
  border-radius:1rem;
}

.colorcontainer {
    display:flex;
    flex-wrap:wrap;
    margin:.5rem;
    padding: 1rem;
    border-radius: 1rem;
    box-shadow: .02rem .02rem .5rem #93a1a1;
}

.sliders {
    margin-right:2em;
    width: 12em;
}
.slider {
    width:100%;
}

</style>

<script type="text/javascript">
function update() {
    var red = parseInt(document.getElementById("red").value,10);
    var green = parseInt(document.getElementById("green").value,10);
    var blue = parseInt(document.getElementById("blue").value,10);
    document.getElementById("circle-red").style.backgroundColor="rgb(" + red + ", 0, 0)";
    document.getElementById("circle-green").style.backgroundColor="rgb(0, " + green + ", 0)";
    document.getElementById("circle-blue").style.backgroundColor="rgb(0,0, " + blue + ")";
    var textString = "#"
    if(red.toString(16).length < 2) textString += 0;
    textString += red.toString(16).toUpperCase();
    if(green.toString(16).length < 2) textString += 0;
    textString += green.toString(16).toUpperCase();
    if(blue.toString(16).length < 2) textString += 0;
    textString += blue.toString(16).toUpperCase();
    document.getElementById("hex").innerText = textString;
}
</script>

# Representing colors in computers

For many years, images and graphics have been some of the most important things represented by computers - think about how much of your daily interaction with computers is about pretty things on screens, pictures, or videos.

In its most basic form, a picture is just a very large collectin of dots (called pixels) that are each a particular color. Get enough dots and you can build a picture. Change the dots rapidly, you get video.

## Primary colors of Human Vision - <span style="color:red">RED</span>, <span style="color:green">GREEN</span>, <span style="color:blue">BLUE</span>

In art class you may have learned that primary colors are red, blue, and yellow. These primary colors apply to mixing together paint or markers or crayons. But computers don't use paint, they use LIGHT. And for humans, the primary colors of light are 
<span style="color:red">RED</span>, <span style="color:green">GREEN</span>, and <span style="color:blue">BLUE</span>. Why? It has to do with how your eyes work - you have three special types of structures in your eyes called CONES that detect red light, green light, and blue light primarily, and all other colors are detected by a mixture of these cones.

Computer monitors and TVs and other devices designed to show colors to human take advantage of the way our eyes work by actually only emitting those three colors in various amounts. Even though the sun outputs light at a particular wavelength we call "yellow", computers don't - instead, they output equal amounts of red light and green light, and our eyes INTERPRET that as yellow.

This means that to a computer, any color is simply defined by three numbers: how bright should the red glow, how bright should the green glow, and how bright should the blue glow?

You can play with this using the splotlight app below. 


<div class="colorcontainer">
    <div class="sliders">
        <p>
        <label style="color:red" for="red">Red</label><br>
        <input type="range" min="0" max="255" value="255" class="slider" id="red" oninput="update()"><br>
        <label style="color:green" for="green">Green</label><br>
        <input type="range" min="0" max="255" value="255" class="slider" id="green" oninput="update()"><br>
        <label style="color:blue" for="blue">Blue</label><br>
        <input type="range" min="0" max="255" value="255" class="slider" id="blue" oninput="update()">
        </p>
        <p>
        Center Hex: <strong id="hex">#FFFFFF</strong>
        </p>
    </div>
    <div class="colorbackground">
        <div class="circle" id="circle-red"></div>
        <div class="circle" id="circle-blue"></div>
        <div class="circle" id="circle-green"></div>
    </div>
</div>

## Storing a color value

Colors in a computer generally are represented with using one byte for the amount of red, one byte for the amount of green, and one byte for the amount of blue, in that order. This allows for $$256^3$$ total possible colors, about 16 million of them, certainly more than the human eye can differentiate.

We often represent a color using hexadecimal, as shown in the above applet. The values range from `00` (0) to `FF` (255), where `00` means none and `FF` means full brightness. The first two characters represent the red, then the green, then the blue. The hashtag in front of the value is a clue to the computer that hexadecimal is coming.

Sometimes you will see a fourth component of a color, called "alpha". This doesn't actually change the color itself, it changes the OPACITY, or transparency, which will effect how that object blends in with the background. When all four bytes are used, we call that "32-bit color". 