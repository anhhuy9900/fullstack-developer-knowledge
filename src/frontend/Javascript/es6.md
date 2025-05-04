Section Overview/Coding Break: Methods and Modules

You made it to the end of the ES6 essentials overview! Woohoo! Now we can move on to some new material in ES6. Before you race onward, here you have a pitstop for an optional coding break. We’ll briefly review the vital topics that came up in this section. But you can use this time to grab coffee or whatever you need to keep learning :)

Let replaces var in es6 in term of variable assignment. Let also allows for block scoping, in contrast to var.

Const declares variables that cannot be re-assigned. Constants also allow for block scoping along with ‘let.’

Template literals, created by a pair of back-ticks, allow for embedded-expressions using the dollar-sign and a pair of curly braces: `${...}`

Local scope refers to the set of statements, variables, objects, and more that confine to a coding block denoted by a pair of curly braces: { ... }

Global scope refers to the set of statements, variables, objects, methods, and more that exist outside and beyond all local scope functions and coding blocks.

The spread operator spreads individual values to allow for expansion with multiple arguments and elements. Denoted by three periods: ...

Rest parameters allow for the gathering of multiple parameter calls into one array: Denoted by three periods: …

Destructuring assignment on arrays allows for much more efficient array manipulation and assigns multiple variables from array data based on the index value.

Destructuring assignment on objects allows for more concise object manipulation and assigns multiple variables from object data based on keynames.

ES6 introduces the arrow function and a whole lot of helper methods to simplify manipulating arrays, objects, strings, and numbers.

The arrow function works just like a normal function expression, but with reduced syntax: ( ) => { … }

By default, arrow functions are anonymous because we declare them with an operator rather than the ‘function’ keyword.

The map helper method creates arrays by calling functions on each individual element of an initial array.

The filter helper method creates arrays based on the same elements of an original array depending on a certain test.

String.repeat() creates large strings by concatenating a string a certain number of times.

The search methods for strings include .startsWith, .endsWith, .includes, and more.

Number type checking can occur through the Number.isFinite method.

Number safety checking can occur through the Number.isSafeInteger method.

Modules refer to reusable pieces of code within an application. Most often, they exist independently within separate files, which come in handy when having to split up a large application.

The export keyword sends primitive values, objects, or functions from one module to another.

The import keyword receives primitive values, objects, or functions from another module.

Using the default keyword gives a module a fallback function when exporting multiple values and methods.

