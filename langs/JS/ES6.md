# ES6

## `let` and `var`
* An issue with `var` is that the variable can be declared again, overwriting the previous declaration without error
* Enter `let`: only let variables be declared **once**
  * When a variable is declared with `let` inside a block, statement, or expression, its scope is limited to that area
    * e.g. when using `let` in a for loop, the looping variable is not accessible outside the loop. When declared with `var`, it is

## `const`
* `const` has all the cool features that `let` has, in addition to being a **read-only, constant** variable
* Best practice to name `const` in all caps, with an underscore separating words i.e. `VARIABLE_NAME`
* Objects (including arrays and functions) assigned to `const` variables **are still mutable**
  * `const` only prevents reassignment of the variable identifier, e.g. can not reassign an entire new array to a `const myArray`, but can change the elements of the array
  * To prevent mutation, use `Object.freeze()`