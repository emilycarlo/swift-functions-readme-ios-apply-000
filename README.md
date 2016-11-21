# Functions

![Conf](http://i.imgur.com/jvFW8gf.jpg?1)

> It does not matter how slowly you go as long as you do not stop. -[Confucius](https://en.wikipedia.org/wiki/Confucius)

## Overview

In this lesson we'll define, create, and call functions that take one and zero arguments. 

## Learning Objectives 

* Explain that a function is a **self-contained** chunk of code that performs a **specific** task
* Call functions using the function name
* Break down the various parts of a function
* Create functions that takes no arguments and functions that take one argument

## Functions

So far, all the code you have written has been a set of steps, such as declaring a variable or constant (using `var` or `let`) or printing variables to the console (using Swift's `print()` function). While this has allowed you to do some cool things, having to constantly retype what you want a program to do doesn't scale well to larger programs. Wouldn't it be nice if you could have a bit of common code in one place, and execute it every time you want to use it?

You've actually seen this in action when you called the `print()` function. Swift's `print()` function prints strings, variables, and constants to the console. It's one of Swift's built-in functions, and contains the nitty-gritty of console output in one place. You don't have to worry about how _exactly_ you print things to the console; when you want to print something, you just call `print()` and it happens! `print()` is really just a bit of code that you can call many times without worrying about the details.

You may be happy to know that you can write your own functions in Swift, too! Let's take a look at how that is done. But first, let's talk about puppies and kittens.

![Puppy! Kitten!](http://i.imgur.com/85Pd59R.gif)

Imagine for a second that you're a dog. Being a dog means you can do a few pretty cool things: You can bark, and you can eat. (Assume that you're a really smart dog who can read and speak English, too.) Those abilities are a common function that you probably do several times a day.

You probably greet lots of people with a bark on a daily basis: Your owner, the mailman, people walking by on the sidewalk, and cats running into your front yard. You don't have to write out explicit instructions for everyone you bark at every day. It'd be much easier to store that code in one place and just call it every time you need to bark. So let's put that into a common place: A _function_!

## Declaring Functions

Here's what a simple `sayHello()` function looks like in Swift:

```swift
func sayHello() {
    let greeting = "Hello there!"
    print(greeting)
}
```

Let's break this down bit-by-bit (no pun intended).

First of all, remember how you declared variables and constants using the keywords `var` and `let`? When you create a function, you have to declare it, as well. Functions in Swift are declared using the `func` keyword. (`func` is short for _function_ and functions are both fun and fancy, which is why we use `func` to introduce them.)

After the `func` keyword, you type the _name_ of the function, just like a variable or constant. You'll use this name later on to _call_ the function (you'll see an example of this in action soon). The name can be anything you want—just like a variable! Normally, functions in Swift are named in _camel case_, which that it starts with a lowercase letter, and each word in the function's name is capitalized, like you see in `sayHello`. (Swift's function names cannot contain spaces.)

After the name of the function, you type a set of parentheses: `()`. For now, that set of parentheses will be empty. You'll soon see why you type those parentheses, but for now, don't worry about them.

After the parentheses comes a set of curly braces: `{}`. The first one, `{`, opens up a _code block_. This code block is also referred to as the function's _body_. Inside this code block is where you write what you want your function to do. You end the function with a matching curly brace: `}`. This lets Swift know that your function definition is done.

Inside those curly braces is where the magic happens. You write exactly what you want your new function to do. It's pretty much what you've been doing in the past lessons, but now it's inside a function. In `sayHello()`, the only thing you do is declare a constant string called `greeting`, then print that string to the console by calling the `print()` function.

## Calling Functions

When you _call_ a function, your program jumps to that function that executes the bit of code inside the function's body (denoted by the curly braces). You usually call a function outside of the function definition itself. A function is called simply by writing the name of the function followed by parentheses. Try entering this in a new playground file:

```swift
func sayHello() {
    let greeting = "Hello there!"
    print(greeting)
}

sayHello()
// prints "Hello there!"

sayHello()
// prints "Hello there!"
```

What's happening here? First you _defined_ the function `sayHello()`, and then you call it twice, on the last two lines of the code above. You should see "Hello there!" printed twice to your playground file's console (don't forget to pop that open by hitting the arrow button at the bottom of the playground!).

Does calling a function look familiar? You've been doing that when you write `print("string")` all along!

Notice that once you've defined a function, you can call it as often as you want, and each time the same bit of code will be executed. You could call `sayHello()` five times...fifty times...even a thousand times! Go ahead and try it! (But don't do it a thousand times, because that'll take a long time to type, and there's still quite a bit more of this lesson. You can if you really want to, though—nothing is stopping you!)

## Scopes

Now is a good time to segue very quickly into _scopes_. Every function has its own scope, which means that constants and variables defined in that function are only usable _within_ that function. In `sayHello()`, you declared a constant called `greeting`. `greeting` can _only_ be used within the body of `sayHello()`. You can't use it outside of the function.

Don't believe me? Add this line to the end of your playground file:

```swift
print(greeting)
```

You should get an error when you try to run your playground!

Here's a more detailed example of scoping:

```swift
func sayGoodbye() {
    let farewell = "Goodbye, world."
    print(farewell)
}

sayGoodbye()
// Prints "Goodbye, world."

print(farewell)
// This will print an error and won't compile. Your playground
// file will not run at all!
```

In a nutshell, _scoping_ refers to the _visibility_ of variables and constants; that is, what parts of your program can see or use the variables or constants you declare. It is very useful to limit a variable's scope to a single function. Changes to a variable inside of a function you write won't affect other parts of your program in unexpected and unintended ways. In our case, we can be certain that since we declared `greeting` within the scope of our function, no one outside of that function can mess with it.

## Function Arguments

Now that you've learned how to declare functions, let's return to your doggie alter ego again. You're a dog, so your owner takes you for a walk every day. During the walk, you always see a lot of cats, which you've gotten to know over the course of many walks. You've always wondered why cats sleep so much, instead of fetching balls and chewing on shoes, which is a lot more fun. You wonder why your feline friends sleep so much.

You could write functions to ask them why they sleep so much. Those functions would look something like this:

```swift
func sayHelloToGarfield() {
    print("Hello, Garfield, why do you sleep so much?")
}

func sayHelloToBuster() {
    print("Hello, Buster, why do you sleep so much?")
}

func sayHelloToScratchy() {
    print("Hello, Scratchy, why do you sleep so much?")
}
```

Add those to your playground file. You probably noticed as you typed those in that they're pretty repetitive. What do they all have in common?

Save for the name of your cat friend, they all have the same format: printing the string "Hello &lt;cat friend&gt;, why do you sleep so much?" Doesn't that defeat the purpose of having code in a function so you only have to type it once?

Luckily, you can generalize functions using _arguments_. You've already seen arguments in action: You've passed different strings to the `print()` function to print different things. There is nothing special about Swift's `print()` function; your own functions, too, can take arguments, which will slightly change how they work. Let's take a look at that.

Remember when you created `sayHello()`, and you added an empty set of parentheses after the function name? You can specify an argument in those parentheses instead. That argument consists of both a name and the argument's data type (you remember learning about data types, right?). You can then pass in a different value in place of that argument when you call the function. Inside the function's body, you can refer to that value using the name in the argument list.

```swift
func sayHello(name: String) {
    print("Hello \(name), why do you sleep so much?")
}
```

Enter the above code into your playground file. (Don't just copy and paste it in! Typing it in yourself helps you to familiarize more closely with the code.) Take a look at what you did: You defined a function (using the `func` keyword) called `sayHello(name:)`. Like `sayHello()` above, you opened with a set of parentheses. But instead of being empty, you declared an argument called `name` of type `String`. Then, you wrote a function body consisting of a call to `print()`. Notice that the string you are printing interpolates the argument, `name`. `name` is a constant that you can use anywhere inside the `sayHello(name:)` function. You can think of it as being a constant declared inside of the function body, just like `greeting` was declared inside of `sayHello()`. Like `greeting`, `name` is visible only within the _scope_ of `sayHello(name:)`, so you cannot refer to it outside of the function.

You can call `sayHello(name:)` just like you called `sayHello()`, except you have to pass an argument to `sayHello(name:)`. You can simply pass a string because the function's argument, `name`, is of type `String`:

```swift
sayHello(name: "Mittens")
// Prints "Hello Mittens, why do you sleep so much?"
```

You can also declare a constant or variable, then pass the constant or variable to `sayHello(name:)`.

```swift
let dumpsterCat = "Rocky"
sayHello(name: dumpsterCat)
// Prints "Hello Rocky, why do you sleep so much?"
```

(Remember: That constant or variable _must_ be a `String`, because you declared the argument to `sayHello(name:)` to be a `String`!)


`sayHello(name:)` _requires_ an argument, but if you call on this function and don't pass an argument to `sayHello(name:)`, it will result in an error. If a function requires an argument, you must pass one when calling the function!

While this is a Readme, this lesson's playground file contains several function declarations. To fork and clone from Github, first click on the little Github icon which is the first of four icons on the upper right side of your Learn screen. Then follow the workflow of forking and cloning the repository. Try various ways of calling those functions until you are comfortable with how they work.


---

<p class='util--hide'>View <a href='https://learn.co/lessons/swift-functions-readme'>Functions</a> on Learn.co and start learning to code for free.</p>


func sayHello () {
let greeting = "Hello there!"
print (greeting)
}

sayHello()

sayHello()

func sayGoodbye() {
let farewell = "Goodbye, world."
print(farewell)
}

sayGoodbye()

func sayHello(name: String) {
print("Hello \(name), why do you sleep so much?")
}

sayHello(name: "Mittens")

let dumpsterCat = "Rocky"
sayHello(name: dumpsterCat)


