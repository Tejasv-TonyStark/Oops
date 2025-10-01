# Object-Oriented Programming (OOP) in Java

Object-Oriented Programming (OOP) is a programming paradigm based on the concept of objects. 
The four key principles of OOP are:

- **Encapsulation**
- **Abstraction**
- **Inheritance**
- **Polymorphism**

---

## 1. Encapsulation
Encapsulation is the process of **binding data (variables) and methods into a single unit (class)** 
and restricting direct access to some of the object’s components.

### Key Points
- Variables should be declared **private**.
- Access provided through **getters** and **setters**.
- Improves **security** and **modularity**.

### Example
```java
class Student {
    private String name;   // private variable
    private int age;

    Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setAge(int age) {
        if (age > 0) {
            this.age = age;
        }
    }
}
```

---

## 2. Abstraction
Abstraction means **hiding implementation details** and only showing essential features.

### Key Points
- Achieved using **abstract classes** and **interfaces**.
- Focuses on **what an object does** rather than **how it does it**.

### Example
```java
abstract class Animal {
    abstract void makeSound();  // Abstract method
}

class Dog extends Animal {
    void makeSound() {
        System.out.println("Woof Woof");
    }
}
```

---

## 3. Inheritance
Inheritance allows a class (**child/derived**) to acquire properties and behaviors from another class (**parent/base**).

### Key Points
- Promotes **code reusability**.
- Child can access all **non-private** members of the parent.
- A parent reference can hold a child object (polymorphic behavior).

### Example
```java
class A {
    int x = 10;

    void display() {
        System.out.println("Value of x: " + x);
    }
}

class B extends A {
    int y = 20;

    void show() {
        System.out.println("Value of y: " + y);
    }
}

public class Main {
    public static void main(String[] args) {
        B obj = new B();
        obj.display(); // Parent method
        obj.show();    // Child method
    }
}
```

---

### Private Members in Inheritance
```java
class Parent {
    private int secret = 100;
}

class Child extends Parent {
    void showSecret() {
        // System.out.println(secret); ❌ Not allowed
    }
}
```

---

### Parent Reference to Child Object
```java
A obj = new B();
obj.display(); // Works (from parent)
// obj.show(); // ❌ Not allowed
```

---

### `super` Keyword
`super` is used to call the parent constructor or parent methods.

```java
class Parent {
    int num;

    Parent(int num) {
        this.num = num;
    }
}

class Child extends Parent {
    Child(int num) {
        super(num);  // Calls parent constructor
    }
}
```

---

### Object Class
Every class in Java inherits from the `Object` class by default.

Common methods:
- `toString()`
- `equals()`
- `hashCode()`

```java
class Sample {
    int value = 5;
}

public class Main {
    public static void main(String[] args) {
        Sample s = new Sample();
        System.out.println(s.toString()); // Inherited from Object
    }
}
```

---

## 4. Types of Inheritance

### Single Inheritance
One child class inherits from one parent class.

```java
class Parent {
    void greet() {
        System.out.println("Hello from Parent");
    }
}

class Child extends Parent {
    void message() {
        System.out.println("Hello from Child");
    }
}
```

---

### Multiple Inheritance
Java does **not support multiple inheritance with classes** to avoid ambiguity, 
but it can be achieved using **interfaces**.

```java
interface A {
    void show();
}

interface B {
    void display();
}

class C implements A, B {
    public void show() {
        System.out.println("From A");
    }

    public void display() {
        System.out.println("From B");
    }
}
```

---

## 5. Polymorphism
Polymorphism allows the same method to perform different actions.

### Key Points
- **Compile-time (Method Overloading)**
- **Runtime (Method Overriding)**

### Example
```java
class Calculator {
    // Method Overloading
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }
}

class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Bark");
    }
}
```

---

## 6. Additional Important Points for Interviews

- **Constructor Chaining:** Child constructor automatically calls the parent constructor (explicitly using `super()` or implicitly).  
- **Final Keyword:** 
  - `final class` → cannot be inherited.  
  - `final method` → cannot be overridden.  
  - `final variable` → value cannot be changed.  
- **this vs super:**  
  - `this` → refers to the current class instance.  
  - `super` → refers to the parent class.  
- **Overloading vs Overriding:**  
  - Overloading → same method name, different parameters.  
  - Overriding → same method name & parameters, but redefined in child class.  
- **Interfaces vs Abstract Classes:**  
  - Interfaces → multiple inheritance, only method signatures (until Java 8 default methods).  
  - Abstract Classes → partial abstraction with both abstract and concrete methods.  

---

# 📌 Conclusion
- OOP revolves around Encapsulation, Abstraction, Inheritance, and Polymorphism.  
- Inheritance improves reusability but private members are not inherited.  
- `super` is used to call parent constructors and methods.  
- Java supports **single inheritance with classes** and **multiple inheritance through interfaces**.  
- `Object` class is the root of all Java classes.  
- Polymorphism is one of the most asked concepts in interviews (overloading vs overriding).  

---
