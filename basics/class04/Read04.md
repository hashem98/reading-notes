# OOP
## What Is an Object:
### Objects are key to understanding object-oriented technology,They all have variables (state )and method(behavior) data encapsulation: Hiding internal state and requiring all interaction to be performed through an object's methods
## the objects provides a number of benefits:

* Information-hiding: the details of its internal implementation remain hidden from the outside world.

* Code re-use: If an object already exists you can use that object in your program. This allows specialists to implement/test/debug complex, task-specific objects, which you can then trust to run in your own code.

* Pluggability and debugging ease: If a particular object turns out to be problematic, you can simply remove it from your application and plug in a different object as its replacement. This is analogous to fixing mechanical problems in the real world. If a bolt breaks, you replace it, not the entire machine.

## What Is a Class? 
### A class is the blueprint from which individual objects are created.

```
class Bicycles {
   public static void main(String[] args) {

       // Create two different 
       // Bicycle objects
       Bicycle bike1 = new Bicycle();
       Bicycle bike2 = new Bicycle();

       // Invoke methods on 
       // those objects
       bike1.changeCadence(50);
       bike2.changeCadence(50);
      
   }
}
```

#### in this code as we can see that we have class called Bicycles and this class have two objects with different method .


---

## Declaring Classes

---
``` class MyClass {
    // variables, constructor for initializing new objects, and 
    // method declarations to implement the behavior of the class and its objects
}
```

#### class MyClass extends MySuperClass implements YourInterface means that MyClass is a subclass of MySuperClass and that it implements the YourInterface interface.

---

## Declaring Member Variables
---
## There are several kinds of variables:

* Member variables in a class—these are called fields.
* Variables in a method or block of code—these are called local variables.
* Variables in method declarations—these are called parameters.
## Access Modifiers
* public modifier—the field is accessible from all classes.
* private modifier—the field is accessible only within its own class.

# Defining Methods
1. Modifiers—such as public, private, and others you will learn about later.
2. The return type—the data type of the value returned by the method, or void if  the method does not return a value.
3. The method name—the rules for field names apply to method names as well, but the convention is a little different.
4. The parameter list in parenthesis—a comma-delimited list of input parameters, preceded by their data types, enclosed by parentheses, (). If there are no parameters, you must use empty parentheses.
5. The method body, enclosed between braces—the method's code, including the declaration of local variables, goes here.

---
## Overloading Methods
---
- The Java programming language supports overloading methods, and Java can distinguish between methods with different method signatures
- This means that methods within a class can have the same name if they have different parameter lists.
---
## Providing Constructors for Your Classes
#### Constructor declarations look like method declarations—except that they use the name of the class and have no return type.

----
## Arbitrary Number of Arguments
* You can use a construct called varargs to pass an arbitrary number of values to a method.

* You use varargs when you don’t know how many of a particular type of argument will be passed to the method.

* It’s a shortcut to creating an array manually (the previous method could have used varargs rather than an array).

* To use varargs, you follow the type of the last parameter by an ellipsis (three dots, …), then a space, and the parameter name. The method can then be called with any number of that parameter, including none.
---

```
public Polygon polygonFrom(Point... corners) {
    int numberOfSides = corners.length;
    double squareOfSide1, lengthOfSide1;
    squareOfSide1 = (corners[1].x - corners[0].x)
                     * (corners[1].x - corners[0].x) 
                     + (corners[1].y - corners[0].y)
                     * (corners[1].y - corners[0].y);
    lengthOfSide1 = Math.sqrt(squareOfSide1);

    // more method body code follows that creates and returns a 
    // polygon connecting the Points
}
```
* You can see that, inside the method, corners is treated like an array. The method can be called either with an array or with a sequence of arguments. The code in the method body will treat the parameter as an array in either case.

* You will most commonly see varargs with the printing methods; for example, this printf method:


---

```
public PrintStream printf(String format, Object... args)
allows you to print an arbitrary number of objects. It can be called like this:

System.out.printf("%s: %d, %s%n", name, idnum, address);
or like this

System.out.printf("%s: %d, %s, %s, %s%n", name, idnum, address, phone, email);
or with yet a different number of arguments.

```
---

## Creating Objects:
#### we can create an objects from the class that we have by new word


## The Garbage Collector:
* Some object-oriented languages require that you keep track of all the objects you create and that you explicitly destroy them when they are no longer needed. Managing memory explicitly is tedious and error-prone.

* The Java platform allows you to create as many objects as you want (limited, of course, by what your system can handle), and you don’t have to worry about destroying them.

* The Java runtime environment deletes objects when it determines that they are no longer being used. This process is called garbage collection.

* An object is eligible for garbage collection when there are no more references to that object.

* References that are held in a variable are usually dropped when the variable goes out of scope. Or, you can explicitly drop an object reference by setting the variable to the special value null.

* Remember that a program can have multiple references to the same object; all references to an object must be dropped before the object is eligible for garbage collection.
---

# Using the this Keyword:
#### The Decimal Number System is also called "Base 10", because it is based on the number 10, with these 10 symbols 1,2,3,4,5,6,7,8,9,0


## Binary Numbers
#### are just "Base 2" instead of "Base 10". So you start counting at 0, then 1, then you run out of digits ... so you start back at 0 again, but increase the number on the left by 1. 0,1,01,011,110

## Hexadecimal Numbers
#### There are 16 of them!They look the same as the decimal numbers up to 9, but then there are the letters ("A',"B","C","D","E","F") in place of the decimal numbers 10 to 15 0,1,1F


```
Decimal:	0	1	2	3	4	5	6	7	8	9	10	11	12	13	14	15
Hexadecimal:0	1	2	3	4	5	6	7	8	9	A	B	C	D	E	F

```










