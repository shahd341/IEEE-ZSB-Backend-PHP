# Reasearch Questions

## 1. Class vs Object
- A **Class* is like a `blueprint` or a `plan` that we use to create things, while an *Object* is the `actual thing` that is created from that blueprint.

- *EX*
A Class as the recipe for making a cake.
The Object is the real cake you bake using that recipe.

*So*, we can say:
- class is a blueprint that you can ctreate object from
- object is a member in the main application 
- *Note*
  -  one class can create many objects, and each object can have different values but follows the same structure.

---
## 2. `$this` vs `self::`

**`$this`**
- refer to current object (the real instance)
- access non static members
- use `$` because it represent a variable 
- **EX** ```php  $this->name ```

**`self::`**
- refer to current class (the blueprint itself)
- access static members
- not use `$` because it is not represent a variable but represent class construction
- **EX** ```php self::$count ```

### When do you use one over the other?
- when we want to access properties or methods of this specific object , we use `$this` 
- when we want to call static methods or static properties , we use `self::` 

---
## 3. Access Modifiers (Encapsulation)

|modifier|who can access|
|:------:|:------------:|
|public|everyone(outside class + inside class)|
|protected|only the class itself + child classes|
|private|only inside the same class|

### Why make a property private?
- Making it private protects the data. You can only change it through safe methods 

---
## 4. Typed Properties: 
### mWhat are Typed Properties in PHP?
- Typed Properties in PHP allow you to explicitly declare the data type a class property is permitted to hold
- Typed Properties = giving a property a specific data type.

### How do they help prevent bugs compared to declaring properties without a type?
- Without type 
```php public $age;  ``` -> anyone can put string, intger, float....

- With type:
   - PHP automatically checks the type.
   - If someone tries to put wrong data (e.g. string in $age), PHP shows an error immediately.
   - Much safer and less debugging time.

--- 
## 5. Constructor Methods: 
- The `__construct()` method is a special function that runs automatically the moment you create a new object.
- It is used to initialize object properties with values directly when the object is created.
### Why is it useful?
  - You can pass values directly when creating the object.
  - You can set up the object with all needed data from the beginning.
  - Cleaner code (no need to set properties one by one after creating the object).

### Why is it useful to pass arguments into a constructor when creating a new object?
- Passing arguments into the constructor is useful because it allows us to set initial values easily instead of assigning them one by one after creating the object.
- For example, we can create an object and pass name and age directly, and the constructor will assign them automatically. This makes the code cleaner and faster.