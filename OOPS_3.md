# Object-Oriented Programming (OOP) Notes

Some of the important topics for interviews are principles of Object-Oriented Programming. These include **Inheritance, Polymorphism, Encapsulation, Abstraction**.

## Principles of OOP

OOP allows us to reuse features of one class in another class through **Inheritance**.

Suppose we have 2 classes `A` and `B`. If `B` needs some important features of `A`, we use inheritance.

* Variables and methods of the **Parent class** can be accessed by the **Child class**.
* Child class **cannot access private members** of the parent class.
* In the main function, we **cannot declare a child reference with a parent object**, as the parent is unaware of the child.

**Example: Single Inheritance**

```java
class A {
    int x = 10;
    private int y = 20;

    void showX() {
        System.out.println("x = " + x);
    }
}

class B extends A {
    void show() {
        showX(); // ✅ Can access
        // System.out.println(y); // ❌ Cannot access private
    }
}

public class Main {
    public static void main(String[] args) {
        B obj = new B();
        obj.show();
    }
}
```

## Example: Box

```java
class Box {
    int length, width, height;

    Box(int l, int w, int h) {
        length = l;
        width = w;
        height = h;
    }

    int volume() {
        return length * width * height;
    }
}

class ColoredBox extends Box {
    String color;

    ColoredBox(int l, int w, int h, String c) {
        super(l, w, h); // Call parent constructor
        color = c;
    }

    void showColor() {
        System.out.println("Color: " + color);
    }
}

public class MainBox {
    public static void main(String[] args) {
        ColoredBox cb = new ColoredBox(2, 3, 4, "Red");
        System.out.println("Volume: " + cb.volume());
        cb.showColor();
    }
}
```

## Explanation

* Use **`super` keyword** to access parent class variables in the child constructor.
* `Object` class is the parent class to all classes in Java.
* Private members of the parent class cannot be accessed by the child class.
* In single inheritance, a child class inherits properties from only one parent class.
* In multiple inheritance, a child class can obtain properties from multiple parent classes. Java allows multiple inheritance via interfaces.

**Example: Multiple Inheritance via Interfaces**

```java
interface A {
    void featureA();
}

interface B {
    void featureB();
}

class C implements A, B {
    public void featureA() {
        System.out.println("Feature A");
    }

    public void featureB() {
        System.out.println("Feature B");
    }
}

public class Main {
    public static void main(String[] args) {
        C obj = new C();
        obj.featureA();
        obj.featureB();
    }
}
```

*This summary covers the key points from the notes for interview preparation, focusing on inheritance, access modifiers, and the use of `super` in Java.*
