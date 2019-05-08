# Typescript and Javascript tools

*Javascript* is a programming language that primarily runs inside of web browsers. It started life in the 1990s as a very simple language with just a few features, but over time it has grown with the web. It is now one of the most popular programming languages around, and is used for desktop applications as well as web browsers - in fact, Visual Studio Code and Github Desktop were both written using javascript technology!

*TypeScript* is an extension of javascript that gives it some programming features not available in javascript itself. We will be using Typescript in this course because it is a better fit for the IB curriculum than javascript itself.

Though it is possible to write code in javascript with nothing but a text editor and a web browser, for typescript we need a few other tools. Let's install them now!

## Install npm (nodejs)

`npm` is a package manager (like homebrew/chocolatey) that is designed specifically for javascript programmers. Let's install that first. It comes as part of a larger project called `nodejs` which will allow us to run javascript code without a browser.

```bash
# mac
brew install nodejs

# windows
choco install nodejs
refreshenv
```

If all went well, you should now be able to run...
```bash
npm install -g typescript

refreshenv # windows only
```

If THAT goes well, when you type `tsc -v` it should print something like `Version 3.4.4`. You're ready to typescript!