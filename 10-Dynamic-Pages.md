# Creating and setting up dynamic pages

1. The page/view is prefixed with an underscore to tell Nuxt that this is a dynamic page: `_pageName.vue`
2. Within the 'list of items' page each item can be clicked to show a page just for that item. Each item within this list page has a `NuxtLink` configured to use a dynamic path using a property within that item as the unique params:

```html
<NuxtLink :to="item.slug" />{{ item.name }}</NuxtLink>

```

3. As the user clicks a specific item the lifecycle begins for the dynamic page component firing the `asyncData` hook. The example below then pulls in the dynamic data and then the component mounts the DOM and renders the dynamic data making `_pageName.vue` dynamic:

```js

<script>
  export default {
    async asyncData({ params, $axios }) {
      const item = await $axios.$get(`https://api.nuxtjs.dev/items/${params.pageName}`); // Note the params is the same as the dynamic page name (pageName) without the underscore
      return { item }
    }
  }
</script>

```
