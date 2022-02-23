# Overview

We can use different Nuxt fetch hooks depending on where the data is used within the app. For data that needs to be loaded on initial load and is used on multiple pages we want to load into the store. For data that is changed by the user within the db we also want this in the store. Some data is only used within one page or a single nested component. Some data is read only with a bit of client side filtering.

There are three basic hooks:

1. asyncData
2. fetch
3. nuxtServerInit

**Note**: All the above hooks have access to the `Nuxt context` and all it's properties as the first argument, except `nuxtServerInit` where the Nuxt context is the second argument as the `VueX context` in this case is the first argument.

## asyncData

asyncData runs on the server and grabs the data so the data can be pre-rendered with the HTML before the page is sent to the client. asyncData can be used within the script of a page, not within a nested component or file within plugins. This data is accessible within the `created()` and `mounted()` hooks within the page component.

asyncData is similar to the `data(){}` object in that data that is returned in the object is directly accessible in the template.

> asyncData can be run asynchronously with the use if async/await

## fetch

The fetch hook also triggers on the server-side but can be run from code within a page, component or a plugin. fetch is one option when we want to initially load data into the store.

The below example is within the script of the application landing page and loads all the required data into the store before using a computed property to pull the data into the page. This again is all pre-rendered:

**Note**: The store is accessed by destructing it from the context

**Note**: `fetch` runs on the server so we need to require `axios` to have access to it

```js
const axios = require("axios");
import { mapState } from "vuex";

export default {
  async fetch({ store }) {
    const response = await axios.get("uri");
    const data = response.data;

    store.commit("SET-DATA", data);
  },
  computed: {
     ...mapState({ "data" });
  }
//   'data' can now be used directly within the template
};
```

## nuxtServerInit

nuxtServerInit runs on the server-side and the code is located directly within `actions` within the `store`. This hook is a good option when loading data that is used on multiple pages and loads the data straight into the store ready to be used anywhere within the application.

Example with single file store:

```js
const axios = require("axios");

export const state = () => ({
  data: [],
});

export const mutations = {
  SET_DATA: (state, newData) => {
    state.data = newData;
  },
};
// The nuxtServerInit first argument is the store context, below 'commit' is being destructed
export const actions = {
  async nuxtServerInit({ commit }) {
    const response = await axios.get("uri");
    const data = response.data;

    store.commit("SET_DATA", data);
  },
};
```

We can then access this data anywhere within the application:

```js
import { mapState } from "vuex";

export default {
   computed: {
      ...mapState({ "data" });
   }
};
```
