# JavaScript notes

## Strings
* In JS, strings are **immutable**
  * Can not change individual characters of a string, e.g. myString[0] = 'a';
  * *CAN* assign string a new value, e.g. myString = "new string value";


## Arrays
* Arrays are declared with square brackets `myArray = [];`
* Arrays can have mixed values `myArray = ["String", 15];`
* Array values are accessed with zero-based indices
* Unlike strings, arrays are *mutable*, i.e. we can change the value of data
* Append data to an array with the push() method
* Add data to beginning of array with unshift()
* Remove data from end of array with pop()
  * pop() returns the data removed; can assign to `var`
* Remove data from *beginning* of array with shift()


## Functions
* Functions are defined with keyword `function`
* If a variable is declared **without** keyword `var`, it behaves as a global variable
  * If a variable is declared outside of a function scope it also behaves as a global

## Comparisons
* In JS, the `==` comparator will *convert* data types to compare the same; e.g. the integer and string `7 == '7'` will evaluate to true
* To do a **strict comparison**, enforcing same data type, use the `===` comparator
* Logical and has keyword `&&`
* Logical or has keyword `||`

## Switch statements
* Switch statements are tested with **strict equality** (`===`)
* Keyword `break` is used to stop execution of the switch statement
* The `default` statement is executed if no cases match
