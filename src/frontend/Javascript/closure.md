# Closures

### Description
Closures | Section Overview

You’ve made it to the end of a section and now arrived at a pit stop. So take this opportunity for a coding break! It’s completely optional and lets you keep the course going at a pace entirely up to you.

However, this also gives us the chance to review the major concepts that just came up.

Closures in JavaScript and ES6 refer to functions that remember their creation environment and can further reference that environment’s independent variables.

Lexical scoping refers to the JavaScript concept of programs keeping track of variable locations to understand in which scopes they can be accessed.

Function factories create functions based on returning inner functions that manipulate its own arguments and the arguments of the outer function.

Data encapsulation and private methods don’t exist natively in JavaScript but can be emulated with closures for data restriction and limited access.

Overall, closures will significantly improve your programs. Having closures can private methods allow you to remove non-essential expressions and methods from the global scope of your program. Furthermore, understanding closures will put you one step ahead of the game as a JavaScript programmer and software engineer. It’s a fundamental yet somewhat abstract concept. But it turns out to not feel so complex once you actually dive into some relevant examples.

Addition Factory (Closures) | Solution

James needed assistance building a factory function in es6 for adding numbers. He almost had it, but just needed to return an inner function with one parameter. That inner function then returns the result of adding the factory’s parameter, ‘x’, and its own parameter ‘y’.

Here is the expanded solution:

const addFactory = (x) => {
  return (y) => {
    return x + y;
  };
};
const add50 = addFactory(50);
const add30 = addFactory(30);

Note we can actually implement the addition factory on one line:

const addFactory = x => y => x + y; 
