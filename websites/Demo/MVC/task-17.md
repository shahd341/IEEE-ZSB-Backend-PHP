# Web Development Concepts Answers

## 1. The MVC Pattern
MVC stands for **Model, View, Controller**.

- **Model:** Handles the data and logic of the application (like database operations).
- **View:** Responsible for displaying data to the user (UI / interface).
- **Controller:** Acts as a middle layer. It receives user input, processes it, and tells the Model and View what to do.

---

## 2. Routing
A **Router** is like a traffic cop for a website.

- It checks the URL requested by the user.
- It decides which part of the application should handle the request.

**Example:**
- `/home` → goes to Home page  
- `/users` → goes to Users page  

---

## 3. The Front Controller
The **Front Controller** means using a single file (usually `index.php`) to handle all requests.

Instead of having many separate files like:
- `about.php`
- `contact.php`

All requests go through **one file**, and it decides what to do.

**Benefits:**
- More organized code  
- Easier to manage  
- More secure  

---

## 4. Clean URLs
Websites use clean URLs like:

example.com/users/profile

Instead of messy URLs like:

example.com/index.php?page=users&action=profile

**Why?**
- Easier to read  
- Look more professional  
- Better for SEO (search engines)  
- Easier to remember  

---

## 5. Separation of Concerns
Putting SQL (database queries) directly inside HTML is a bad idea because:

- It mixes logic with design  
- Makes code hard to read and maintain  
- Harder to debug  
- Not secure  

**Best practice:**
- SQL → in Model  
- HTML → in View  

This keeps the code clean and well organized.