# Java

## The Four Principles of Java

All ```the concepts of JAVA``` are based on classes and its objects. An object is a real world entity that has some attributes or properties. Class is a prototype, blueprint or template on the basis of which objects are created. An object cannot exist without a class.
The basic three principles of JAVA are defined below.

* ```Inheritance``` - a concept that is used for code re-usability.
* ```Polymorphism``` - polymorphism means many forms. It is a concept that allows one interface to be used for a general class of actions. It is also called 'one interface many methods '. For example there is a mobile set that contains many types of keys. Each key can perform several types of functions. It can either write digits, letters or symbols. This key is polymorphic because it can be used for performing many things at the same time. This is a suitable example of polymorphism. Method overriding is a part of polymorphism.
* ```Encapsulation``` - it is a concept that acts like a binding force. It prevents unauthorized access of a class from outside users. Encapsulation means 'in capsule' that means that everything is secured so that security of the class is maintained. It is implemented by the use of access specifiers for example public, private, protected. Access modifiers specify the access of one class from another class. For example if a class is defied as private then then it cannot be accessed from any other class. Public class can be accessed from any class that is within or outside the package. It acts as a security feature.
* ```Abstraction``` - abstraction is a process of hiding the implementation details from the user, only the functionality will be provided to the user. In other words, the user will have the information on what the object does instead of how it does it. In Java, abstraction is achieved using Abstract classes and interfaces.

## Inner Classes
Nested classes are divided into two types:

* **Non-static nested classes** − These are the non-static members of a class.
* **Static nested classes** − These are the static members of a class

![alt text](inner_classes.jpg "inner classes tree representation")

### Inner Classes (Non-static Nested Classes)

Inner classes are a security mechanism in Java. We know a class cannot be associated with the access modifier private, but if we have the class as a member of other class, then the inner class can be made private. And this is also used to access the private members of a class.

Inner classes are of three types depending on how and where you define them. They are:

* Inner Class
* Method-local Inner Class
* Anonymous Inner Class

#### Inner Class

Creating an **inner** class is quite simple. You just need to write a class within a class. Unlike a class, an inner class can be private and once you declare an inner class private, it cannot be accessed from an object outside the class.

```java
class Outer_Demo {
   // private variable of the outer class
   private int num = 175;  
   
   // inner class
   public class Inner_Demo {
      public int getNum() {
         System.out.println("This is the getnum method of the inner class");
         return num;
      }
   }
}

public class My_class2 {
   public static void main(String args[]) {
      // Instantiating the outer class
      Outer_Demo outer = new Outer_Demo();
      
      // Instantiating the inner class
      Outer_Demo.Inner_Demo inner = outer.new Inner_Demo();
      System.out.println(inner.getNum());
   }
}
```

```
Output

This is the getnum method of the inner class: 175
```

#### Method-local Inner Class

In Java, we can write a class within a method and this will be a local type. Like local variables, the scope of the inner class is restricted within the method.

```java
public class Outerclass {
   // instance method of the outer class 
   void my_Method() {
      int num = 23;

      // method-local inner class
      class MethodInner_Demo {
         public void print() {
            System.out.println("This is method inner class "+num);	   
         }   
      } // end of inner class
	   
      // Accessing the inner class
      MethodInner_Demo inner = new MethodInner_Demo();
      inner.print();
   }
   
   public static void main(String args[]) {
      Outerclass outer = new Outerclass();
      outer.my_Method();	   	   
   }
}
```

```
Output

This is method inner class 23
```

#### Anonymous Inner Class

An inner class declared without a class name is known as an anonymous inner class. In case of anonymous inner classes, we declare and instantiate them at the same time. Generally, they are used whenever you need to override the method of a class or an interface.

```java
abstract class AnonymousInner {
   public abstract void mymethod();
}

public class Outer_class {

   public static void main(String args[]) {
      AnonymousInner inner = new AnonymousInner() {
         public void mymethod() {
            System.out.println("This is an example of anonymous inner class");
         }
      };
      inner.mymethod();	
   }
}
```

```
Output

This is an example of anonymous inner class
```

***Explanation on how this abstract fuckery actually works*** <br/>
https://stackoverflow.com/questions/55045572/instantiation-of-abstract-classes 


### Static Nested Class

A static inner class is a nested class which is a static member of the outer class. It can be accessed without instantiating the outer class, using other static members. Just like static members, a static nested class does not have access to the instance variables and methods of the outer class.

```java
public class Outer {
   static class Nested_Demo {
      public void my_method() {
         System.out.println("This is my nested class");
      }
   }
   
   public static void main(String args[]) {
      Outer.Nested_Demo nested = new Outer.Nested_Demo();	 
      nested.my_method();
   }
}
```

## Packages

A ```package``` in Java is used to group related classes. Think of it as a folder in a file directory. We use packages to avoid name conflicts, and to write a better maintainable code. Packages are divided into two categories:

* Built-in Packages (packages from the Java API)
* User-defined Packages (create your own packages)


---
* The four Java principles
* Autoboxing and Unboxing