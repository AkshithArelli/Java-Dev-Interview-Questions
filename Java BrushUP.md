# ✅ Object-Oriented Programming (OOP) — Brush-Up

OOP is a programming paradigm that organizes code into objects — real-world entities that contain data (fields) and behavior (methods).

OOP helps create software that is:

- **Modular**
- **Reusable**
- **Maintainable**
- **Extensible**

OOP has 4 main pillars:

⸻

### 1️⃣ Abstraction — “Show only what is needed”

You expose only the necessary details and hide the internal working.

 Example:
```java
List<Integer> list = new ArrayList<>();
list.add(10);
```
You know add() adds an element — you don’t know how the array grows internally → that is abstraction.

 Interview line:

Abstraction reduces complexity by exposing only essential features.

⸻

### 2️⃣ Encapsulation — “Bind data + methods and protect them”

Keep variables private and expose functionality through getters/setters.

 Example:
```java
class BankAccount {
    private double balance;

    public void deposit(double amount) { balance += amount; }
    public double getBalance() { return balance; }
}
```
balance is protected — clients cannot change it illegally.

 Interview line:

Encapsulation improves security and avoids accidental modification of data.

⸻

### 3️⃣ Inheritance — “Reuse code from parent”

A child class derives features from a parent class.

 Example:
```java
class Vehicle { void start() {} }
class Car extends Vehicle { void playMusic() {} }
```
 Interview line:

Inheritance provides reusability and establishes an IS-A relationship.

⸻

### 4️⃣ Polymorphism — “Many forms”

Same method behaves differently depending on the object.

 Two types:

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

 Interview line:

Polymorphism increases flexibility and enables dynamic behavior.

⸻

Here is a clean, crisp, interview-ready brush-up on Abstract Class vs Interface — the exact way to explain it in interviews.

⸻

# 🔥 ABSTRACT CLASS vs INTERFACE

1️⃣ Purpose

### Abstract Class:

Used when classes share a common base with some default behavior.

### Interface:

Defines a contract → what the class must do, not how.

⸻

2️⃣ Methods

 Abstract Class
 
	•	Can have abstract methods (no body)
	•	Can have concrete methods (with body)
	•	Can have constructor

 Interface
 
	•	Until Java 8 → only abstract methods
	•	After Java 8 → can have:
	•	default methods (with body)
	•	static methods
	•	private methods (Java 9+)
	•	Cannot have constructors

⸻

3️⃣ Fields

 Abstract Class
 
	•	Can have instance variables
	•	Can have different access modifiers (private, protected, etc.)

 Interface
 
	•	All fields are public static final implicitly
(i.e., constants only)

⸻

4️⃣ Inheritance Rules

 Abstract Class
 
	•	A class can extend only ONE abstract class (single inheritance)
	•	Abstract class can extend another class (abstract or concrete)

 Interface
 
	•	A class can implement multiple interfaces
	•	Interface can extend multiple interfaces

⸻

5️⃣ When to Use What? (Interview Gold Answer)

 Use Abstract Class when:
 
	•	You want to provide partial implementation
	•	You want shared variables or methods
	•	Classes are closely related
	•	You need non-final fields

Real Example:

Animal abstract class → all animals have eat(), sleep(), but sound differs.

⸻

 Use Interface when:
 
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
 Can speed up CPU-intensive tasks

❌ Not recommended for shared mutable data

⸻

🔟 Nashorn JavaScript Engine

A JavaScript engine added in Java 8 (deprecated later).

⸻

# Consumer, Supplier and Predicate

### 🔥 1. Consumer — Takes input, returns nothing

 Definition:

A Consumer represents an operation that accepts a single input and returns no result.
```java
@FunctionalInterface
public interface Consumer<T> {
    void accept(T t);
}
```
 Example:
```java
Consumer<String> print = s -> System.out.println(s);
print.accept("Hello");  // prints: Hello

list.forEach(s -> System.out.println(s));
```

⸻

### 🔥 2. Supplier — Provides output, takes nothing

 Definition:

A Supplier takes no input and returns a value.
```java
@FunctionalInterface
public interface Supplier<T> {
    T get();
}
```
 Example:
```java
Supplier<Double> randomSupplier = () -> Math.random();
System.out.println(randomSupplier.get());

Supplier<String> getName = () -> "Akshith";
```

⸻

### 🔥 3. Predicate — Takes input, returns boolean

 Definition:

A Predicate tests a condition and returns true/false.
```java
@FunctionalInterface
public interface Predicate<T> {
    boolean test(T t);
}
```
 Example:
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

 What is a Default Method?

A method with a body inside an interface.
```java
default void show() {
    System.out.println("Showing...");
}
```
 Why Needed?

	•	To add new methods to interfaces without breaking existing implementations
	•	To provide common reusable behavior

 Usage Example:
```java
interface Vehicle {
    default void start() {
        System.out.println("Vehicle starting...");
    }
}

class Car implements Vehicle { }

new Car().start();  // Vehicle starting...
```
 Inside default methods you can:

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

 What are Static Methods?

A static method inside an interface is just like a static method in a class, but it belongs to the interface only, not to implementing classes.
```java
interface Utils {
    static void log(String msg) {
        System.out.println("LOG: " + msg);
    }
}
```
 How to call?
```java
Utils.log("Hello");
```
❌ You cannot call a static interface method on an object:
```java
Utils obj = new UtilsImpl();
obj.log("Hi"); // ❌ Not allowed
```
 Why Static Methods?

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
##  Error

	•	Serious issues → Not recoverable
	•	Examples: OutOfMemoryError, StackOverflowError
	•	You should not catch them normally.

##  Exception

Recoverable problems. Two types:

⸻

### 2️⃣ Checked vs Unchecked Exceptions

##  Checked Exceptions

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

##  Unchecked Exceptions (RuntimeExceptions)

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

 throw

Used to manually throw an exception.
```java
throw new IllegalArgumentException("Invalid age");
```
 throws

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

Sealed classes restrict which classes can extend them.

Each permitted subclass must be final, sealed, or non-sealed, giving complete control over inheritance and enabling exhaustive pattern matching.
```java
public sealed class Payment permits CardPayment, UpiPayment, WalletPayment { }

public final class CardPayment extends Payment { }
public final class UpiPayment extends Payment { }
public non-sealed class WalletPayment extends Payment { }
```

# Serialization vs Deserialization
```
Concept				Meaning										Direction
Serialization		Converting a Java object → byte stream		Object ➝ Bytes
Deserialization		Converting a byte stream → Java object		Bytes ➝ Object
```

# sealed classes

1️⃣ Definition

transient keyword prevents a field from being serialized—those fields are skipped when an object is converted to bytes.

⸻

2️⃣ Why Needed?

	•	To avoid serializing sensitive data (passwords, tokens)
	•	To skip temporary or derived values

⸻

3️⃣ Key Features

	•	transient fields → not written during serialization
	•	When deserialized → restored with default values
	•	Works only with fields
	•	static fields aren’t serialized anyway

⸻

4️⃣ Example
```java
class User implements Serializable {
    private String name;
    private transient String password; // will not be serialized
}

User u = new User("Akshith", "secret123");
```
After deserialization:

	•	name = “Akshith”
	•	password = null

⸻

# Shallow Copy vs Deep Copy

### Shallow Copy

A shallow copy copies only the top-level object, but does not copy nested objects. Both objects share the same references inside.

### Deep Copy

A deep copy creates a fully independent clone by copying all nested objects recursively.

Shallow Copy example
```java
class Student implements Cloneable {
    String name;
    Address address; // mutable reference type

    public Student clone() throws CloneNotSupportedException {
        return (Student) super.clone(); // shallow copy
    }
}

class Address {
    String city;
}
```

Deep Copy example
```java
class Student implements Cloneable {
    String name;
    Address address;

    public Student clone() throws CloneNotSupportedException {
        Student copy = (Student) super.clone();
        copy.address = new Address(address.city); // deep copy
        return copy;
    }
}

class Address {
    String city;
    Address(String city) { this.city = city; }
}
```

# Multithreading

### ✅ 1️⃣ Thread — Definition

A Thread is the smallest unit of execution in a program. Multiple threads allow parallelism.

⸻

🚀 Why Threads?

	•	Perform multiple tasks simultaneously
	•	Improve performance
	•	Background tasks (timers, async calls, schedulers)

⸻


### ✅ 2️⃣ Thread Creation (Two Ways)

Method 1: Extending Thread class
```java
class MyThread extends Thread {
    @Override
    public void run() {
        System.out.println("Thread running");
    }
}

new MyThread().start();
```
Method 2: Implementing Runnable (preferred)
```java
class MyTask implements Runnable {
    public void run() {
        System.out.println("Task executing");
    }
}

Thread t = new Thread(new MyTask());
t.start();
```
✔ Runnable is preferred because Java supports multiple interface inheritance, not multiple class inheritance.

⸻


### ✅ 3️⃣ start() vs run()
```
start()							run()
Creates a new OS thread			Does NOT create a new thread
Calls JVM to schedule thread	Runs like a normal method
Executes asynchronously			Executes synchronously
```
Example:
```java
Thread t = new Thread(() -> System.out.println("Running"));
t.start();  // New thread  
t.run();    // Same thread (main)
```

⸻

### ✅ 4️⃣ Thread Life Cycle

NEW → RUNNABLE → RUNNING → BLOCKED/WAITING → TERMINATED

States:
```
	1.	NEW – thread created but start() not called
	2.	RUNNABLE – eligible for CPU scheduling
	3.	RUNNING – executing instructions
	4.	BLOCKED / WAITING
		•	sleep()
		•	wait()
		•	I/O blocking
	5.	TERMINATED – completed or stopped
```
⸻

### ✅ 1️⃣ Synchronization

Definition

Synchronization ensures only one thread at a time can access shared resources, preventing race conditions.

⸻

Examples

✔ Synchronized Method
```java
public synchronized void increment() {
    count++;
}
```
✔ Synchronized Block (preferred)
```
synchronized (lock) {
    count++;
}
```
✔ Object-level Lock vs Class-level Lock
```
public synchronized void method() {} 
// locks 'this' object

public static synchronized void method() {}
// locks Class object
```

⸻

### ✅ 6️⃣ wait(), notify(), notifyAll()

Used for inter-thread communication, especially in producer–consumer.

✔ wait()

	•	Releases lock
	•	Moves thread to WAITING state

✔ notify()

	•	Wakes one waiting thread

✔ notifyAll()

	•	Wakes all waiting threads

Example:
```
synchronized (lock) {
    lock.wait();      // thread waits
    lock.notify();    // wake one
    lock.notifyAll(); // wake all
}
```
✔ Must be called inside synchronized block
✔ Used for coordination between threads

⸻

### ✅ 7️⃣ volatile — Definition

volatile ensures visibility of changes across threads.

What it does:

	•	Prevents thread caching
	•	Always reads from main memory
	•	Writes go directly to main memory

Example:
```java
volatile boolean flag = true;
```
Without volatile, one thread may not see updated values written by another thread.

volatile DOES NOT:

	•	Make operations atomic
	•	Replace synchronization

⸻

### ✅ 8️⃣ thread.join() — Definition

join() makes one thread wait until another thread completes execution.

Example:
```java
Thread t = new Thread(() -> {
    System.out.println("Task");
});

t.start();
t.join();  // main waits until t finishes
System.out.println("Main continues");
```
✔ Used when a task must finish before continuing
✔ Useful in multi-thread pipelines

⸻

### ✅ 9️⃣ Thread Priority

In Java:

	•	Priorities range 1 to 10
	•	Thread.MAX_PRIORITY = 10
	•	Thread.MIN_PRIORITY = 1
	•	Thread.NORM_PRIORITY = 5

Set priority:

t.setPriority(Thread.MAX_PRIORITY);

But…

Thread priority is only a hint to the scheduler.
JVM & OS may ignore it.

⸻

Here is a clean, crisp, interview-ready brush-up on Synchronization, Deadlocks, and ReentrantLock — in the structured format you prefer.

⸻

🚀 BRUSH-UP: SYNCHRONIZATION, DEADLOCK, REENTRANTLOCK

⸻

# 🔥 Deadlock

Definition

Deadlock is a situation where two or more threads are permanently blocked, each waiting for a resource held by the other.

⸻

### Four Conditions Required for Deadlock (VERY IMPORTANT)

All four must exist simultaneously:

1️⃣ Mutual Exclusion
Only one thread can access a resource at a time.

2️⃣ Hold and Wait
Thread holds one resource and waits for another.

3️⃣ No Preemption
Resources cannot be forcibly taken away.

4️⃣ Circular Wait
Thread A waits for Thread B’s resource,
Thread B waits for Thread C’s resource…
Thread N waits for Thread A’s resource.

If you break any one of these conditions → deadlock is prevented.

⸻

Simple Deadlock Example
```java
Thread t1 = new Thread(() -> {
            synchronized (lock1) {
                System.out.println("T1 locked lock1");

                try { Thread.sleep(100); } catch (Exception ignored) {}

                synchronized (lock2) {
                    System.out.println("T1 locked lock2");
                }
            }
        });

        Thread t2 = new Thread(() -> {
            synchronized (lock2) {
                System.out.println("T2 locked lock2");

                try { Thread.sleep(100); } catch (Exception ignored) {}

                synchronized (lock1) {
                    System.out.println("T2 locked lock1");
                }
            }
        });

        t1.start();
        t2.start();
```		
Two threads locking in opposite order → deadlock.

⸻

### 🛡 Deadlock Prevention Techniques

✔ 1. Lock Ordering (Most Common)

Always acquire locks in the same order everywhere.

synchronized(lock1) {
    synchronized(lock2) { }
}

⸻

✔ 2. Timeout using tryLock()

If lock cannot be acquired → avoid waiting forever.

if (lock.tryLock(100, TimeUnit.MILLISECONDS)) {
    // do work
} else {
    // handle timeout
}


⸻

✔ 3. Avoid Nested Locks

Break complex locking structures.
Simplify critical sections.

⸻

✔ 4. Use Higher Level Concurrency Tools

	•	Executors
	•	Semaphores
	•	ConcurrentHashMap
	•	Atomic variables

⸻

✔ 5. Using volatile + immutable objects

Reduces need for locking.

⸻

# 🔐 ReentrantLock

Definition

A reentrant lock is an advanced locking mechanism from java.util.concurrent.locks that allows a thread to acquire the same lock multiple times without blocking itself.

⸻

Why Needed?

	•	More flexibility than synchronized
	•	Allows:
	•	timed lock attempts
	•	interruptible lock attempts
	•	fairness policies
	•	manual lock/unlock control

⸻

Key Features

✔ 1. Reentrancy

A thread holding a lock can acquire it again.

✔ 2. tryLock()

Avoids blocking forever; useful to prevent deadlocks.

if (lock.tryLock()) {
    // acquired
}

✔ 3. tryLock(timeout, unit)

Wait for limited time → timeout instead of deadlock.

✔ 4. Interruptible Locks

lock.lockInterruptibly();

Useful when a waiting thread should be interruptible.

✔ 5. Fairness Policy

ReentrantLock lock = new ReentrantLock(true); // fair mode

Maintains queue order of threads.

⸻
```java
import java.util.concurrent.locks.ReentrantLock;

public class ReentrantExample {

    private static final ReentrantLock lock = new ReentrantLock();

    public static void main(String[] args) {
        new ReentrantExample().methodA();
    }

    public void methodA() {
        lock.lock();   // Thread acquires lock 1st time
        try {
            System.out.println("Inside methodA - lock acquired once");

            methodB(); // Call another method that tries to acquire same lock
        } finally {
            lock.unlock();
        }
    }

    public void methodB() {
        lock.lock();   // Thread acquires SAME LOCK 2nd time
        try {
            System.out.println("Inside methodB - lock acquired second time by SAME thread");
        } finally {
            lock.unlock();
        }
    }
}
```

Here is your clean, crisp, interview-ready brush-up for:
	•	Runnable vs Callable
	•	Future vs CompletableFuture
	•	@Async vs ThreadPoolExecutor

Structured in the same format you prefer.

⸻

# Runnable vs Callable

⸻

✅ 1️⃣ Definition

Runnable

Represents a task that does not return a value and cannot throw checked exceptions.

Callable

Represents a task that returns a value and can throw checked exceptions.

⸻
Examples:
```java
Runnable task = () -> {
	System.out.println("Runnable task is running.");
};

Thread thread = new Thread(task);
thread.start(); // Starts the thread

Callable<Integer> task = () -> {
	System.out.println("Callable task is running.");
	return 123; // return result
};
```	
⸻


# 🚀 Future vs CompletableFuture

✔ 1️⃣ Future

Represents the result of an asynchronous computation, but is blocking and limited.

✔ 2️⃣ CompletableFuture — Definition

An advanced async API that supports non-blocking, chaining, callbacks, combining tasks, and fully asynchronous pipelines.

⸻

✔ Examples

Future (Blocking)
```java
Future<Integer> future = executor.submit(() -> 10);
int result = future.get(); // blocking
```

⸻

CompletableFuture (Non-Blocking)
```java
CompletableFuture.supplyAsync(() -> 10)
    .thenApply(n -> n * 2)
    .thenAccept(System.out::println);
```
Pipeline explained:

	•	supplyAsync → produce value
	•	thenApply → transform value
	•	thenAccept → consume value

✔ No blocking

✔ Runs asynchronously

⸻

✔ One-line Summary

Future is blocking and limited, while CompletableFuture supports async pipelines, chaining, combining tasks, and non-blocking programming.

⸻

# ExecutorService & Thread pools

ExecutorService manages a pool of threads.

Instead of creating threads manually, we submit tasks to the executor.

This improves performance, reduces memory usage, avoids too many threads, and provides clean task management.

A thread pool is a group of worker threads maintained by the ExecutorService.
```
           Submit Tasks
                |
                v
        +-----------------+
        | ExecutorService |
        +-----------------+
          /     |      \
         v      v       v
   Worker1   Worker2  Worker3   <-- Thread Pool
```

# ForkJoinPool for divide-and-conquer vs vs normal ExecutorService

It uses a technique called:

Fork → Divide task into smaller subtasks

Join → Combine results of subtasks

Think of it like splitting a big job into small parts, processing all parts in parallel, then merging results.

⸻

Why ForkJoinPool (vs normal ExecutorService)?

Normal ExecutorService works best when:

•	each task is independent
•	tasks are not recursively broken down

ForkJoinPool is designed for:

•	recursive tasks (divide and conquer)
•	tasks that can be split into smaller tasks
•	tasks that benefit from parallel computation (CPU-heavy)
```
                          MAIN TASK
                              |
                     -----------------
                     |               |
                  SubTask1       SubTask2
                   |   |           |   |
                T1    T2        T3     T4
```
All run in parallel → Combine results → Final answer

# @Async vs ThreadPoolExecutor

@Async is only a declarative annotation for executing a method asynchronously. It internally uses a TaskExecutor (usually ThreadPoolTaskExecutor).

If you need fine control over the thread pool (core size, max size, queue, rejection policy), configure a ThreadPoolTaskExecutor manually and point @Async to it.


Here is a clean, crisp, interview-ready brush-up on Atomic Classes vs volatile — in your preferred structured format.

⸻

# Atomic Classes vs volatile

⸻

volatile

volatile guarantees visibility of changes across threads but does NOT make operations atomic.

Atomic Classes (java.util.concurrent.atomic)

Atomic classes provide atomic (thread-safe) operations like increment, decrement, compare-and-set without using synchronization.

Example:

Even if volatile int count is visible to all threads,

count++;

is NOT atomic because it’s 3 operations internally:

	1.	read
	2.	increment
	3.	write

Multiple threads can interleave → inconsistent results.

⸻

🚀 Atomic Classes (Overview)

Popular classes:

	•	AtomicInteger
	•	AtomicLong
	•	AtomicBoolean
	•	AtomicReference
	•	AtomicLongArray, etc.

⸻

🔥 AtomicInteger Example

AtomicInteger count = new AtomicInteger(0);
```
count.incrementAndGet(); // atomic ++
count.getAndIncrement();
count.addAndGet(5);
```
These operations are atomic, no race conditions, no synchronized needed.

🚀 volatile Example (Visibility Guarantee)

```java
volatile boolean flag = true;

Thread t = new Thread(() -> {
    while (flag) { }
    System.out.println("Stopped");
});
t.start();

Thread.sleep(1000);
flag = false; // visible immediately to t
```

### ✔ Difference

volatile prevents stale reads; atomic classes prevent race conditions.

⸻

