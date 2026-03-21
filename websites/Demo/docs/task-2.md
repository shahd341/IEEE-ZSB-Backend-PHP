# The documentation 

## Database  Table & Index

- *Table Creation*: we design a `notes` table with a primary key and a `body` field (set to `text` type, not nullable).
- *Database Integrity*: we create a `users` table with a unique index on the `email` column to prevent duplicate accounts.
- *Relationships*: Establishing a foreign key constraint to link notes to specific users, enabling cascading deletes.
      - `on delete cascade` ->(if a user is deleted, their notes are also removed).

---

## Authorization

- Authorization is the process of checking if a user has permission to access a specific resource.

- If a user tries to access something they are not allowed to, the system should prevent it.

- *Error Handling*: Implementing a `403` Forbidden status code if a user tries to access a note they do not own.
   - The difference between `404` and `403`
     - `404`
       -  it means the page does not exist.
      
     - `403` 
         - it means the page Forbidden.


---
## Validation

- *Purpose*: To prevent empty or incorrect data from being submitted to the database, *ensuring data integrity*
- ### Why is Validation important?
  - It prevents invalid or empty data.
  - It improves application security.
  - It protects the database from incorrect input.

- *Security Check*: we use `htmlspecialchars()` to escape untrusted user input and prevent XSS vulnerabilities
- *EX*

```PHP
<?php foreach ($notes as $note) :  ?>
                <li>
                    <a href='/note?id=<?= $note['id'] ?>' class="text-blue-500 hover:underline">
                        <?= htmlspecialchars($note['body']) ?>
                    </a>
                </li>
            <?php endforeach; ?>
```           
