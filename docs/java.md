# Java

[Refer here for examples](https://github.com/vinkrish/DataStructure-Algorithm-Snippets_Java)

Java is a general-purpose programming language that is class-based, object-oriented, and designed to have as few implementation dependencies as possible.
 
**Class** : A template that describes the kinds of state and behavior that objects of its type support.

**Object** : An instance of class, which will have its own state and access to all of the behaviors defined by its class.

**State** : (Instance variable).

**Behavior** : (methods) where class' logic is stored or data gets manipulated.

...

**Inheritance** : allows code defined in one class to be reused in other classes.

**Interfaces** : 100 % abstract superclass that defines the methods a subclass must support but not how they must be supported.

## Java identifiers

1. Legal Identifiers - rules the compiler uses to determine whether a name is legal.
2. Sun's Java Code Conventions - for naming classes, vaiables and methods.
3. JavaBeans Naming Standards

### Legal Identifiers

- Identifiers can't start with a number.
- Java keywords can't be a identifier.
- Identifiers are case-sensitive.

### Sun's Java Code Conventions

- Classes and interfaces - camelCase, for interfaces names should typically be adjectives eg:(Runnable, Serializable).
- Methods - lower_camelcase, names should be verb-noun pairs.
- Variables - lower_camelcase.
- Constants - are created by marking variables static and final, names should be uppercase letters with underscore characters as seperators.

### JavaBeans Naming Standards

JavaBeans are Java classes that have properties:

- if property is not a boolean, the getter method's prefix must be get.
- if property is boolean, the getter method's prefix is either get or is.
- the setter method's prefix must be set.
- To complete the name of a getter or setter method, change the first letter of the property name to uppercase and then append.
- setter method signature must be marked public, with a void return type and argument that represents the property type.
- getter method signature must be marked public, take no arguments, and have a return type that matches the argument type of the setter method for that property.

JavaBean spec supports events, (eg: mouse click is multicast to many objects). The objects that receive the information that an event occurred are called  listeners.

JavaBean Listener Naming Rules:

- Listener method names must end with the words "Listener".
- The type of listener to be added or removed must be passed as the argument to the method.
- Listener method names used to register/remove a listner with an event source must use the perfix add/remove, followed by the listener type.

## Class Declarations and Modifiers:

| Modifier | Class | Package | Subclass(same pkg) | Subclass(diff pkg) | World |
| -------- | ------| ------- | ------------------ | ------------------ | ----- |
| public | + | + | + | + | + |
| protected | + | + | + | + | |
| no modifier | + | + | + | | |
| private | + | | | | |

Modifiers:
 
- Access modifiers(public, protected, private) 
- Non-access modifiers(strictfp, final, abstract)

four access controls but three access modifiers, the fourth access control level (called default or package access) is what you get when you don't use any of the three access modifiers.

### Class Access(access a class)
 
Access means visibility. class can be declared with default or public access.

- Default Access : class with default access can be seen only by classes within the same package.
- Public Access : gives all classes from all packages access to public class.

Non-access class modifiers - used in addition to access control. (below are valid combination)

- public_final, default_final
- public_abstract, default_final
- strictfp_final, public_strictfp, default_strictfp

Final Classes - class can't be subclassed.
Abstract Classes - can never be instantiated.

### Interface

It is a contract for what a class can do, without saying anything about how the class will do it.
Interface variables must be public, static and final = constants.

Interface methods:

- must not be static.
- can extend only Interface(many).
- cannot implement another interface or class.

### Modifiers On Member

Access Modifiers:

- Public Members - all other classes can access the member.
- Private Members - can be accessed by code in which they are declared.
- Protected and Default Members - default member may be accessed only if the class accessing the member belongs to the same package, whereas a protected member can be accessed by a subclass.
- Default Members - package level.

Nonaccess Member Modifiers:

- Final Methods - final keyword prevents the method from being overridden.
- Abstract Methods - declared but not implemented.
- Synchronized Methods - method can be accessed by only one thread at a time (applied only to methods).
- Native Methods - implemented in platform dependent code(like in C).

## Variable Declarations:

1. Primitives - char, boolean, byte, short, int, long, double, float.
2. Reference variables - used to refer (or access) an object. they can be static, instance variables, method parameters or local variables.

**Instance Variables** : are defined inside class but outside any method, and are only initialized when class is instantiated. they are the fields that belong to each unique object.

**Array** : objects that store multiple variables of the same type or variables that are all subclasses of the same type. can hold both primitives and object references.

**Final Variable** : cannot be reinitialized (primitives) or reference variable cannot be changed but data within the object can be modified.(no final object only final references).

**Static variables and Methods** : will exist independently of any instances created for the class (exist before we make instance of a class). one copy of static member exist regardless of number of instances of that class. static blocks are called before constructor.

**Enums** : (java 5)> restrict a variable to have pre-defined value from an enumerated list. (items in the list are called enums). Enums can be declared as seperate class or class member but never within a method.

...

Benefit of encapsulation - The ability to make changes in your implementation code without breaking the code of others who use your code.

access methods - getters and setters(accessors and mutators).

Hide implementation details behind a public programming interface, interface in the sense set of accessible methods your code makes available for other code to call - your code's API.

## Inheritance, Is-A, Has-A

instanceof operator: returns true if the reference variable being tested is of the type being compared to.
every class is subclass of class Object.

inheritance relationships can be created by extending a class. 
Reasons to use inheritance: To promote code reuse, To use polymorphism.

code reuse - generic functionality (like method) don't have to be reimplemented, all subclasses are guaranteed to have capabilities of the superclass.

**polymorphism** - treats any subclass of classA as classA, which allows you to write methods that don't need to change if new subclasses are created.
Runtime polymorphism doesn't happen when static

**IS-A** : based on class inheritance and interface implementation, "this thing is a type of that thing".

**HAS-A** : based on usage, class A HAS-A B if code in class A has a reference to an	instance of class B.
Polymorphic method invocations apply only to instance methods, at runtime the only things that are dynamically selected based on the actual object are instance methods. Only overriden instance methods are dynamically invoked based on the real object's type.

Overridden Methods - based on object type.
Polymorphism lets you use a abstract supertype reference to refer to one of its subtypes.

Overloading Methods - based on reference type.

...

**Coupling and Cohesion** : good OO design calls for loose coupling and high cohesion.

...

A primitive literal is merely a source code representation of primitive data types(eg:integer, floating-point number, boolean or character).

## Assignment

- Variables are bit Holders, with a designed type.
- A variable referring to an object is just that - a reference variable.
- A reference variable bit holder contains bits representing a way to get to the object.

## Reification

In computing, reification has come to mean an explicit representation of a type — that is, run-time type information.  
In Java, arrays reify information about their component types, while generic types do not reify information about their type parameters (while the type of a
parameterized type is reified without its type parameters).

In Java, we say that a type is reifiable if the type is completely represented at run time — that is, if erasure does not remove any useful information. 

To be precise, a type is reifiable if it is one of the following:

- A primitive type (such as int)
- A nonparameterized class or interface type (such as Number, String, or Runnable)
- A parameterized type in which all type arguments are unbounded wildcards (such as `List<?>, ArrayList<?>, or Map<?, ?>`)
-  A raw type (such as List, ArrayList, or Map)
-  An array whose component type is reifiable (such as `int[], Number[], List<?>[], List[], or int[][]`)

A type is not reifiable if it is one of the following:

- A type variable (such as T)
- A parameterized type with actual parameters (such as `List<Number>`, `ArrayList<String>`, or `Map<String, Integer>`)
- A parameterized type with a bound (such as `List<? extends Number>` or `Comparable<? super String>`)

So the type `List<? extends Object>` is not reifiable, even though it is equivalent to `List<?>`. Defining reifiable types in this way makes them easy to identify syntactically.

**Principle of Indecent Exposure:** This principle guarantees that the component type at compile time will be a reifiable type.

Based on above principle, never publicly expose an array where the components do not have a reifiable type.

**Principle of Truth in Advertising:** This principle guarantees that the reified component type returned at run time must be a subtype of the reifiable component type declared at compile time. 

Converse to cast-iron guarantee, above principle illustrates if there are unchecked warnings, then casts inserted by erasure may fail.

## Generics

In Java 5, the class Class has been made generic, and now has the form `Class<T>`. 

What does the T stand for?  
An instance of type `Class<T>` represents the type T. For example, `String.class` has type `Class<String>`.

**cast-iron guarantee:** No cast inserted by erasure will fail, so long as there are no unchecked warnings.

**The Get and Put Principle:**  
- use an extends wildcard when you only get values out of a structure
- use a super wildcard when you only put values into a structure
- don’t use a wildcard when you both get and put.

Why can't you create generic array type?  
Java's arrays (unlike generics) contain, at runtime, information about its component type. So you must know the component type when you create the array.

## Reflection

Every type in Java, including primitive types and array types, has a class literal and a corresponding class token.

generics for reflection: some of the types used for reflection are now generic types.  
reflection for generics: reflection now returns information about generic types.

Class represents information about the type of an object at run time. The method getClass() is defined on every object and returns a class token that represents the reified type information carried by that object at run-time.

class always represents a reifiable type, there is no point in parameterizing the class Class with a type that is not reifiable. Hence, the two main methods for producing a class with a type parameter, namely the getClass method and class literals, are both designed to yield a reifiable type for the type parameter in all cases.

Each class token corresponds to a reifiable type. If you try to reflect a parameterized type, you get the reified information for the corresponding raw type.

## Data Strucures

Collections come in four basic flavors:

- **Lists** : Lists of things (classes that implement List)
- **Sets** : Unique things (classes that implement Set)
- **Maps** : Things with a unique ID (classes that implement Map)
- **Queues** : Things arranged by the order in which they are to be processed

The core interfaces:

![Interfaces](https://vinkrish-notes.s3-us-west-2.amazonaws.com/collection_interface.png)

The core concrete implementation classes:

![Classes](https://vinkrish-notes.s3-us-west-2.amazonaws.com/collection_class.png)

The interface and class hierarchy for collections:

![Collection](https://vinkrish-notes.s3-us-west-2.amazonaws.com/collection.png)

Arrays

- Arrays are objects in Java that store multiple variables of same type.
- Arrays can store either primitives or object references.

List

- methods related to the index.
- eg:get(int index), indexof(Object o), add(int index, Object obj)

ArrayList

- ordered collection
- implements RandomAccess, marker Interface
- supports fast random access

Vector

- synchronized for thread safety
- implement RandomAccess

LinkedList

- ordered by index position and also elements are doubly linked to one another
- choose this for implementing a stack or queue

Set

- doesn't allow duplicates [using equals() method to determine identical objects]

HashSet

- unsorted, unordered Set
- uses hashcode of the object being inserted

LindkedHashset

- ordered and unsorted Set
- maintains doubly linked List across all elements
- iterates through the order in which they were inserted

TreeSet

- Sorted Set
- elements will be in ascending order, according to natural order

Map

- maps a unique key(ID) to a specific value
- can search for a valued based on the key
- uses equals() method to determine whether two keys are the same or different

HashMap

- unsorted and unordered Map
- allows one null key and multiple null values in a collection

LinkedHashMap

- maintains insertion order (optionally access order)
- faster iteration

Hashtable

- doesn't allow any null
- can't synchronize class: only key methods of the class are synchronized

TreeMap

- Sorted Map
- can define custom sort order(via a Comparable or Comparator)

Queue

- holds things to be processed in some way

Priority Queue

- to create "priority-in, priority-out" queue as opposed to FIFO
- ordered either by natural ordering or according to a Comparator

## Comparable Interface:

- A comparable object is capable of comparing itself with another object.
- Comparable provides compareTo() method to sort elements.
- Comparable affects the original class, i.e., the actual class is modified.
- Used by Collections.sort() and java.util.Arrays.sort() method.

## Comparator Interface

- A comparator object is capable of comparing two different objects. It is not comparing its instances, but some other class's instances. 
- Comparator provides compare() method to sort elements.
- Comparator doesn't affect the original class, i.e., the actual class is not modified.

## Developlment

```
javac [options] [source files]
java p[options] class [args]
```

## AOP

- Join Point represents the effective execution of a method where the aspect will be applied.
- Advice is the action taken by an aspect at the particular Join Point. eg: Before, After, AfterReturning, AfterThrowing.
- Spring AOP may create chains of Advice for one single Join Point.
- Pointcut is a predicate that matches Join Point.
- An Advice is associated with a Pointcut expression and runs at any Join Point matching that Pointcut.

## Equality

Often in Java programs you need to compare two objects to determine if they are equal or not.  It turns out there are two different kinds of equality one can determine about objects in Java, **reference equality** or **logical equality**.

Equality operator (==) compares the references (addresses in memory) of the two Strings as two different numbers - this is known as Reference Equality.

Logical equality compares the data of the objects instead of the value of the references.

> Why, you might ask, did the String class override the equals method inherited from the Object class? 

Because the equals method inherited from Object performs reference equality!  Here is what the implementation of the equals method in Object looks like:

```java
public boolean equals(Object other)
{
   return this == other;
}
```

Notice that the parameter type is Object - it must be Object or you will have overloaded equals instead of overriding it.

### Inheritance and the equals Method

When overriding the equals method in classes making use of inheritance it is important to keep the super class and sub-class as loosely coupled as possible. Loosely coupled classes make as few assumptions about each other as possible making the code more maintainable over time. A secondary goal is to avoid duplication of code.

## HashCode

General Contracts for hashCode() in Java:

- If two objects are considered equal, their hashcodes must also be equal.
- Whenever the hashCode() method is invoked on the same object more than once within a single execution of the application, hashCode() must return the same integer provided no information or fields used in equals and hashcode is modified.
- If two objects are not equaled by equals() method it is not require that there hashcode must be different. Though it’s always good practice to return different hashCode for unequal object.

You must override hashCode() in every class that overrides equals(). Failure to do so will result in a violation of the general contract for Object.hashCode(), which will prevent your class from functioning properly in conjunction with all hash-based collections, including HashMap, HashSet and HashTable.

Hashing retrieval is a two-step process:

- Find the right bucket...using hashCode()
- Search the bucket for the right element...using equals()

[Follow this for complete example...](https://stackoverflow.com/questions/1894377/understanding-the-workings-of-equals-and-hashcode-in-a-hashmap)

## Java 8
### Functional Interfaces

- A functional interface has a single abstract method.
- Functional interfaces included with Java runtime. eg: Runnable, Callable, Comparator, TimerTask
- Prior to Java 8 it is known as Single Abstract Method (SAM) Types. 

### Method References

Method reference is used to refer method of functional interface. It is compact and easy form of lambda expression. Each time when you are using lambda expression to just referring a method, you can replace your lambda expression with method reference.

**Types of Method References**

- Reference to a static method
- Reference to an instance method of a particular object or arbitrary object
- Reference to a constructor

Details:

**1. Reference to a Static Method**

You can refer to static method defined in the class. Following is the syntax and example which describe the process of referring static method in Java.

```java
ContainingClass::staticMethodName
```

**2. Reference to an Instance Method**

like static methods, you can refer instance methods also

```java
containingObject::instanceMethodName  
```

**3. Reference to a Constructor**

You can refer a constructor by using the new keyword

```java
ClassName::new
```

### Optional

Java 8 has introduced a new class Optional in java.util package. It is used to represent a value is present or absent. The main advantage of this new construct is that No more too many null checks. It avoids any runtime `NullPointerExceptions` and supports us in developing clean and neat Java APIs or Applications. Like Collections and arrays, it is also a Container to hold at most one value. Let us explore this new construct with some useful examples.

Advantages of Java 8 Optional:

- Null checks are not required.
- No more NullPointerException at run-time.
- We can develop clean and neat APIs.
- No more Boiler plate code

### Lambda Expressions

Lambda expressions can only appear in places where they will be assigned to a variable whose type is a functional interface.

One issue with anonymous classes is that if the implementation of your anonymous class is very simple, such as an interface that contains only one method, then the syntax of anonymous classes may seem unwieldy and unclear. In these cases, you're usually trying to pass functionality as an argument to another method, such as what action should be taken when someone clicks a button. Lambda expressions enable you to do this, to treat functionality as method argument, or code as data.

The previous section, Anonymous Classes, shows you how to implement a base class without giving it a name. Although this is often more concise than a named class, for classes with only one method, even an anonymous class seems a bit excessive and cumbersome. Lambda expressions let you express instances of single-method classes more compactly.

## Hibernate

Hibernate is an open-source and lightweight ORM tool that is used to store, manipulate and retrieve data from the database.

ORM -> Object Relational Mapping

Its is a programming strategy to map object with the data stored in the database.

Hibernate architecture comprises of many interfaces such as:

- Configuration
- SessionFactory
- Session
- Transaction...etc (Query, Criteria)

![hibernate_architecture](https://vinkrish-notes.s3-us-west-2.amazonaws.com/hibernate_architecture.jpg)

SessionFactory provides the instance of Session:

- It is a factory of Session
- It holds the data of second level cache that is not enabled by default
- It is a thread safe object

Session maintains a connection beetween hibernate application and database:

- It provides methods to store, update, delete or fetch data from the database such as persist(), update(), delete(), load(), get() etc
- It is a factory of Query, Criteria and Transaction. It provides factory methods to return these instances
- It is not thread safe

3 states of object (instance):

- 1. **Transient**: Th object is in transient state if it is just created but has no primary key (identifier) and not associated with session.
- 2. **Peristent**: The object is in persistent state if session is open, and you just saved the instance in the database or retreived the instance from the database.
- 3. **Detached**: The object is in detached state if session is closed. After detached state, object comes to persistent state if you call lock() or update() method.

3 ways of inheritance mapping:

- 1. Table Per Hierarchy
- 2. Table Per Concrete Class
- 3. Table Per Subclass

This will allow us to map ther inheritance hierarchy classes with the table of the database.

In table per hierarchy mapping, single table is required to map the whole hierarchy, an extra column is added to identify the class (known as discriminator column).

In case of table per concrete class, tables are created as per class. But duplicate column is added in subclass tables.

In table per subclass, tables are created as per class but related by foreign key. So there are no duplicate columns.

## Maven 

Tool used for building and managing any Java-based project.

### groupId

It identify your project uniquely across all projects, It has to follow the package name rules.

eg: org.apache.maven

A good way to determine the granularity of the groupId is to use the project structure. That is, if the current project is a multiple module project, it should append a new identifier to the parent's groupId.

eg: org.apache.maven.plugins

### artifactId

It is the name of the jar without version.

eg: maven