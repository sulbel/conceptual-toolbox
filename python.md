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

 ## Modularity
 * Functions are defined with keyword `def` and end with a colon, e.g. `def square(x):`
   * The main function of a python program is `__main__`.  Place the main code like: `if __name__ == "__main__"`
* Command line arguments: `import sys` and accessed via `sys.argv[1]` for the first command line argument
* Shebang `#!/usr/bin/env python3` 
* Function default arguments are evaluated **once**, at program runtime
  * This can cause strange behavior when the default argument is a *mutable* type, like a list, e.g. repeatedly appending a value
  * A solution to this is to supply value `None` to the default, and check if the object `is None`, then create a new object to operate with/return
* To adjust a **global variable** within a function, use the `global` keyword, e.g. `global count = 5`
