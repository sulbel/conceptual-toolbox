# Java
Java is an **object oriented language**, that is platform independent.  The **JVM** acts as a translator between the Java code and machine code.

## Strings
* Comes from the (default) java.lang package
* In java, strings are **immutable**
  * Can be overwriten by using the `new` keyword
  * For example:
    ```
    String stringA = "Hello";
    String stringB = "Hello";
    ```

    * Both of these variables would point to the same object in memory

    ```
    String stringA = "Hello";
    String stringB = new String("Hello");
    ```
    * Now the 2 objects are in separate memory locations

* Some common string methods:
  ```
  stringA.length();
  stringA.toUpperCase();
  stringA.toLowerCase();
  stringA.indexOf('char');
  stringA.lastIndexOf('char');
  stringA.charAt(int);
  stringA.equals(stringB);
  stringA.equalsIgnoreCase(stringB);
  ```

## Classes
Template for objects
* Access Modifiers
  * Public - can be accessed/modified by any other class in the application, from any package
  * Private - only accessible from within the same class it is declared
* Best practice to use getter/setter methods to access/modify private variables

## Inheritance
Gives access to the variables and methods of one class to another.  Indicated by usage of the `extends` keyword, e.g. class Magazine extends Book

  * A class in Java can only extend one other class
  * A child class inherits public and protected items from its parent class, but these can be overridden, e.g. by declaring a method with the same name and parameters

## Polymorphism
An object is considered an instance of every class in its inheritance chain

## Keywords
* Static - defines class members; **shared across all instances**
* Final - declares something as immutable
  * Primitive cariables can't modify values
  * Reference variables can't switch references
  * Methods can't be overwritten
  * Classes can't be extended
* Abstract - incomplete, missing definition
  * Cannot be instantiated, **can only be extended**