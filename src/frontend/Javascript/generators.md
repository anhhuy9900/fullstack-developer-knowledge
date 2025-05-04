ES6 Generators | Section Overview & Coding Break

Time for an optional coding break. Grab some coffee, a drink, or whatever you need to stay motivated to learn es6!

Let’s also take a moment to review the topics and concepts that appeared in this section:

- Generators break the typical “run to completion” model of normal functions and can start, pause, and reset.

- Generators use the syntax of a normal function, but have an asterisk following the function keyword: function* generator { … } .

- The generator yield keyword signals when to ‘pause’ the function and return its current state.

- Generator instances don’t use the new keyword like the typical function prototype or Object.

- Using the generator’s special next() method allows us to access its yielded state.

- Passing values to the next() method introduces a way for generators to reset, or complete their runtime.

An iterator in JavaScript demonstrates a type of object that can access values in a collection one at a time.

A generatorcan provide a convenient and complex alternative to iterators.

Overall, generators bring a lot of excitement to es6 because they introduce a lot of control in flow of functions. They seem strange to work with at first. But after a couple of examples - how to write generators, and why we need generator - both become a lot more clear. Generators will certainly help make your programs a lot more complex and capable of handling unique problems according to your design!

### example
To solve this exercise, you had to add three yields to the letterMaker generator. Simply one a time, yield ‘x’, ‘y’, and ‘z’ respectively.

function* letterMaker() {
  yield 'x';
  yield 'y';
  yield 'z';
}
let letterGen = letterMaker();
And boom! We have a working XYZ generator.