# PHP Basics and Concepts 

## Basic PHP Syntax :
- A PHP script starts with `<?php` and ends with `?>`
- A PHP file normally contains some HTML tags and some PHP scripting code
  - *EX*
  ```PHP
  <!DOCTYPE html>
  <html>
  <body>

  <h1>PHP</h1>

  <?php
   // code
  ?>

  </body>
  </html>
  ```

- All PHP statements end with a semicolon (`;`).
- We use `echo` or `print` to display data
  - `echo` output one or more strings
  - `print` output only one string

```php
  - *EX*
  ```PHP
   <?php
   echo 'Hello World!';
   echo "Hello", " ", "World";
   print "Hello World";
   ?>
   ```

- PHP keywords are not case-sensitive, meaning we can write them in uppercase or lowercase.

   - *EX*
   ```PHP
    echo "Hello";
    ECHO "Hello";
   ```

   **However**, variable names are case-sensitive.

  - *EX*

    `$book` not equal `$Book`

- We use `//`or `#` or `/* */` to make comment in php
  - for single line comment we use `//` OR `#`
  ```PHP
  <?php
  //This is a single line comment
  #This is a single line comment too
  echo 'Shahd Ahmed'; // AND THIS
  ?>
  ```
  - for multi line comments we use `/* */`
  ```PHP
  <?php
  /*
  This is a multi line comment 
  in
  php
  */
  echo "Hello Shahd";
  ?>
  ```
**Note**
  - To concatenate strings in PHP, we use the dot (`.`) operator.
    - *EX*
    ```PHP
    <?php
    echo "Hello, " . "World";
    ?>
    ```
  
---
## Variables in PHP

- All variable names must start with a dollar sign (`$`) followed by the name of the variable.
- Variable names are case-sensitive.
- We use the `=` operator to assign a value to a variable
- Variable names must start with a letter or underscore.
- Variable names can not start with a number.

  - *EX*

  ```PHP
  <?php
  $var = 'shahd';       //valid
  $Var = 'ahmed';      //valid
  $_var = 'ramzy';    //valid
  $1var = 'mahmoud'; //invalid
  ?>
  ```
**Note**
- There is a difference between single quotes versus double quotes and that difference is -> if you want to nest and evaluate a variable within a string ,you have to use double quotes not single quotes        

   >because 
->In PHP, variables inside `double quates` are interpreted and their values are displayed.However, variables inside `single quotes` are treated as plain text. 

  - *EX*
   ```PHP
    <?php

     $name = "Shahd";

     echo "Hello $name"; // Output: Hello Shahd
     echo 'Hello $name'; // Output: Hello $name
    ?>
   ```
---
## Conditionals and Booleans
- Conditionals allow the program to execute different code depending on whether a condition is true or false.
   - *EX*
   ```PHP
    <?php
     $score = 85;

   if ($score >= 50) {
    echo "Successful";
   } 
   else { 
    echo "Unsuccessful";
   }
   ?>
   ```
---
## Array
- in PHP, Array is used to store multiple values in a single variable.
- We can access the values by using their index or key.
- ## There are types of array
   1. `Indexed Array`     -> use index to access the values
   2. `Associative Array` -> use key to access the values (like map)
   3. `Multidimensional Arrays` -> Arrays containing one or more arrays
### Indexed Array  

```PHP
<?php

$colors = ["red", "blue", "green"];
$fruits = array("apple", "banana", "cherry");
# TO accesss
echo $fruits[0]; 
echo $colors[1];   

?>
```
### Associative Array
```PHP
<?php

$person = ["first_name" => "Shahd",
           "age" => 20, 
           "id" => "123"];

// to access
echo $person["first_name"];
?>
```
### Multidimensional Arrays
```PHP
<?php

$person = [[ "first_name" => "Shahd","age" => 20 ], 
           [ "first_name" => "Rahma","age" => 21 ]];

// to access
echo $person[0]["first_name"];
?>
```
---
## Loops 

- loops are used to execute a block of code multiple times.
- The `foreach` loop is used to iterate over arrays.
  - It allows us to access each element in the array one by one.

```php 
<?php

$colors = ["red", "blue", "green"];

foreach ($colors as $color) {
    echo $color . " ";
}
?>

```


---
## Functions
- Functions are reusable blocks of code that perform a specific task.
- To declare a function in PHP, we use the `function` keyword.
- *EX*
   ```PHP
   function message() {
    echo "Hello world";
   }
   // to call the function
    message();
   ```
---
## Lambda Functions (Anonymous Functions)
- A lambda function is a function without a name.
- It can be stored in a variable.
```php

    $filteredBooks = filter($books, function ($book) {
        return $book['releaseYear'] <= 2000;
    });

```
---

## Superglobals 
- Built-in variables that are always available in all scopes
- Superglobals are variables that are accessible from any script or from any file 
- *EX*
  -  `$SERVER` -> contains information about the web server.
    ```php
    echo "<pre>";
    var_dump($_SERVER);
    echo "</pre>";
    ```
   
**Note**
  - When we use `die()` nothing after that function will be executed.
---
