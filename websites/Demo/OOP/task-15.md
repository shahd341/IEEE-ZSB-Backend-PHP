# Research Questions

## 1. Inheritance

- Inheritance means that a child class can take properties and methods from a parent class.

*Main benefit:*
- It helps us reuse code instead of writing the same code again.

**Example:**
```php
<?php
class Animal {
    public function eat() {
        echo "Animal is eating";
    }
}

class Dog extends Animal {
    public function bark() {
        echo "Dog is barking";
    }
}
?>
```
---

## 2. The `Final` Keyword

### What happens if you put the `final` keyword before a class or a method? 

If we use `final` with a class:
-  No other class can inherit from it.

If we use `final` with a method:

- The method cannot be overridden in child classes.

### Why we use it:
- To protect the code and prevent changes.

Example:
```php
<?php
final class Animal {
    // code
}
?>

```
---

## 3. Overriding Methods

Overriding means writing the same method in the child class but with a different behavior.

**Example:**
```php
<?php
class Animal {
    public function sound() {
        echo "Animal sound";
    }
}

class Dog extends Animal {
    public function sound() {
        echo "Dog barks";
    }
}
?>
```
Calling parent method:
```php
parent::sound();
```
---

## 4. Abstract Class vs Interface

*Abstract Class:*

- Can have normal methods and abstract methods
- Can have variables

**Example:**
```php
<?php
abstract class Animal {
    abstract public function sound();
}
?>
```
*Interface:*

- Only has method declarations (no implementation)

**Example:**
```php
<?php
interface Animal {
    public function sound();
}
?>
```
Main difference:
- Abstract class can have some implementation, but interface cannot.

### Can a class implement multiple interfaces?
Yes, it can.

---

## 5. Polymorphism

- Polymorphism means one method can have different behaviors depending on the object.

**Example:**
```php
<?php
class Dog {
    public function sound() {
        echo "Dog barks";
    }
}

class Cat {
    public function sound() {
        echo "Cat meows";
    }
}
?>
```
---