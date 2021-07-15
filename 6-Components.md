# Components

Reusable components are created within the `components` folder. Nuxt by default auto imports components so there is no need to import components manually within other components or views before they can be used.

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
