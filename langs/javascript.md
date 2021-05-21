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
