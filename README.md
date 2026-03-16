# Java Core

A reference guide covering core Java concepts and fundamentals.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Data Types](#data-types)
3. [Variables](#variables)
4. [Operators](#operators)
5. [Control Flow](#control-flow)
6. [Object-Oriented Programming (OOP)](#object-oriented-programming-oop)
7. [Arrays](#arrays)
8. [Strings](#strings)
9. [Exception Handling](#exception-handling)
10. [Collections Framework](#collections-framework)
11. [Generics](#generics)
12. [Interfaces and Abstract Classes](#interfaces-and-abstract-classes)
13. [Java I/O](#java-io)
14. [Multithreading](#multithreading)
15. [Lambda Expressions & Streams](#lambda-expressions--streams)

---

## Introduction

Java is a high-level, class-based, object-oriented programming language designed to have as few implementation dependencies as possible. It follows the **Write Once, Run Anywhere (WORA)** principle — compiled Java code can run on any platform that supports the Java Virtual Machine (JVM).

**Key features:**
- Platform independent
- Object-oriented
- Strongly typed
- Automatic memory management (Garbage Collection)
- Rich standard library

---

## Data Types

Java has two categories of data types:

### Primitive Types

| Type      | Size    | Range / Description                          |
|-----------|---------|----------------------------------------------|
| `byte`    | 8-bit   | -128 to 127                                  |
| `short`   | 16-bit  | -32,768 to 32,767                            |
| `int`     | 32-bit  | -2^31 to 2^31 - 1                            |
| `long`    | 64-bit  | -2^63 to 2^63 - 1                            |
| `float`   | 32-bit  | Single-precision floating point              |
| `double`  | 64-bit  | Double-precision floating point              |
| `char`    | 16-bit  | Unicode character ('\u0000' to '\uffff')     |
| `boolean` | 1-bit   | `true` or `false`                            |

### Reference Types

Reference types include classes, interfaces, arrays, and enums. They store references (memory addresses) to objects.

```java
String name = "Java";
int[] numbers = {1, 2, 3};
```

---

## Variables

```java
// Declaration and initialization
int age = 25;
double salary = 75000.50;
final double PI = 3.14159; // constant (cannot be reassigned)

// Type inference (Java 10+)
var message = "Hello, Java!"; // inferred as String
```

**Scope:**
- **Local variables** — declared inside a method; not accessible outside it.
- **Instance variables** — declared inside a class but outside methods; belong to an object.
- **Class (static) variables** — declared with `static`; shared across all instances.

---

## Operators

| Category       | Operators                            |
|----------------|--------------------------------------|
| Arithmetic     | `+`, `-`, `*`, `/`, `%`              |
| Relational     | `==`, `!=`, `<`, `>`, `<=`, `>=`     |
| Logical        | `&&`, `\|\|`, `!`                    |
| Bitwise        | `&`, `\|`, `^`, `~`, `<<`, `>>`      |
| Assignment     | `=`, `+=`, `-=`, `*=`, `/=`, `%=`   |
| Ternary        | `condition ? valueIfTrue : valueIfFalse` |

---

## Control Flow

### Conditionals

```java
// if-else
if (score >= 90) {
    System.out.println("A");
} else if (score >= 80) {
    System.out.println("B");
} else {
    System.out.println("C");
}

// switch
switch (day) {
    case "Monday":
        System.out.println("Start of the week");
        break;
    case "Friday":
        System.out.println("End of the week");
        break;
    default:
        System.out.println("Midweek");
}
```

### Loops

```java
// for loop
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}

// while loop
while (count > 0) {
    count--;
}

// do-while loop
do {
    System.out.println("Runs at least once");
} while (false);

// enhanced for loop (for-each)
for (String item : list) {
    System.out.println(item);
}
```

---

## Object-Oriented Programming (OOP)

Java is built around four core OOP principles:

### 1. Encapsulation

Bundling data and methods within a class and restricting direct access using access modifiers.

```java
public class Person {
    private String name;
    private int age;

    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
}
```

### 2. Inheritance

A class can inherit fields and methods from another class using `extends`.

```java
public class Animal {
    public void speak() { System.out.println("..."); }
}

public class Dog extends Animal {
    @Override
    public void speak() { System.out.println("Woof!"); }
}
```

### 3. Polymorphism

The ability of an object to take many forms. Achieved through method overriding and interfaces.

```java
Animal a = new Dog();
a.speak(); // prints "Woof!"
```

### 4. Abstraction

Hiding implementation details and exposing only what is necessary.

```java
public abstract class Shape {
    public abstract double area();
}

public class Circle extends Shape {
    private double radius;
    public Circle(double radius) { this.radius = radius; }

    @Override
    public double area() { return Math.PI * radius * radius; }
}
```

---

## Arrays

```java
// Single-dimensional
int[] nums = new int[5];
int[] primes = {2, 3, 5, 7, 11};

// Multi-dimensional
int[][] matrix = new int[3][3];
int[][] grid = {{1, 2}, {3, 4}, {5, 6}};

// Useful methods (java.util.Arrays)
Arrays.sort(primes);
Arrays.fill(nums, 0);
System.out.println(Arrays.toString(primes));
```

---

## Strings

Strings in Java are **immutable** objects of the `String` class.

```java
String s = "Hello, World!";

s.length();           // 13
s.toUpperCase();      // "HELLO, WORLD!"
s.substring(0, 5);    // "Hello"
s.contains("World"); // true
s.replace("World", "Java"); // "Hello, Java!"
s.split(", ");        // ["Hello", "World!"]
s.trim();             // removes leading/trailing whitespace

// StringBuilder for mutable strings
StringBuilder sb = new StringBuilder();
sb.append("Hello").append(" ").append("World");
String result = sb.toString();
```

---

## Exception Handling

```java
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero: " + e.getMessage());
} catch (Exception e) {
    System.out.println("General error: " + e.getMessage());
} finally {
    System.out.println("Always runs");
}

// Throwing exceptions
public void validate(int age) throws IllegalArgumentException {
    if (age < 0) throw new IllegalArgumentException("Age cannot be negative");
}

// Custom exception
public class MyException extends RuntimeException {
    public MyException(String message) { super(message); }
}
```

---

## Collections Framework

The Java Collections Framework provides interfaces and classes for storing and manipulating groups of objects.

```java
import java.util.*;

// List — ordered, allows duplicates
List<String> list = new ArrayList<>();
list.add("apple");
list.add("banana");

// Set — no duplicates
Set<Integer> set = new HashSet<>();
set.add(1);
set.add(2);

// Map — key-value pairs
Map<String, Integer> map = new HashMap<>();
map.put("one", 1);
map.put("two", 2);
int value = map.get("one"); // 1

// Queue
Queue<String> queue = new LinkedList<>();
queue.offer("first");
queue.poll(); // removes and returns "first"

// Stack
Deque<Integer> stack = new ArrayDeque<>();
stack.push(10);
stack.pop(); // 10
```

---

## Generics

Generics enable types (classes and interfaces) to be parameters, providing compile-time type safety.

```java
// Generic class
public class Box<T> {
    private T value;
    public Box(T value) { this.value = value; }
    public T getValue() { return value; }
}

Box<Integer> intBox = new Box<>(42);
Box<String> strBox = new Box<>("Hello");

// Generic method
public <T extends Comparable<T>> T max(T a, T b) {
    return a.compareTo(b) > 0 ? a : b;
}
```

---

## Interfaces and Abstract Classes

### Interface

An interface defines a contract that implementing classes must follow.

```java
public interface Drawable {
    void draw(); // implicitly public and abstract

    default void display() {
        System.out.println("Displaying: ");
        draw();
    }
}

public class Circle implements Drawable {
    @Override
    public void draw() { System.out.println("Drawing a circle"); }
}
```

### Abstract Class

An abstract class can have both abstract and concrete methods.

```java
public abstract class Vehicle {
    protected String brand;

    public Vehicle(String brand) { this.brand = brand; }

    public abstract void start();

    public void stop() { System.out.println(brand + " stopped."); }
}
```

**Key differences:**

| Feature              | Interface                     | Abstract Class             |
|----------------------|-------------------------------|----------------------------|
| Multiple inheritance | Yes (a class can implement many) | No (single inheritance)  |
| Constructor          | Not allowed                   | Allowed                    |
| Fields               | `public static final` only    | Any type                   |
| Method types         | Abstract + default + static   | Abstract + concrete        |

---

## Java I/O

```java
import java.io.*;
import java.util.Scanner;

// Reading from console
Scanner scanner = new Scanner(System.in);
String input = scanner.nextLine();

// Reading from a file
try (BufferedReader reader = new BufferedReader(new FileReader("file.txt"))) {
    String line;
    while ((line = reader.readLine()) != null) {
        System.out.println(line);
    }
}

// Writing to a file
try (BufferedWriter writer = new BufferedWriter(new FileWriter("output.txt"))) {
    writer.write("Hello, File!");
}
```

---

## Multithreading

Java supports concurrent execution through threads.

```java
// Extending Thread
class MyThread extends Thread {
    public void run() { System.out.println("Thread running"); }
}

// Implementing Runnable (preferred)
class MyTask implements Runnable {
    public void run() { System.out.println("Task running"); }
}

Thread t1 = new Thread(new MyTask());
t1.start();

// Using lambda
Thread t2 = new Thread(() -> System.out.println("Lambda thread"));
t2.start();

// Synchronization
public synchronized void increment() { count++; }
```

---

## Lambda Expressions & Streams

### Lambda Expressions (Java 8+)

A concise way to represent a single-method (functional) interface.

```java
// Before lambda
Runnable r = new Runnable() {
    public void run() { System.out.println("Hello"); }
};

// With lambda
Runnable r = () -> System.out.println("Hello");

// With parameters
Comparator<String> c = (a, b) -> a.compareTo(b);
```

### Streams (Java 8+)

Streams allow functional-style operations on collections.

```java
import java.util.stream.*;

List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6);

// Filter, map, collect
List<Integer> evens = numbers.stream()
    .filter(n -> n % 2 == 0)
    .collect(Collectors.toList()); // [2, 4, 6]

// Map and reduce
int sum = numbers.stream()
    .mapToInt(Integer::intValue)
    .sum(); // 21

// Sorted and distinct
List<String> names = Arrays.asList("Charlie", "Alice", "Bob", "Alice");
names.stream()
    .distinct()
    .sorted()
    .forEach(System.out::println); // Alice, Bob, Charlie
```

---

## Resources

- [Official Java Documentation](https://docs.oracle.com/en/java/)
- [Java Language Specification](https://docs.oracle.com/javase/specs/)
- [OpenJDK](https://openjdk.org/)
