# PHP Website Security

## What is security ?
 - state of being protected or safe.

---
## PHP Security
 - if you want to protect your website 
   - Use framework [`Laravel` , `Symphony` , `YII`], .
   - Use Templates Engines [`Smarty` , `Plates`].
   - Update to the Latest Version.
   - Maintain the code.
   - Follow Exploits websites. like exploit-db.com
   - Follow Security Specialists.
   - Use Kali Linux when it comes to presentation testing.

---
## Why web Security ?

- websites are public.
- users add prrsonal information.
- knowledge and actions.
- takes years to be an expert.
- on going process.
- no absolute security.
- do not inconvenience real users.

> the only truly secure system is one that is powered off, cast in a block of concrete and put in a sealed room with armed guards, and even that may not be enough.

---
## What is a hacker?
- may start in the real world .

### Black hat types :
- Curios users.
- Script kiddie.
- Thrill seekers.
- Hacktivists.
- Trophy hunters.
- Proffesionals.

---
## What is Social Engneering?

- keep confidential information hidden.
- trash
- key logger
- publicly avialable infrommation e.g social media.
- password reset security questions.
- phishing.

---
# KEEP FUNCTIONAL CODE PRIVATE
- avoid directory listing -index -indexs
- private and public folders.
- always use php extensions.

---

## KEEP IT SIMPLE
- less points of entry.
- segemented code
- use OOP.

---
## `XSS` Filtering Input
- `XSS` -> Cross Site Scripting
- *EX:*
```PHP
<?php 
 if (isset($_GET['search'])):
   echo filter_var($_GET['search'], FILTER_SANITIZE_NUMBER_INT);
endif;
?>

```
## Prevent SQL Injection
- *EX:*
```PHP
<?php 

 if (isset($_GET['id']) && ! empty($_GET['id'])):

  $userid = filter_var($_GET['id'], FILTER_SANITIZE_NUMBER_INT);

  $stmt = $con->prepare("select * from `members` where id=?");

  $stmt->execute(array($userid));

  $count = $stmt->rowCount(); 

  while($row = $stmt->fetch()){

    $id = $row['id']
    $name = $row['name'];

  }

   if ($count > 0):
   echo $name;

   else:
   echo 'Theres no profile with this id'; 
   
   endif;

 else:
   echo 'profile id can not be empty'

 endif;

?>

```
## Prevent Remote File Injection
- Remote File Injection (RFI) is a vulnerability in PHP applications that allows an attacker to include and execute a remote file by manipulating input parameters.
- This usually happens when user input is directly passed to functions like:
`include()`
`require()`

- *EX:*
```PHP
<?php
  $page = $_GET['page'];
  include($page);
?>
```

### How to Prevent Remote File Injection
- Disable Remote File Inclusion in PHP Configuration
```php
allow_url_include = Off
allow_url_fopen = Off
```
--- 
## Good Password Hashing
- Password hashing is the process of converting a plain text password into a secure, irreversible string using a hashing algorithm.
- salt is a string added to a password before it is hashed
### Why is Hashing Important?
- Protects user passwords from being exposed.
- Prevents attackers from reading plain text passwords.
- Even if the database is leaked, hashed passwords are difficult to crack.

-*EX:*
```PHP 
<?php 
 
 $password='shahd';
 $goodpass= password_hash($password, PASSWORD_DEFAULT);
 echo $goodpass;

?>
```
-to verify password we use `password_varify`
-*EX:*

```PHP

 if (password_verify($password, $hash)) {
    echo 'Password is valid!';
} else {
    echo 'Invalid password.';
}

```