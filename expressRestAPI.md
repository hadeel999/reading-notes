# Express REST API

## Review: ES6 Classes
Classes are a template for creating objects. 
### To declare a class:
![defineClass](https://user-images.githubusercontent.com/103508563/170985466-38869197-699b-4747-93db-5bd4bf2310cc.PNG)

#### Class expressions:
It is another way to define a class.
![defineClass1](https://user-images.githubusercontent.com/103508563/170986295-a51ebd6e-9149-4a90-ab14-8d3daaa56846.PNG)
#### Methods definitions:
![defineClass2](https://user-images.githubusercontent.com/103508563/170986946-f6095089-e687-4e85-b246-b0018c436526.PNG)


## Using Express Routing
Routing refers to how an application’s endpoints (URIs) respond to client requests.

### Route methods:
GET, POST(add), PUT(update), DELETE, ALL(for all HTTP request methods on the same path).
We can use them like: `app.get('path',handlePathFun);`.

## Express Routing
Router is like a mini-Express application.
Router doesn’t bring in views or settings but provides us with the routing APIs like:
- `.use`
- `.get` 
- `.params`
- `.route` 

### With Express Router we can:
- Use `express.Router()` multiple times to define groups of routes.
- Apply the `express.Router()` to a section of our site using `app.use()`.
- Use route middleware to process requests.
- Use route middleware to validate parameters using `.param()`.
- Use `app.route()` as a shortcut to the Router to define multiple requests on a route.
