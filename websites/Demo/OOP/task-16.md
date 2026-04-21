# Research Questions 

## 1. Traits

- **The Problem**: PHP does not support multiple inheritance, which means a class cannot extend more than one class.
Traits solve this problem by allowing us to reuse code from multiple sources.

- A trait is like a small piece of code (methods) that we can include inside a class using the `use` keyword.

**How Traits Solve It:**
-  Traits are essentially "partial classes" that can be inserted into other classes. Think of them as a way to "copy and paste" code horizontally. A single class can use multiple traits, effectively bypassing the single inheritance limit.

**When to use Traits:**

- When you want to share the same methods between multiple classes
- When inheritance is not suitable or possible

---

## 2. Namespaces

- A Namespace in PHP is a way to organize code and avoid naming conflicts.

- **Preventing Collisions:**  Sometimes, you may have two classes with the same name but in different files. This can cause a problem called "naming collision".

   -Namespaces solve this by giving each class a unique path.
---

## 3. Autoloading

- Before autoloading, developers had to manually include every file using `require` or `include`.

- Autoloading automatically loads the required class file when you use the class.

### How it Saves Time:
 -  **Automation**: You no longer need to write hundreds of require or include statements at the top of your files.
 -  **Performance**: It only loads the files your script actually uses during that specific execution, rather than loading every single file in your project.

---

## 4. Magic Methods (`__get` and `__set`)

- Magic methods are special methods in PHP that are automatically called in certain situations.

`__get`:

- Used when trying to access a private or undefined property

`__set`:

- Used when trying to assign a value to a private or undefined property

### When are they automatically triggered?
 - They are triggered automatically whenever you try to access (`$obj->property`) or assign a value to `($obj->property = 'value')`a property that the script cannot normally see.

- These methods help control how properties are accessed and modified.

---

## 5. Static Methods and Properties

- When a method or property is declared as static, it belongs to the class itself, not to an object.

- You do **NOT** need to create an object using new
- you can access them without creating an object. You use the Scope Resolution Operator (`::`) instead of the arrow operator (`->`).

Ex
```php
ClassName::methodName();
```
- Static is useful when the function does not depend on object data.

---