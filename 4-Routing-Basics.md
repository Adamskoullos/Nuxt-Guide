# Routing Basics

There is no file were the router and all routes are set up. Within Nuxt this is done for us.

For internal links anchor tags are replaced with the Nuxt `<NuxtLink to="/">Home</NuxtLink>`, this allows Nuxt to intercept the routing and prevents a page reload. This is rendered as an anchor tag.

The `pages` folder is the root so the index.vue file within this folder is equals `/` for all other views/pages the root name is the file name for example:

- File name: About.vue
- link: <NuxtLink to="/About">About</NuxtLink>

Nested pages are managed with nested folders within the `pages` folder.
