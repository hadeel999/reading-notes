# Redux - Asynchronous Actions

So far, all the data we've worked with has been directly inside of our React+Redux client application. However, most real applications need to work with data from a server, by making HTTP API calls to fetch and save items.

## Example REST API and Client

To keep the example project isolated but realistic, the initial project setup already included a fake in-memory REST API for our data (configured using the Mirage.js mock API tool). The API uses `/fakeApi` as the base URL for the endpoints, and supports the typical `GET/POST/PUT/DELETE` HTTP methods for `/fakeApi/todos`. It's defined in `src/api/server.js`.

The project also includes a small HTTP API client object that exposes `client.get()` and `client.post()` methods, similar to popular HTTP libraries like `axios`. It's defined in `src/api/client.js`.

We'll use the `client` object to make HTTP calls to our in-memory fake REST API for this section.

## Redux Middleware and Side Effects

Earlier, we said that Redux reducers must never contain **side effects**. A **side effect is any change to state or behavior that can be seen outside of returning a value from a function**. Some common kinds of side effects are things like:

- Logging a value to the console.
- Saving a file.
- Setting an async timer.
- Making an AJAX HTTP request.
- Modifying some state that exists outside of a function, or mutating arguments to a function.
- Generating random numbers or unique random IDs (such as `Math.random()` or `Date.now()`).

## [Thunk Middleware](https://github.com/reduxjs/redux-thunk)


### References:

[async actions](https://redux.js.org/tutorials/fundamentals/part-6-async-logic)


### [Home Page](./README.md)
