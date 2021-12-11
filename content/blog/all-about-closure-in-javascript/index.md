---
id: 918821
title: All about closure in javascript
published_at: 2021-12-06T17:19:37.776Z
tag_list: javascript,webdev,beginners,functional
---

Hello all 👋🏻,

This article is all about closure in javascript.

Closure is not a easy topic. It will be confusing topic for beginners. In this article i will try to explain it easily.

### What is a closure

According to MDN

> A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment). In other words, a closure gives you access to an outer function’s scope from an inner function. In JavaScript, closures are created every time a function is created, at function creation time.

According to Stackoverflow

> A closure is a persistent scope which holds on to local variables even after the code execution has moved out of that block. Languages which support closure (such as JavaScript, Swift, and Ruby) will allow you to keep a reference to a scope (including its parent scopes), even after the block in which those variables were declared has finished executing, provided you keep a reference to that block or function somewhere.

It might confusing you again. Let's jump to javascript lexical scoping in a high level not in detail because lexical scoping is a huge concept i will try to publish article on it separately.

```javascript
var title = "Devto"
function printTitle() {
  console.log(title)
}
printTitle() // Devto
```

The above snippet will print `Devto` in console. `title` variable is accessible in printTitle method because `title` variable is in `printTitle` parent scope. So if `title` and `printTitle` both are in single scope here i.e `global scope`

Consider the following snippet

```javascript
function main() {
  var title = "Devto"
  function printTitle() {
    console.log(title)
  }
  printTitle()
}
main() // Devto
```

The above snippet will print `Devto` in console but in this `title` and `printTitle` are not in `global scope` instead they are in `main method scope`.

Now checkout this example

```javascript
var title = "Devto"
function main() {
  function printTitle() {
    console.log(title)
  }
  printTitle()
}
main() // Devto
```

Same output but here the difference is `title` is in `global scope` and we are accessing it in `printTitle` method. So here the point is child's can access their parent / global level scope items. This is not only in javascript you can see this feature in other languages like `Java`, `C#`, `C++` and `Python` etc..

We will the change above snippet

```javascript
var title = "Devto"
function main() {
  return function printTitle() {
    console.log(title)
  }
}
const printTitleGlobal = main()
printTitleGlobal() // Devto
```

In javascript functions are `First class objects` means they are like variables. We can return any type of variable in a function so here we can return function itself because as i said it is also treated as a variable.

In the above snippet `main` method returning `printTitle` method and we are assigned it to `printTitleGlobal` variable and called that `printTitleGlobal` function. Indirectly we are calling `printTitle` function as `title` in global scope it is accessible in `printTitle` method so worked as expected.

Now Check the following snippet

```javascript
function main() {
  var title = "Devto"
  return function printTitle() {
    console.log(title)
  }
}
const printTitleGlobal = main()
printTitleGlobal()
```

Can you guess the output ?
It is same but here the craziest thing is `title` is in `main` method's scope but we are executing `printTitleGlobal` function in `global` scope . As per javascript lexical scope concept once the function is executed completely JS will clear the memory allotted for that. Here once `main` method is called it should clear all the references related to `main` method so JS should clear `title`, `printTitle` and `main`. As we stored `printTitle` in `printTitleGlobal` we can call that method anytime but that method has `main` method references which should be cleared after execution of `main`.

Then how it is printing "Devto" ❓.

That is what **closure** is ❗️

When ever we return any function in javascript. JS will not only return that method before returning it will find all the references required to that returned function it will pack all the references along with along with that function. We will call that pack as **closure**.

> A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment).

Now the above definition will make sense once we call `main` method it will give us a closure named `main` that closure will hold all the references required for `printTitle` and `main` method scope will get cleared after execution but still some of references required for `printTitle` are persistent in closure.

Checkout this screenshots:
I have added two `debuggers` this is the screenshot taken at the time of first debugger which is in `main` method. Look at the `call stack` in the left side window and `scope` in right side. `title` is in `local` scope. This is as expected.
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/fbck5wlpvhrmiij8rk1a.png)

Now time for second debugger which is inside `printTitle` method. `main` got cleared from `call stack` and in right side you can see `Closure (main)` it has `title` reference. This is the one holding reference of `title` which is being used in `printTitle`.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/bn03quhdgj2vg5fjroxk.png)

Hope you enjoyed it.
Cheers!

You can now extend your support by buying me a Coffee.

<a href="https://www.buymeacoffee.com/sakethk" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-blue.png" alt="Buy Me A Coffee" style="height: 30px !important;width: 60px !important;" ></a>
