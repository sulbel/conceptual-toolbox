# What is OOP?

Object-oriented programming combines a group of variables (properties) and functions (methods) into a unit called an "object." These objects are organized into classes where individual objects can be grouped together. OOP can help you consider objects in a program's code and the different actions that could happen in relation to the objects.



# Main Concepts

## Encapsulation
* Encapsulation is a way to bundle data with the methods that interact with the data
  * Gives rise to `getter` and `setter` methods
* Data inside an object should only be accessible via a *public interface*
* Bad practice to retrieve the object's information and perform an action outside of the object

Encapsulation should be used for several reasons:
* functionality is defined in one place instead of several places
* defined in a logical place - where the data exists
* data inside the object is not modified unexpectantly by outside code
* can use the same method on several, differently-valued objects

## Abstraction
* Like encapsulation because it hides certain properties and methods from the outside code to make the interface of the objects simpler.
* Overall, abstraction helps isolate the impact of changes made to the code so that if something goes wrong, the change will only affect the variables shown and not the outside code.

## Inheritance
* Can extend the functionality of the code's existing classes to eliminate repetitive code.
  * Instead of redefining the properties and methods for every type of HTML element, you can define them once in a generic object.
* Subclasses inherit elements from a *superclass* while implementing additional elements which are unique to the *subclass*.

## Polymorphism
* This concept allows one to redefine the way something works by changing how it is done or changing the parts in which it is done.
  * Overloading - babies first learn to crawl using their arms and legs.  Once they learn to walk using only their legs, is similar to the concept of overloading
  * Overriding - suppose you are walking forwards, then change direction and start walking backwards.  This action changes the direction and functionality of walking, similar to the concept of overriding