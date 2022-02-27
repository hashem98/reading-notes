# Read: 03 - Maps, primitives, File I/O
# Maps:
## ``Map`` is an ``object`` that maps ``keys`` to ``values``. A map cannot contain ``duplicate keys``: Each key can map to at most one value. 

## In the ``ArrayList`` chapter, you learned that Arrays store items as an ordered collection, and you have to access them with an ``index`` number . A ``HashMap`` however, store items in ``key/value`` pairs, and you can access them by an index of another type ``(e.g. a String)``.

# Example

```
// Import the HashMap class
import java.util.HashMap;

public class Main {
  public static void main(String[] args) {
    // Create a HashMap object called capitalCities
    HashMap<String, String> capitalCities = new HashMap<String, String>();

    // Add keys and values (Country, City)
    capitalCities.put("England", "London");
    capitalCities.put("Germany", "Berlin");
    capitalCities.put("Norway", "Oslo");
    capitalCities.put("USA", "Washington DC");
    System.out.println(capitalCities);
  }
}


```
---

## Access an Item
### To access a value in the HashMap, use the ``get()`` method and refer to its ``key``:
```
capitalCities.get("England");
```

---

## Remove an Item
### To remove an item, use the ``remove()`` method and refer to the ``key``:

``capitalCities.remove("England");``
 
``To remove all items, use the clear() method:``

---

# Java Type System
## In java Every primitive type like ``int``, ``boolean``, corresponds to a reference type like , , etc

```
Integer j = 1;          // autoboxing converted from primitive to reference type
int i = new Integer(1); // unboxing converting from reference type to primitive 
```
---

## Single Item Memory Footprint
---
### the primitive type variables have the following impact on the memory:
```
boolean– 1 bit
byte– 8 bits
short, char– 16 bits
int, float– 32 bits
long, double– 64 bits
```
---
### The primitive type live on the stack and The reference types are objects, they live on the heap and are relatively slow to access

```
Boolean– 128 bits
Byte– 128 bits
Short, Character– 128 bits
Integer, Float– 128 bits
Long, Double– 192 bits
```
---
## Memory Footprint for Arrays
```
long, double: m(s) = 128 + 64 s
short, char: m(s) = 128 + 64 [s/4]
byte, boolean: m(s) = 128 + 64 [s/8]
the rest: m(s) = 128 + 64 [s/2]
```
---
#### arrays of the primitive types long and double consume more memory than their wrapper classes Long and Double.
---
#### either that single-element arrays of primitive types are almost always more expensive (except for long and double) than the corresponding reference type.

---
# What Is an Exception?
### An exception is an event, which occurs during the execution of a program, that stop the normal flow of the program's instructions

exception objec: it's an object created by amethod to hand error off to the runtime system it will contains information about the error

throwing an exception: Creating an exception object and handing it to the runtime system

call stack :list of methods that had been called to get to the method where the error occurred

exception handler: block of code that can handle the exception that contained in method that run time system search about

---
## The Catch or Specify Requirement

### This means that code that might throw certain exceptions must be enclosed by either of these method

* try statement that catches the exception
* method that specifies that it can throw the exception

---
## Three Kinds of Exceptions:
* Checked Exception
   * Checked Exceptions are subject to the Catch or Specify Requirement

* Error
  * Runtime Exceptions are not subject to the Catch or Specify Requirement

* Runtime Exception
  * Runtime exceptions are not subject to the Catch or Specify Requirement
---

# Scanning :
### Objects of type Scanner are useful for breaking into tokens depend on their datat type **Breaking Input into Tokens** :By default, a scanner uses white space to separate tokens.

---
```
Scanner s = null;

try {
  s = new Scanner(new BufferedReader(new FileReader("xanadu.txt")));

  while (s.hasNext()) {
      System.out.println(s.next());
  }
} finally {
  if (s != null) {
      s.close();
  }
}
```

---
#### To use a different token separator, invoke useDelimiter(), specifying a regular expression.












