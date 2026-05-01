# Research Questions 

## 1. MVC and Database Access
In the MVC pattern, the Model is the only part that should talk directly to the database.  
This is because the Model is responsible for handling data and business logic. Keeping database access inside the Model makes the code more organized, easier to manage, and more secure. It also prevents other parts like the View or Controller from mixing UI with data logic.

## 2. Storing Sensitive Information
Sensitive information like database passwords should be stored in a separate configuration file instead of writing it directly in the code.  
This is important because:
- It improves security (less chance of exposing passwords)
- It makes it easier to change settings without editing the whole project
- It helps when uploading code to public repositories like GitHub

## 3. What is PDO in PHP?
PDO (PHP Data Objects) is a way to connect to databases in PHP.  
It is preferred over older methods like mysqli because:
- It supports multiple types of databases (not just MySQL)
- It is more secure
- It works well with prepared statements
- It makes the code cleaner and easier to reuse

## 4. Prepared Statements and SQL Injection
Prepared Statements help protect websites from SQL Injection attacks.  
They work by separating the SQL query from the user input. This means even if a user enters harmful input, it will be treated as data, not as part of the SQL command. So attackers cannot change the query or access unauthorized data.

## 5. Fetching One Row vs Multiple Rows
Sometimes we only need one row from the database. For example, when a user logs in, we fetch only their account data using their email or ID.  

Other times we need multiple rows. For example, when showing a list of products in an online store, we fetch all products, so we get an array of many rows.

