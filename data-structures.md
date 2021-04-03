# Static Arrays
Some common use cases are:
* Storing and accessing sequential data
* Temporarily storing objects
* Used by IO routines as buffers
* Lookup tables and inverse lookup tables
* Return multiple values from a function
* Used in dynamic programming to cache answers to subproblems

# Dynamic Arrays
Dynamic arrays can **grow** and **shrink** in size
* Typically implemented with a static array
  * Keep track of the number of elements added; once size capacity is reached, create a new static array with double the capacity and copy the original elements into it

# Linked Lists
What is linked list?
* A sequential list of nodes that hold data, which point to other nodes (also containing data)
* The last node points to **null**


Where are linked lists used?
* List, Queue, Stack implementations
* Creating circular lists
* Modelling real world objects such as trains
* Present in certain Hashtable implementations to deal with hasing collisions
* Often used in the implementation of adjacent lists for graphs

### Pointers
* **HEAD** which refers to the first node in the linked list
* **TAIL** which refers to the last node in the linked list
* Node an object of the linked list which contains data and pointers
* Pointers which reference another node in the linked list

### Types
* Singly linked lists *only* reference the next node in the linked list
* Doubly linked lists reference the next node *and* the previous node in the linked list

### Complexity Analysis
* Searching is O(n) for singly & doubly linked lists
* Insert at head is O(1)
* Insert at tail is O(1)
* Remove head is O(1)
* Removing at tail differs for singly & doubly linked:
  * O(n) for singly
  * O(1) for doubly
* Removing in middle is O(n) for both


# References
https://github.com/williamfiset/Algorithms