# Routing Basics

Nuxt automatically creates the router and adds routes as files are added to the `pages` folder. There is no work required to configure the router within Nuxt.

For internal links anchor tags are replaced with the Nuxt `<NuxtLink to="/">Home</NuxtLink>`, this allows Nuxt to intercept the routing and prevents a page reload. This is rendered as an anchor tag.

The `pages` folder is the root so the index.vue file within this folder equals `/` for all other views/pages the route name is the file name for example:

- File name: About.vue
- link: <NuxtLink to="/About">About</NuxtLink>

Nested pages are managed with nested folders within the `pages` folder.

Example:

The app has a page that shows a list of blog posts this page would be index.vue within the `posts` folder:

```
pages/
    posts/
        index.vue
```

This would be the route: `<NuxtLink to="/posts">Blog Posts</NuxtLink>`

Within the `posts` folder is a page for each individual post, however this only requires one dynamic page prefixed with an underscore.
The folder structure would look like this:

```
pages/
    posts/
        index.vue
        _post.vue

```

1. The page/view is prefixed with an underscore to tell Nuxt that this is a dynamic page: `_post.vue`
2. Within the 'posts' page each post card can be clicked to show a page just for that post:

**NOTE**: When we are using a dynamic route path we need to prefix `:to` with a colon:

```html
<NuxtLink :to="`/posts/${post.id}`" />{{ post.name }}</NuxtLink>

```
