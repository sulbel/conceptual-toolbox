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


