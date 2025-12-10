# ✅ Object-Oriented Programming (OOP) — Brush-Up

OOP is a programming paradigm that organizes code into objects — real-world entities that contain data (fields) and behavior (methods).

OOP has 4 main pillars:

⸻

### 1️⃣ Abstraction — “Show only what is needed”

You expose only the necessary details and hide the internal working.

✔ Example:
```java
List<Integer> list = new ArrayList<>();
list.add(10);
```
You know add() adds an element — you don’t know how the array grows internally → that is abstraction.

✔ Interview line:

Abstraction reduces complexity by exposing only essential features.

⸻

### 2️⃣ Encapsulation — “Bind data + methods and protect them”

Keep variables private and expose functionality through getters/setters.

✔ Example:
```java
class BankAccount {
    private double balance;

    public void deposit(double amount) { balance += amount; }
    public double getBalance() { return balance; }
}
```
balance is protected — clients cannot change it illegally.

✔ Interview line:

Encapsulation improves security and avoids accidental modification of data.

⸻

### 3️⃣ Inheritance — “Reuse code from parent”

A child class derives features from a parent class.

✔ Example:
```java
class Vehicle { void start() {} }
class Car extends Vehicle { void playMusic() {} }
```
✔ Interview line:

Inheritance provides reusability and establishes an IS-A relationship.

⸻

### 4️⃣ Polymorphism — “Many forms”

Same method behaves differently depending on the object.

✔ Two types:

1. Compile-time (Method Overloading)
```java
void print(int a) {}
void print(String s) {}
```
2. Runtime (Method Overriding)
```java
class Animal { void sound() { System.out.println("Animal sound"); } }
class Dog extends Animal { void sound() { System.out.println("Bark"); } }
```
Calling sound() chooses method at runtime based on object type.

✔ Interview line:

Polymorphism increases flexibility and enables dynamic behavior.

⸻

Here is a clean, crisp, interview-ready brush-up on Abstract Class vs Interface — the exact way to explain it in interviews.

⸻

# 🔥 ABSTRACT CLASS vs INTERFACE — Brush-Up

1️⃣ Purpose

### Abstract Class:

Used when classes share a common base with some default behavior.

### Interface:

Defines a contract → what the class must do, not how.

⸻

2️⃣ Methods

✔ Abstract Class
	•	Can have abstract methods (no body)
	•	Can have concrete methods (with body)
	•	Can have constructor

✔ Interface
	•	Until Java 8 → only abstract methods
	•	After Java 8 → can have:
	•	default methods (with body)
	•	static methods
	•	private methods (Java 9+)
	•	Cannot have constructors

⸻

3️⃣ Fields

✔ Abstract Class
	•	Can have instance variables
	•	Can have different access modifiers (private, protected, etc.)

✔ Interface
	•	All fields are public static final implicitly
(i.e., constants only)

⸻

4️⃣ Inheritance Rules

✔ Abstract Class
	•	A class can extend only ONE abstract class (single inheritance)
	•	Abstract class can extend another class (abstract or concrete)

✔ Interface
	•	A class can implement multiple interfaces
	•	Interface can extend multiple interfaces

⸻

5️⃣ When to Use What? (Interview Gold Answer)

✔ Use Abstract Class when:
	•	You want to provide partial implementation
	•	You want shared variables or methods
	•	Classes are closely related
	•	You need non-final fields

Real Example:
Animal abstract class → all animals have eat(), sleep(), but sound differs.

⸻

✔ Use Interface when:
	•	You want loose coupling
	•	You want to define a behavior/capability
(e.g., Runnable, Serializable, Comparable)
	•	A class needs to implement multiple behaviors

Real Example:
A class can be both Runnable and Comparable at the same time.

⸻

# Constants vs Enums

Constants are simple variable values with no enforcement or behavior.

Enums are powerful, type-safe, self-contained classes that represent a fixed set of related values. 
```java
public static final int PENDING = 0;
public static final int SUCCESS = 1;
public static final int FAILED = 2;

void process(int status) {
    if (status == SUCCESS) {
        ...
    }
}
```
If someone passes 5, code still compiles → Not safe.
```java
enum PaymentStatus {
    PENDING, SUCCESS, FAILED
}

void process(PaymentStatus status) {
    if (status == PaymentStatus.SUCCESS) {
        ...
    }
}
```
If someone passes anything else, the compiler rejects → Safe.

Enums with Behavior

Enums are actually classes, so you can add logic.
```java
enum Direction {
    NORTH(0), SOUTH(180), EAST(90), WEST(270);

    private int angle;

    Direction(int angle) {
        this.angle = angle;
    }

    public int getAngle() {
        return angle;
    }
}
```

# Marker interface

A Marker Interface is an interface that has no methods and no fields.

It is used only to mark a class with some metadata so that JVM or frameworks treat that class differently.

•	Serializable
•	Cloneable
•	Remote
•	RandomAccess


# 🔥 Java 8 Features 

Java 8 introduced functional programming, streams, default methods, and new APIs.
These features made Java more concise, expressive, and parallel-friendly.

⸻

### 1️⃣ Lambda Expressions

Anonymous functions written in a compact form.

Example:
```java
(nums) -> nums * 2
```
Why important?

	•	Enables functional programming
	•	Removes boilerplate code (anonymous classes)

Interview line:

Lambda expressions allow passing behavior as arguments.

⸻

### 2️⃣ Functional Interfaces

An interface with exactly one abstract method.

Examples:

	•	Runnable
	•	Callable
	•	Comparator
	•	Function, Predicate, Supplier, Consumer

Annotation:

@FunctionalInterface

Example:
```java
@FunctionalInterface
interface Calculator {
    int add(int a, int b);
}
```

⸻

### 3️⃣ Stream API

Processes collections in a functional, declarative way.

Key operations:

	•	Intermediate: map, filter, sorted, distinct
	•	Terminal: collect, forEach, reduce, count

Example:
```java
List<String> list = Arrays.asList("a","bb","ccc");

list.stream()
    .filter(s -> s.length() > 1)
    .forEach(System.out::println);
```
Benefits:

	•	Cleaner code
	•	Lazy evaluation
	•	Supports parallel execution via .parallelStream()

⸻

### 4️⃣ Default & Static Methods in Interfaces

Default method:

Allows interfaces to have method bodies.
```java
interface A {
    default void show() {
        System.out.println("Default");
    }
}
```
Static method:
```java
interface A {
    static void log() { }
}
```
Why?

	•	Backward compatibility
	•	Avoid breaking existing implementations

⸻

### 5️⃣ Optional Class

Avoids NullPointerException by modeling optional values.

Example:
```java
Optional<String> name = Optional.ofNullable("Akshith");
name.ifPresent(System.out::println);
```
Methods:

	•	isPresent()
	•	ifPresent()
	•	orElse()
	•	orElseThrow()

⸻

### 6️⃣ Method & Constructor References

Examples:
```java
System.out::println      // method reference
String::toUpperCase      // instance method reference
ArrayList::new           // constructor reference
```
Equivalent to lambda expressions.

Benefit:

Cleaner and more readable.

⸻

### 7️⃣ New Date & Time API (java.time package)

Replaces old Date and Calendar which were mutable and inconsistent.

Classes:

	•	LocalDate
	•	LocalTime
	•	LocalDateTime
	•	Instant
	•	Period, Duration

Example:
```java
LocalDate today = LocalDate.now();
LocalDate next = today.plusDays(5);
```

⸻

### 8️⃣ Collectors API

Used with streams for grouping, partitioning, etc.

Example:
```java
Map<Integer, List<String>> grouped =
    list.stream()
        .collect(Collectors.groupingBy(String::length));
```

⸻

### 9️⃣ Parallel Streams

For parallel execution of stream operations:
```java
list.parallelStream().forEach(System.out::println);
```
✔ Can speed up CPU-intensive tasks

❌ Not recommended for shared mutable data

⸻

🔟 Nashorn JavaScript Engine

A JavaScript engine added in Java 8 (deprecated later).

⸻

# Consumer, Supplier and Predicate

### 🔥 1. Consumer — Takes input, returns nothing

✔ Definition:

A Consumer represents an operation that accepts a single input and returns no result.
```java
@FunctionalInterface
public interface Consumer<T> {
    void accept(T t);
}
```
✔ Example:
```java
Consumer<String> print = s -> System.out.println(s);
print.accept("Hello");  // prints: Hello

list.forEach(s -> System.out.println(s));
```

⸻

### 🔥 2. Supplier — Provides output, takes nothing

✔ Definition:

A Supplier takes no input and returns a value.
```java
@FunctionalInterface
public interface Supplier<T> {
    T get();
}
```
✔ Example:
```java
Supplier<Double> randomSupplier = () -> Math.random();
System.out.println(randomSupplier.get());

Supplier<String> getName = () -> "Akshith";
```

⸻

### 🔥 3. Predicate — Takes input, returns boolean

✔ Definition:

A Predicate tests a condition and returns true/false.
```java
@FunctionalInterface
public interface Predicate<T> {
    boolean test(T t);
}
```
✔ Example:
```java
Predicate<Integer> isEven = n -> n % 2 == 0;
System.out.println(isEven.test(10)); // true

```
⸻

# Default & Static Methods in Interfaces

🔥 Default & Static Methods in Interfaces — Brush-Up

Before Java 8, interfaces could only contain abstract methods (and constants).

Java 8 introduced:

	•	Default methods → instance-level behavior
	•	Static methods → class-level behavior inside interfaces

These were added mainly for backward compatibility with the Collections and Stream APIs.

### 1️⃣ Default Methods in Interfaces

✔ What is a Default Method?

A method with a body inside an interface.
```java
default void show() {
    System.out.println("Showing...");
}
```
✔ Why Needed?

	•	To add new methods to interfaces without breaking existing implementations
	•	To provide common reusable behavior

✔ Usage Example:
```java
interface Vehicle {
    default void start() {
        System.out.println("Vehicle starting...");
    }
}

class Car implements Vehicle { }

new Car().start();  // Vehicle starting...
```
✔ Inside default methods you can:

	•	Use this
	•	Override them in implementing classes
	•	Provide reusable logic

⸻

## ⭐ Default Method Conflict (Important Interview Point)

If a class implements two interfaces with same default method → conflict occurs.
```java
interface A { default void show() { System.out.println("A"); } }
interface B { default void show() { System.out.println("B"); } }

class C implements A, B {
    @Override
    public void show() {
        A.super.show();  // or B.super.show()
    }
}
```
Interview line:

When two interfaces provide the same default method, the class must override it to resolve ambiguity.

⸻

### 2️⃣ Static Methods in Interfaces

✔ What are Static Methods?

A static method inside an interface is just like a static method in a class, but it belongs to the interface only, not to implementing classes.
```java
interface Utils {
    static void log(String msg) {
        System.out.println("LOG: " + msg);
    }
}
```
✔ How to call?
```java
Utils.log("Hello");
```
❌ You cannot call a static interface method on an object:
```java
Utils obj = new UtilsImpl();
obj.log("Hi"); // ❌ Not allowed
```
✔ Why Static Methods?

	•	Utility methods belonging logically to the interface
	•	Cleaner design (e.g., Collectors.toList() in Streams API)


# Exception Hierarchy

Exceptions are unexpected events that occur during runtime and can disrupt normal program flow.

Java uses exceptions to handle errors gracefully instead of crashing.

⸻

### 1️⃣ Exception Hierarchy (Very Important)
```
              java.lang.Object
                   ↓

                Throwable
              /           \
         Error           Exception
                         /        \
               Checked Exceptions  RuntimeException
```
## ✔ Error

	•	Serious issues → Not recoverable
	•	Examples: OutOfMemoryError, StackOverflowError
	•	You should not catch them normally.

## ✔ Exception

Recoverable problems. Two types:

⸻

### 2️⃣ Checked vs Unchecked Exceptions

## ✔ Checked Exceptions

	•	Checked at compile time
	•	Must be handled using:
	•	try-catch OR
	•	throws keyword

Examples:

	•	IOException
	•	SQLException
	•	ClassNotFoundException

Example:
```java
try {
    FileReader fr = new FileReader("test.txt");
} catch (IOException e) {
    e.printStackTrace();
}
```

⸻

## ✔ Unchecked Exceptions (RuntimeExceptions)

	•	Occur at runtime
	•	Not required to catch or declare
	•	Usually programming mistakes

Examples:

	•	NullPointerException
	•	ArrayIndexOutOfBoundsException
	•	ArithmeticException
	•	IllegalArgumentException

Example:
```java
int x = 10 / 0; // ArithmeticException
```

⸻

## 3️⃣ Common Built-in Exceptions

Runtime:

	•	NullPointerException
	•	NumberFormatException
	•	IllegalStateException
	•	ConcurrentModificationException
	•	IndexOutOfBoundsException

Checked:

	•	IOException
	•	FileNotFoundException
	•	SQLException
	•	ParseException

⸻

## 4️⃣ Exception Handling Blocks
 ```java
//try-catch

try {
    int x = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero");
}

// try-catch-finally

try {
    connection.open();
} finally {
    connection.close(); // always runs
}

// try-with-resources (Java 7+)

Automatically closes resources.

try (FileReader fr = new FileReader("file.txt")) {
    // use file
}
```

⸻

### 5️⃣ throws vs throw

✔ throw

Used to manually throw an exception.
```java
throw new IllegalArgumentException("Invalid age");
```
✔ throws

Used in method signature to indicate the method may throw exceptions.
```java
void read() throws IOException { }
```

⸻

### 6️⃣ Custom Exceptions

Use custom exceptions for business rules

Custom Checked Exception:
```java
class InvalidAgeException extends Exception {
    public InvalidAgeException(String msg) {
        super(msg);
    }
}
```
Custom Unchecked Exception:
```java
class InvalidInputException extends RuntimeException {
    public InvalidInputException(String msg) {
        super(msg);
    }
}

```
⸻

### 7️⃣ Exception Propagation

Runtime exceptions automatically propagate up the call stack until caught.
```
methodA() -> methodB() -> methodC()  
Exception occurs in C → goes to B → A → main → JVM
```
⸻

# Controller Advice, Rest Controller Advice, Exception Handler

@ExceptionHandler handles exceptions inside a single controller.

@ControllerAdvice applies cross-cutting exception handling to all controllers globally.

@RestControllerAdvice does the same but automatically returns JSON, making it ideal for REST APIs.
```java
@RestController
public class UserController {

    @GetMapping("/user/{id}")
    public String getUser(@PathVariable int id) {
        if(id <= 0) {
            throw new IllegalArgumentException("Invalid user id");
        }
        return "User found";
    }
}

@RestControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(IllegalArgumentException.class)
    public ResponseEntity<String> handleIllegal(IllegalArgumentException ex) {
        return ResponseEntity.badRequest().body(ex.getMessage());
    }

    @ExceptionHandler(Exception.class)
    public ResponseEntity<String> handleOther(Exception ex) {
        return ResponseEntity.status(500).body("Something went wrong");
    }
}
```

# Sealed Classes in Java

