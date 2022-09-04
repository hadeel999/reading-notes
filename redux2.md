# Redux - Combined Reducers
The most common state shape for a Redux app is a plain Javascript object containing "slices" of domain-specific data at each top-level key. Similarly, the most common approach to writing reducer logic for that state shape is to have "slice reducer" functions, each with the same `(state, action)` signature, and each responsible for managing all updates to that specific slice of state. Multiple slice reducers can respond to the same action, independently update their own slice as needed, and the updated slices are combined into the new state object.

### There are several important ideas to be aware of when using combineReducers:

- First and foremost, `combineReducers` is simply a utility function to simplify the most common use case when writing Redux reducers.

- While Redux itself is not opinionated about how your state is organized, combineReducers enforces several rules to help users avoid common errors.

- One frequently asked question is whether Redux "calls all reducers" when dispatching an action. Since there really is only one root reducer function, the default answer is "no, it does not". However, `combineReducers` has specific behavior that does work that way.

- You can use it at all levels of your reducer structure, not just to create the root reducer. It's very common to have multiple combined reducers in various places, which are composed together to create the root reducer.

### [Multiple Reducers Example](https://www.youtube.com/watch?v=gBER4Or86hE)


### References:

[Redux Docs: Using Combined Reducers](https://redux.js.org/usage/structuring-reducers/using-combinereducers/)

[Redux Docs: Combined Reducer Syntax](https://redux.js.org/api/combinereducers/)

### [Home Page](./README.md)
