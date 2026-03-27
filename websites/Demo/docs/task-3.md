# The Documentation

## Resourceful Naming Conventions

- Use clear and meaningful names for controllers
- Follow a consistent naming pattern
 - *EX:*
  - `index`-> display all resources
  - `create` -> show create form
  - `store` -> save new data
  - `show` -> display single item
  - `edit` -> show edit form
  - `update` -> update data
  - `delete` -> remove data

---

## Namespacing: What, Why, How? 
- Namespaces prevent class name conflicts
- Used to organize project structure
- *EX*

``` php 
<?php

namespace Core;
```
---
## Autoloading

- Autoloading is a mechanism that automatically loads PHP classes when they are needed, instead of manually including files using `require` or `include`
- *EX*
```PHP

spl_autoload_register(function ($class) {
     $class = str_replace('\\', DIRECTORY_SEPARATOR, $class);
     require basePath("{$class}.php");
     });

```
---

## Helper Functions

- `base_path()` 
   - is a helper function used to get the root (base) path of the project directory.
   - *EX*
    ```PHP

   // core/functions.php

   function basePath(string $path): string
    {
     return BASE_PATH . '/' . $path;
    }
    ```
- `view()`
   - *EX* 
   ```PHP
     // Core/functions.php

    function view(string $path, array $attributes = []): void
    {
    extract($attributes);
 
    require base_path("views/{$path}");
   } 

   ```
---
##  Advanced Routing
- Advanced Routing is the process of handling and organizing application routes in a more flexible and structured way.
- *EX*
```PHP
<?php

namespace Core;

use Core\Middleware\Middleware;

class Router {
    protected $routes = [];

    protected function add($uri, $controller, $method) {
       $this->routes[] = [
            'uri' => $uri,
            'controller' => $controller,
            'method' => $method,
            'middleware' => null
        ];

        return $this;
    }

    public function only($key) {
        $this->routes[array_key_last($this->routes)]['middleware'] = $key;
        
        return $this;
    }

    public function get($uri, $controller) {
        return $this->add($uri, $controller, 'GET');
    }

    public function post($uri, $controller) {
        return $this->add($uri, $controller, 'POST');
    }

    public function delete($uri, $controller) {
        return $this->add($uri, $controller, 'DELETE');
    }

    public function patch($uri, $controller) {
        return $this->add($uri, $controller, 'PATCH');
    }

    public function put($uri, $controller) {
        return $this->add($uri, $controller, 'PUT');
    }

    public function route($uri, $method) {
        foreach ($this->routes as $route) {
            if ($route['uri'] === $uri && $route['method'] === strtoupper($method)) {
                Middleware::resolve($route['middleware']);

                return require base_path($route['controller']);
            }
        }

        $this->abort();
    }

    protected function abort($code = 404) {
        http_response_code($code);

        require base_path("views/{$code}.php");

        die();
    }
}
```
- The convenience methods ->`POST()`, `GET()`, `DELETE()`, `patch()`, and `put()` 
- *EX*
```PHP

<form method="POST" action="/notes">
    <input type="hidden" name="_method" value="DELETE">
    <input type="hidden" name="id" value="<?= $note['id'] ?>">
    <button type="submit">Delete</button>
</form>

```
---
## Updated `routes.php`

- `routes.php` after update

```PHP
<?php

$router->get('/', "controllers/index.php");
$router->get('/about', "controllers/about.php");
$router->get('/contact', "controllers/contact.php");

$router->get('/notes', "controllers/notes/index.php")->only('auth');
$router->get('/note', "controllers/notes/show.php");
$router->delete('/note', "controllers/notes/destroy.php");

$router->get('/note/edit', "controllers/notes/edit.php");
$router->patch('/note', "controllers/notes/update.php");

$router->get('/notes/create', "controllers/notes/create.php");
$router->post('/notes', "controllers/notes/store.php");

$router->get('/register', "controllers/registration/create.php")->only('guest');
$router->post('/register', "controllers/registration/store.php")->only('guest');

$router->get('/login', "controllers/session/create.php")->only('guest');
$router->post('/session', "controllers/session/store.php")->only('guest');
$router->delete('/session', "controllers/session/destroy.php")->only('auth');

```
---

