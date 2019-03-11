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
## Comparable and Comparator

In most real-life scenarios, we want sorting based on different parameters. For example, as a CEO, I would like to sort the employees based on Salary, an HR would like to sort them based on age. This is the situation where we need to use Java ```Comparator``` interface because ```Comparable```.compareTo(Object o) method implementation can provide default sorting and we can’t change it dynamically. Whereas with Comparator, we can define multiple methods with different ways of sorting and then chose the sorting method based on our requirements.

### Comparable
 ```java
@Override
public int compareTo(Employee emp) {
   return (this.id - emp.id);
}
```

### Comparator

```java
@Override
public int compare(Employee e1, Employee e2) {
   return e1.getName().compareTo(e2.getName());
}
```

## Immutable Classes

```Immutable class``` means that once an object is created, we cannot change its content. In Java, all the wrapper classes (like String, Boolean, Byte, Short) and String class is immutable. We can create our own immutable class as well.

Following are the requirements:
* Class must be declared as final (So that child classes can’t be created)
* Data members in the class must be declared as final (So that we can’t change the value of it after object creation)
* A parameterized constructor
* Getter method for all the variables in it
* No setters(To not have option to change the value of the instance variable) 

---

## Comparing Objects

* ```equals(Object obj)```: a method provided by java.lang.Object that indicates whether some other object passed as an argument is "equal to" the current instance. The default implementation provided by the JDK is based on memory location — two objects are equal if and only if they are stored in the same memory address.

* ```hashcode()```: a method provided by java.lang.Object that returns an integer representation of the object memory address. By default, this method returns a random integer that is unique for each instance. This integer might change between several executions of the application and won't stay the same.

The default implementation is not enough to satisfy business needs, especially if we're talking about a huge application that considers two objects as equal when some business fact happens. In some business scenarios, developers provide their own implementation in order to force their own equality mechanism regardless the memory addresses.

As per the Java documentation, developers should override both methods in order to achieve a fully working equality mechanism — it's not enough to just implement the equals() method.

---

## Autoboxing and Unboxing

```Autoboxing``` - converting a primitive value into an object of the corresponding wrapper class is called autoboxing. For example, converting int to Integer class. The Java compiler applies autoboxing when a primitive value is:

* Passed as a parameter to a method that expects an object of the corresponding wrapper class.
* Assigned to a variable of the corresponding wrapper class.

```Unboxing``` - converting an object of a wrapper type to its corresponding primitive value is called unboxing. For example conversion of Integer to int. The Java compiler applies unboxing when an object of a wrapper class is:

* Passed as a parameter to a method that expects a value of the corresponding primitive type.
* Assigned to a variable of the corresponding primitive type.

---

## Singleton

In object-oriented programming, a ```singleton class``` is a class that can have only one object (an instance of the class) at a time.
After first time, if we try to instantiate the Singleton class, the new variable also points to the first instance created. So whatever modifications we do to any variable inside the class through any instance, it affects the variable of the single instance created and is visible if we access that variable through any variable of that class type defined.

To design a singleton class:
1. Make constructor as private.
2. Write a static method that has return type object of this singleton class. Here, the concept of Lazy initialization in used to write this static method.

```java
class Singleton 
{ 
    private static Singleton single_instance = null;
    public String s; 
  
    // private constructor restricted to this class itself 
    private Singleton() { 
        s = "Hello I am a string part of Singleton class"; 
    } 
  
    // static method to create instance of Singleton class 
    public static Singleton getInstance() { 
        if (single_instance == null) 
            single_instance = new Singleton(); 
  
        return single_instance; 
    } 
} 
  
class Main { 
    public static void main(String args[]) { 
        Singleton x = Singleton.getInstance(); 
        Singleton y = Singleton.getInstance(); 
        Singleton z = Singleton.getInstance(); 
  
        x.s = (x.s).toUpperCase(); 
  
        System.out.println("String from x is " + x.s); 
        System.out.println("String from y is " + y.s); 
        System.out.println("String from z is " + z.s); 
        System.out.println("\n"); 
  
        z.s = (z.s).toLowerCase(); 
  
        System.out.println("String from x is " + x.s); 
        System.out.println("String from y is " + y.s); 
        System.out.println("String from z is " + z.s); 
    } 
} 

```

```
Output:

String from x is HELLO I AM A STRING PART OF SINGLETON CLASS
String from y is HELLO I AM A STRING PART OF SINGLETON CLASS
String from z is HELLO I AM A STRING PART OF SINGLETON CLASS

String from x is hello i am a string part of singleton class
String from y is hello i am a string part of singleton class
String from z is hello i am a string part of singleton class
```

## Stack Trace and Call Stack

```Stack trace``` is a representation of the ```call stack```. A stack trace is a report of the active stack frames at a certain point in time during the execution of a program. In other words, the call stack is the actual data structure in memory, while the stack trace is a snapshot of said data structure.

---

## Concurrency

### Synchronization

* ```Lock``` allows only one thread to enter the part that's locked and the lock is not shared with any other processes.
* ```Mutex``` is the same as a lock but it can be system wide (shared by multiple processes).
* ```Semaphore``` does the same as a mutex but allows x number of threads to enter, this can be used for example to limit the number of cpu, io or ram intensive tasks running at the same time.

* ```atomic``` variable - low-level direct operations, idk this one
* ```volatile``` variable - used to mark a Java variable as "being stored in main memory". More precisely that means, that every read of a volatile variable will be read from the computer's main memory, and not from the CPU cache, and that every write to a volatile variable will be written to main memory, and not just to the CPU cache. 

#### Possible problems
* ```Deadlock``` is a situation when two threads are waiting for each other and the waiting never ends. Here both threads cant complete their tasks.
* In ```Starvation```, threads are also waiting for each other. But here waiting time is not infinite after some interval of time, waiting thread always gets the resources whatever is required to execute thread **run()** method.
* ```Livelock``` occurs when two or more processes continually repeat the same interaction in response to changes in the other processes without doing any useful work. These processes are not in the waiting state, and they are running concurrently. This is different from a deadlock because in a deadlock all processes are in the waiting state.

---

## Lambda Expressions

```java
Collections.sort(employees, new Comparator<Employee>() {
   @Override
   public int compare(employee1, employee2) {
      return employee1.getName().compareTo(employee2.getName());
   }
});
```

```java
Collections.sort(employees, (Employee employee1, Employee employee2) ->
   employee1.getName().compareTo(employee2.getName())
);
```

It is also possible to add new blocks of code into methods (constructor in this case).

```java
UpperConcat uc = (s1, s2) -> {
   System.out.println("Lambda expression");
   String result = s1.toUpperCase() + " " + s2.toUpperCase();
   return result;
};
```

```
Output:

Initial expression
Lambda expression
STRING1 STRING2
```

```java
employees.forEach(e -> System.out.println(e.getName()));
```

### Predicate Interface

```java
static void pred(int number, Predicate<Integer> predicate) { 
   if (predicate.test(number)) { 
      System.out.println("Number " + number); 
   } 
} 
public static void main(String[] args) { 
   pred(10, (i) -> i > 7); 
} 
```

```
Output:

Number 10
```

### Functions

```java
Function<Employee, String> getLastName = employee ->
   employee.getName().substring(employee.getName().indexOf(' ') + 1);

System.out.println(getLastName.apply(new Employee("John", "Mayers")));
```

```
Output:

Mayers
```

### Streams

The ```Stream API``` is used to process collections of objects. A stream is a sequence of objects that supports various methods which can be pipelined to produce the desired result.
The features of Java stream are –

* A stream is not a data structure instead it takes input from the Collections, Arrays or I/O channels.
* Streams don’t change the original data structure, they only provide the result as per the pipelined methods.
* Each intermediate operation is lazily executed and returns a stream as a result, hence various intermediate operations can be pipelined. Terminal operations mark the end of the stream and return the result.

#### Different Operations On Streams

* Intermediate Operations:

   * ```map``` - used to map the items in the collection to other objects according to the Predicate passed as argument.
      ```java
      List number = Arrays.asList(2,3,4,5);
      List square = number.stream().map(x->x*x).collect(Collectors.toList());
      ```
   * ```filter``` - used to select elements as per the Predicate passed as argument.
      ```java
      List names = Arrays.asList("Reflection","Collection","Stream");
      List result = names.stream().filter(s->s.startsWith("S")).collect(Collectors.toList());
      ```
   * ```sorted``` - used to sort the stream.
      ```java
      List names = Arrays.asList("Reflection","Collection","Stream");
      List result = names.stream().sorted().collect(Collectors.toList());
      ```

* Terminal Operations:

   * ```collect``` - used to return the result of the intermediate operations performed on the stream.
      ```java
      List number = Arrays.asList(2,3,4,5,3);
      Set square = number.stream().map(x->x*x).collect(Collectors.toSet());
      ```
   * ```forEach``` - used to iterate through every element of the stream.
      ```java
      List number = Arrays.asList(2,3,4,5);
      number.stream().map(x->x*x).forEach(y->System.out.println(y));
      ```
   * ```reduce``` - used to reduce the elements of a stream to a single value. The reduce method takes a BinaryOperator as a parameter.

      ```java
      List number = Arrays.asList(2,3,4,5);
      int even = number.stream().filter(x->x%2==0).reduce(0,(ans,i)-> ans+i);
      ```

---

Trees