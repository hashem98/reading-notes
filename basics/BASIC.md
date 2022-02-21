# Java Basics
---
## in this class we'll learne ..
- Variables
- Operators
- Expressions, Statements, and Blocks
- Control Flow Statements

# Variables
### In java we use many differnt type of variable , for example :

* String
* int
* float
* char
* boolean
* long
* short
* double

## String
### String stores text , for example :

``` public class Main{
    public static void main(String[] args){
        String str = "Hello World"; 
        System.out.println(str); 
    }
}
// Out : Hello World
```
---
## Integers
### integers stores a real number , example :
``` 
public class Main{
    public static void main(String[] args){
        int val = 50 ; 
        System.out.println(val); 
    }
}
// Out : 50
```
----
## Float
### float stores a  decimals  number , example :
``` 
public class Main{
    public static void main(String[] args){
        int floatNumber = 5.75f; 
        System.out.println(floatNumber); 
    }
}
// Out : 5.75
```
----
## char
### char stores a charecter , example :
``` 
public class Main{
    public static void main(String[] args){
        char letter = 'h'; 
        System.out.println(letter); 
    }
}
// Out : h
```
----
## Boolean
### Boolean stores  true or false values
 , example :

----
# Operators
| Operators      | Precedence |
| ----------- | ----------- |
| postfix     |expr++ expr--    |
| multiplicative   | * / %        |
| additive   | + -        |
| shift   | << >> >>>       |
| relational   |  < > <= >= instanceof       |
|equality   | == !=        |
| AND   | &        |
| OR   | |        |
| logical AND   | &&        |
| logical OR   | ||        |
| ternary   | 	? :        |
| assignment   | = += -= *= /= %= &= ^= |= <<= >>= >>>=        |


# Expressions, Statements, and Blocks

## Expressions :-
```
public class Main{
    public static void main(String[] args){
        boolean flag = true ; 
        System.out.println(flag); 
    }
}
// Out : true 
```
### The expression ``` bool=true ``` returns an boolean because the assignment operator returns a value of the same data type as its left-hand operand;

# Statements
## Each statment followed by semicolon ```;``` :

# Blocks
## Block is group of statments between braces ``` {} ``` :
``` public class Main{
    public static void main(String[] args){ // begin block 
        boolean bool = true ; 
        System.out.println(bool); 
    } // end block 
}
// Out : true
 ```
# Control Flow Statements
### The execution flow do the statment from top to bottom in your code but controle flow statment can change things some of this control flow statment :
- decision making (if-then, if-then-else, switch)
- looping statements (for, while, do-while)
- branching statements (break, continue, return)
