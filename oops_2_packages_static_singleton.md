# OOPS Lecture 2

---

## Introduction
This lecture covers **Packages, Static elements, Inner Classes, and Singleton classes**. Focus is on understanding why these concepts exist and how they are used in Java.

---

## Packages Example
### Theory
- Packages allow you to **organize classes** and avoid **name conflicts**.  
- If two classes have the same name, putting them in different packages allows both to exist.  
- Packages also make code **reusable** by enabling imports.

### Code Example
```java
// File: com/example/package1/Main.java
package com.example.package1;
public class Main {
    public void greet() {
        System.out.println("Hello from package1!");
    }
}

// File: com/example/package2/Main.java
package com.example.package2;
public class Main {
    public void greet() {
        System.out.println("Hello from package2!");
    }
}

// File: TestPackages.java
import com.example.package1.Main as Main1;
import com.example.package2.Main as Main2;

public class TestPackages {
    public static void main(String[] args) {
        Main1 obj1 = new Main1();
        Main2 obj2 = new Main2();
        obj1.greet(); // Output: Hello from package1!
        obj2.greet(); // Output: Hello from package2!
    }
}
```

---

## Java Packages
- Packages are like **namespaces or directories** for classes.  
- Helps **avoid naming conflicts** and **organize code logically**.

---

## import Statement
- Use `import` to **access classes** from other packages:  
```java
import java.util.ArrayList; // Access ArrayList class
```

---

## Static Elements Example
### Theory
- **Static members** belong to the **class**, not individual objects.  
- Can be accessed using **class name**, without creating an object.  
- Useful for **shared/common properties**.

### Code
```java
class Human {
    static int population = 7000000000; // shared variable
    String name;

    Human(String name) {
        this.name = name;
    }

    void display() {
        System.out.println(name + " belongs to population: " + population);
    }
}

public class TestStatic {
    public static void main(String[] args) {
        Human h1 = new Human("Alice");
        Human h2 = new Human("Bob");
        h1.display(); // Alice belongs to population: 7000000000
        h2.display(); // Bob belongs to population: 7000000000
    }
}
```

---

## Static Variable Meaning
- **Static variables** are **shared across all objects**.  
- Initialized once at class load time.

---

## Non-static Member Inside a Static Context
- **Cannot directly access non-static members** inside static methods or static blocks.  
- Example:
```java
class Demo {
    int x = 10; // non-static
    static void test() {
        // System.out.println(x); // Error
    }
}
```

---

## Static Member Inside a Non-Static Class
- Static members **can exist in non-static classes**.  
- Access using **class name** or **object**, but object is optional.  

```java
class Outer {
    static int count = 0; // static variable
}
public class TestOuter {
    public static void main(String[] args) {
        System.out.println(Outer.count); // 0
    }
}
```

---

## this Keyword Inside Static
- `this` **cannot be used inside static methods or blocks** because `this` refers to **object instance**, which may not exist.

---

## Initialization of Static Variables
- Use **static blocks** to initialize complex static variables:  
```java
class Demo {
    static int x;
    static {
        x = 100; // static block
        System.out.println("Static block executed");
    }
    public static void main(String[] args) {
        System.out.println(Demo.x); // 100
    }
}
```

---

## Inner Classes
- **Static inner classes** can be accessed without an outer class instance.  
- **Non-static inner classes** require an instance of outer class.

```java
class Outer {
    static class Inner {
        void msg() {
            System.out.println("Inside static inner class");
        }
    }
}

public class TestInner {
    public static void main(String[] args) {
        Outer.Inner obj = new Outer.Inner();
        obj.msg(); // Inside static inner class
    }
}
```

---

## Singleton Class
### Theory
- Ensures **only one instance of a class exists**.  
- Useful for **config, logging, or shared resources**.

### Code
```java
class Singleton {
    private static Singleton instance;

    private Singleton() {}

    public static Singleton getInstance() {
        if(instance == null) {
            instance = new Singleton();
        }
        return instance;
    }

    void showMessage() {
        System.out.println("Singleton instance called!");
    }
}

public class TestSingleton {
    public static void main(String[] args) {
        Singleton obj1 = Singleton.getInstance();
        Singleton obj2 = Singleton.getInstance();
        obj1.showMessage(); // Singleton instance called!
        System.out.println(obj1 == obj2); // true
    }
}
```

---

## Outro
- Covered **Packages, Static members, Inner Classes, and Singleton pattern**.  
- Understanding these helps **organize code, share data efficiently, and control object instances**.