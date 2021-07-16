# Layouts

The `layouts` folder includes the `default.vue` file which is the equivalent to Vue's `App.vue`, it is the entry point for all Nuxt pages.
Components that are within each view (NavBar etc..) are placed here.

Within the template of `default.vue` is the main `<Nuxt />` element which is equivalent to Vue's `<router-view />` tag and is the application.

However we do not always want components like the NavBar to show on all pages. In this instance we can define another layout within the `layouts` folder with the structure we need for a specific page and then assign that layout to the given page within the `script` of that page. We can only do this for top level pages though, not nested pages:

```js
<script>
    export default {
        layout: 'layoutName'
    }
</script>
```

It is good practice to have an `error.vue` layout where any error or page not found components can be nested. Nuxt will show this page on error.

# Components

Reusable components are created within the `components` folder. Nuxt by default auto imports components so there is no need to import components manually before they can be used.

To use a component: <ComponentName />

## Nested component directories

We can have folders within the `components` folder, but still just call the components within the nested directory by its name without referencing the nested folder:

```js
// directory
components
    /nestedFolder
        File.vue

// component within template
<File />
```

Best practice to organize components within nested folders is to prefix them with the folder name:

```js
// directory
components
    /user
        UserCard.vue

// component within template
<UserCard />

```

## Lazy-Loading
