# MVC Architecture: Questions and Answers

## 1. The Controller's Job
When a user clicks a "View Profile" button, the **Controller** acts as the middleman. It performs the following steps:
- **Intercepts the Request:** It receives the specific URL request from the server.
- **Communicates with the Model:** It asks the Model to fetch the specific user's data from the database.
- **Handles Logic:** It processes any necessary logic (like checking if the user exists or has permission to view the profile).
- **Selects the View:** Once it has the data, it picks the appropriate View template and passes the data to it.
- **Returns the Response:** Finally, it sends the rendered HTML back to the user's browser.

---

## 2. Dynamic Views vs. Static HTML
- **Static HTML:** These files are fixed. Every user who visits the page sees the exact same content because the code is hard-coded and cannot change unless a developer manually edits the file .
- **Dynamic PHP View:** These are template files that use placeholders. They can change their content based on the data sent by the Controller. For example, a single "Profile" view can show different names and photos for thousands of different users.

---

## 3. Data Passing
A Controller passes data to a View by providing a **variable or an array** as a second argument to the `view()` function.
- In frameworks like Laravel, you fetch data (e.g., `$user = User::all();`) and then `return the view using return view('profile', ['user' => $user]); `.
- Inside the View file, you can then access this data using template engines (like Blade) to echo the variables directly into the HTML.

---

## 4. Templating (Headers & Footers)
The MVC structure uses **Layouts** to avoid code duplication.
- Instead of copying the navigation bar to every file, you create a "master" layout file (e.g., `app.blade.php`) containing the header and footer.
- You use a directive like `@yield('content')` in the master file to mark where unique page content should go.
- Individual pages then "extend" this master layout, meaning they only need to write the unique content for that specific page, and the header/footer are automatically included.

---

## 5. Logic in Views
Placing complex logic (like heavy loops or database queries) inside a View is considered bad practice because:
- **Violates Separation of Concerns:** The View's only job should be **presentation** (how things look).
- **Difficult to Maintain:** If you need to change how data is calculated, you would have to search through many HTML files instead of one Controller or Model.
- **Readability:** Mixing heavy PHP logic with HTML makes the code messy and harder for designers to work on.