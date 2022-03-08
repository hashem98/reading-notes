# Inheritance?
 Object-oriented programming allows classes to inherit commonly used state and behavior from other classes which each class is allowed to have one direct superclass, and each superclass has the potential for an unlimited number of subclasses

 ```
 class MountainBike extends Bicycle {

    // new fields and methods defining 
    // a mountain bike would go here

}
 ```
 > MountainBike it's subclasse which extend from the super Bicycle class

  > A subclass inherits all of the public and protected members of its parent, no matter what package the subclass is in. If the subclass is in the same package as its parent

  > A subclass does not inherit the private members of its parent class
  > A nested class has access to all the private members of its enclosing class

 # Interface
an interface is a group of related methods with empty bodies and it is like a reference type, similar to a class, that can contain only constants, method signatures, default methods, static methods, and nested types. Method bodies exist only for default methods and static methods. Interfaces cannot be instantiated—they can only be implemented by classes or extended by other interfaces

* Implementing an interface allows a class to become more formal about the behavior it promises to provide. Interfaces form a contract between the class and the outside world

  **we can see this interface**
```
interface Bicycle {

    //  wheel revolutions per minute
    void changeCadence(int newValue);

    void changeGear(int newValue);

    void speedUp(int increment);

    void applyBrakes(int decrement);
}

class ACMEBicycle implements Bicycle {

    int cadence = 0;
    int speed = 0;
    int gear = 1;
     void changeCadence(int newValue) {
         cadence = newValue;
    }

    void changeGear(int newValue) {
         gear = newValue;
    }
   then the main method  
```
# Interfaces as APIs
 this like standered package that contains complex methods that another companys wants to use in its own software product by it's own way 

 # Casting Objects
 * A cast, instructs the compiler to change the existing type of an object reference to another type.
 * In Java, all casting will be checked both during compilation and during execution to ensure that they are legitimate.

 
 > public MountainBike myBike = new MountainBike(); --> //then myBike is of type MountainBike.
 Object obj = new MountainBike();

 > Object obj = new MountainBike();    --> //then obj is both an Object and a MountainBike (until such time as obj is assigned another object that is not a MountainBike). This is called implicit casting.

 >MountainBike myBike = obj;  --> incorrect
 
 >MountainBike myBike = (MountainBike)obj; --> //This cast inserts a runtime check that obj is assigned a MountainBike so that the compiler can safely assume that obj is a MountainBike. If obj is not a MountainBike at runtime, an exception will be thrown



 

# Package
A package is a namespace that organizes a set of related classes and interfaces
