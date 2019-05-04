# Installing our Text Editor / IDE

A *text editor* is a program whose primary purpose is editing files that consist only of words and numbers. Macs include the simple text editor TextEdit, and Windows computers include Notepad. For most computer programming, you could get away with just one of these text editors, plus the command line!

An *IDE*, or "integrated development environment," can edit text, just like a text editor, but it also comes with built-in tools to color-code the text (*syntax highlighting*), run programs, find problems in programs, and even help make graphical user interfaces. They tend to be much fancier and more complicated than text editors, but also more powerful. They are often designed for a specific programming language. We will use one of these, later in the course, called Netbeans for Java.

For now, we will install [Visual Studio Code](https://code.visualstudio.com) to write our software. This software is somewhere between a basic text editor and an IDE; it isn't as complex as some IDEs, but can do much more than Notepad. You can install it from the website (and probably the Mac store) but it is better to use our new package manager!

* Mac Users! Type
`brew cask install visual-studio-code` and press enter. 

* Windows Users! Type `choco install vscode` and press enter.

If all goes well, it should download and install the program for you. When it is installed, go ahead and open it - you should see something like this:

![Visual Studio Code Welcome Screen](media/01/img004_vscode_welcome.png)

On that screen, go ahead and click the two links in the upper right that say "Install support for Javascript" and "TypeScript". We will be using both of those soon, and getting the support installed is a great idea!