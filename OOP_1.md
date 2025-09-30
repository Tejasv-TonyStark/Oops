# Object-Oriented Programming (Java Basics)

## 1. OOPS (Object-Oriented Programming)
- Object-Oriented Programming is based on the concept of **classes** and **objects**.  
- Classes define the structure (logic), while objects represent real instances.  

---

## 2. Class
- A **class** is a logical construct that contains **properties (variables)** and **methods (functions)**.  
- Classes usually start with a **capital letter** by convention.  
- Classes themselves do not occupy memory for instance variables.  
- **Static members** of a class occupy memory even without objects.

---

## 3. Object
- An **object** is an instance of a class.  
- Objects are stored in **heap memory**.  
- To access what is inside a class, we must create an object.  
- **Keyword `new`** is used to create objects.  
- Objects occupy dynamic memory (allocated at runtime).  

---

## 4. Variables
- **Instance Variables**: Variables declared inside a class, tied to each object.  
- **Reference Variables**: Variables that point to objects. They are stored in the stack memory.  

---

## 5. Constructors
- A **constructor** initializes the object.  
- It is a special function with:
  - No return type.  
  - The same name as the class.  
- Types of constructors:  
  - Default constructor (no arguments, created automatically if none is provided).  
  - No-argument constructor (explicitly defined with no parameters).  
  - Parameterized constructor (accepts arguments).  
- **Purpose**: Initializes object variables with specific values.  

---

## 6. `this` Keyword
- Refers to the current object.  
- Used to distinguish between instance variables and parameters with the same name.  
- Ensures each object is initialized with its own values.  
- Can be used to:
  - Call another constructor in the same class (`this(...)`).  
  - Access fields and methods of the current object.  
  - Return the current object.  
  - Pass the current object as a parameter.  

---

## 7. Object Assignment
- If one object is assigned to another, both reference variables point to the same object.  
- Example:  
  ```java
  A obj1 = new A();
  A obj2 = obj1;  // both refer to the same object
  ```
- The old reference becomes lost if reassigned, and the object is eligible for garbage collection.  

---

## 8. Garbage Collection
- Java automatically removes unused objects from memory.  
- When no reference exists for an object, it becomes eligible for garbage collection.  
- The `finalize()` method was used earlier, but it is now deprecated.  

---

## 9. `final` Keyword
- Used to restrict changes.  
- For **primitives**: value cannot be modified.  
- For **objects**: reference cannot point to a new object, but internal fields of the object may still change.  

---

## 10. Wrapper Classes
- Wrapper classes provide an **object representation of primitives**.  
- Examples: `Integer`, `Double`, `Character`, etc.  
- Allow use of methods and properties (e.g., `Integer.MAX_VALUE`).  
- **Autoboxing**: automatic conversion from primitive to wrapper.  
- **Unboxing**: automatic conversion from wrapper to primitive.  
- Java is always **pass by value**:
  - Primitive values: actual value is copied.  
  - Object references: reference value (address) is copied.  
- Because of this, swapping values using wrapper classes does not work.

- class Box { int value; }

public class Test {
    static void change(Box b) {
        b.value = 100;     // (1) modifies the original
        b = new Box();     // (2) reassign local reference
        b.value = 200;     // (3) modifies the new object
    }

    public static void main(String[] args) {
        Box box1 = new Box();
        box1.value = 10;
        change(box1);
        System.out.println(box1.value);
    }
}

box1.value = 10 → box1 → {value=10}.

change(box1) → local b is created, pointing to the same {value=10}.

b.value = 100 → now {value=100} (affects both box1 and b).

b = new Box() → local b now points to a new object {value=0}.

b.value = 200 → changes the new object to {value=200}.

But box1 is still pointing to the old object {value=100}.

Method ends → b disappears, leaving only box1 → {value=100}.
