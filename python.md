# Python
Python is a dynamically typed, interpreted language

## Access Modifiers
Python classes have 3 flavors of access modifiers for classes: `public` `protected` and `private`.
* `public` by default, all data members and member functions of a class are public, and accessible from outside the class
* `protected` members are declared by prepending a single `_` and are only accessible to derived classes
* `private` members are declared by prepending a double `__` and are only accessible within the class they are declared

## Scalar Types
Int, float, None, bools
* Ints can be declared normally, i.e. x = 10, but also binary `0b10`, oct `0o10` or hex `0x10`
* Floats implemented as IEEE-754 double-precision with 53-bits binary precision (~15-16 decimal sig figs)
 * `None` represents null
 * Bool has values (note capitalized) `True` and `False`

 ## Collections
 * Strings - can be enclosed by either single or double quotes, but must remain consistent
   * Python strings are **immutable**
 * Lists - sequences of objects
   * Unlike strings, lists are **mutable**
   * Can be extended across multiple lines to improve readability
 * Dicts - key/value map declared with curly braces `{}`

 