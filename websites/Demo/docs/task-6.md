# PHP Security

## Always Use HTTPS

### What is HTTPS?
 - `HTTPS` (HyperText Transfer Protocol Secure) is the secure version of `HTTP`.
 - It uses SSL/TLS encryption to protect data transmitted between the user and the server.

### Why is HTTPS Important?
 - Encrypts sensitive data (passwords, credit cards, personal info).
 - Prevents attackers from intercepting data (Man-in-the-Middle attacks).
 - Ensures data integrity (data is not modified during transfer).
 - Builds user trust (secure connection in browser).

### Risks of Using HTTP
 - If your website uses HTTP instead of HTTPS:
 - Data is sent in plain text 
 - Attackers can steal login credentials
 - Vulnerable to session hijacking
 - Users may see “Not Secure” warning in browser

*SO* Always use `HTTPS`

---
## Protect Directory with Firewall
### What Does It Mean?
 - restricting unauthorized access to sensitive parts of your application (like admin panels, config files, or private data folders) using security rules.
 - A firewall (or Web Application Firewall - WAF) filters incoming traffic and blocks malicious requests before they reach your server.

## Why is It Important?
 - Prevents unauthorized access to sensitive directories
 - Blocks malicious requests (bots, hackers)
 - Protects against common attacks (brute force, scanning)
 - Adds an extra security layer beyond application code

---
## Protect Directory with IP
### What Does It Mean?
 - allowing access only to specific IP addresses and blocking all other users.
 - This is commonly used to secure sensitive areas like admin panels or internal tools.

### Why is It Important?
 - Limits access to trusted users only
 - Prevents unauthorized access
 - Adds an extra layer of security
 - Reduces risk of attacks on sensitive pages

### How to Protect Directory by IP
- *EX:*

```php

Order Deny,Allow
Deny from all
Allow from 192.168.1.1

```
---
## Prevent Executing Specific Files
### What Does It Mean?
 - blocking certain file types (like .php, .exe, .sh) from being executed on the server, especially in directories like uploads.
 - This helps protect your application from attackers uploading and running malicious scripts.

### Why is It Important?
 - Prevents execution of malicious files
 - Secures upload directories
 - Protects against Remote Code Execution (RCE)
 - Reduces risk of server compromise

### How to Prevent File Execution

```php

<FilesMatch "\.(php|rb|py|inc|txt)$">
Order allow,deny
Deny from all
</FilesMatch>

```
---

## Securing Uploads
- Uploading files is one of the most dangerous features in web applications if not handled properly.
- Attackers can upload malicious files to execute code or damage the system.

1. Rename File (Add Complexity)
   #### Why?
     - Prevents overwriting existing files
     - Makes file names unpredictable
     - Reduces risk of direct access

2. Check File Extension
   #### Why?
     - Blocks dangerous file types like .php, .exe
     - Allows only safe extensions

3. Check File MIME Type
    #### Why?
     - Prevents fake extensions (e.g., .jpg but actually PHP file)
     - Verifies real file type

4. Check File Size
   #### Why?
     - Prevents large file uploads (DoS attacks)
     - Saves server storage
---
## Fix Error Logs
- it means managing how errors are displayed and logged in your application.
- ### Why is It Important?
   - Prevents leaking sensitive information (paths, database queries, credentials)
   - Protects against attackers gaining system details
  - Helps developers debug issues safely
  - Improves application stability

```php
<?php
ini_set('display_errors', 1);
error_reporting(E_ALL);
?>
```
---
## Backend Validation
- ### What is Backend Validation?
    - Backend validation is the process of validating and checking user input on the server side before processing it or storing it in the database.
    - Even if validation is applied on the frontend, backend validation is still required because client-side validation can be bypassed.
- ### Why is It Important?
  - Prevents malicious or invalid data from entering the system
  - Protects against common attacks (like SQL Injection, XSS)
  - Ensures data integrity and correctness
  - Cannot be bypassed like frontend validation
- *EX*
```PHP
<?php
$email = $_POST['email'];

if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
    die("Invalid email format");
}
?>
```
---
## Prevent Session Fixation

- Session Fixation is an attack where the attacker sets or knows a user’s session ID before login, then uses the same session after the user authenticates to gain access.

### Why is It Dangerous?
 - Allows attackers to hijack user sessions
 - Gains unauthorized access to accounts
 - Bypasses authentication after login
 - How to Prevent Session Fixation

```PHP
<?php
session_start();
session_regenerate_id(true);
?>
```