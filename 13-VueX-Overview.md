# VueX Overview

The `store` folder contains the store and all store module for the application. There is no manual configuration, once a file is created within this folder Nuxt automates the configuration.

A store with a single file uses `index.js` and contains:

- **state**: Function
- **mutations**: Object
- **actions**: Object
- **getters**: Object

Here is the layout of a single file store:

```js
// holds your root state
export const state = () => ({
  counter: 0,
});

// contains your actions
export const actions = {
  counterUp({ state, commit }) {
    commit("setCounter", state.counter + 1);
  },
};
// contains your mutations
export const mutations = {
  setCounter(state, value) {
    state.counter = value;
  },
};
// your root getters
export const getters = {
  myGetter(state) {
    return state.counter + 1000;
  },
};
```

There is a core process most workflows follow when updating the store:

1. A function is called from a component (to update some data) `dispatching` a function within `actions`, this where any async code runs that interacts with API's and where any further logic is done in order to itemize changes in the store
2. Once the db has been updated or new data received successfully any changes to the store are `committed` to `mutations`.
3. `mutations` directly updates the data within the store

The above overview is a broad stroke but essentially aims to maintain synchronization between the db and the store by consistently reconciling any changes.

This way the store is the single source of truth for the client and the whole application is working with the same current data.

## Modules

The store can be structured depending on the size of the application and provisions for scalability. With that in mind it is good practice to separate data that is used in different parts of the application into namespace modules. This makes it easier to manage as an application grows.

For horizontally large applications a good approach is to use `single file modules`, this is where each file is a module and contains **state**, **mutations**, **actions** and **getters**. This is a nice way to work as the workflow is all in one place.

For vertically large applications where there are many workflows for data within a single module we can give the module a folder and break each: **state** **mutations** **actions** and **getters** out into their own files.

## Accessing data within Components

One way to access data within a component is to use a computed property within the component where the data is to be used. The below example assumes there is a module named `cart` and a property within the state called `counter`. this is how to access the `counter` within its module:

```js
computed:{
  counter(){
    return this.$store.state.cart.counter
  }
}
```

## Update the state within a Module

For example a user deletes a blog post, a click event triggers a function within that component that has the below logic which dispatches to a function within actions:

```js
this.$store.dispatch("blog/deletePost", post);
```

Above: The first argument is the path to the function, `blog` is the module, `deletePost` is the function within `actions` and the second argument is the post to be deleted, this is accessed by passing it into the callback on the click event.

## Conclusion

- **dispatch** to `actions` > **commit** to `mutations` > **Set-data** to update the `state`

- We use **getters** to access dynamic data within components, this way when the data is updated within the store it is also re-rendered to the DOM
