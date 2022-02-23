# Plugins

Nuxt has a `plugins` folder that is used to extract set-up code for third party libraries and other code that would be extracted to a composable.

Nuxt runs files within the `plugins` folder once on the server and then again on the client. Files within the this folder can be named:

- **file.client.js** > To run only client-side
- **file.server.js** > To run only server-side
- **file.js** > To run both server-side and client-side

plugins need to be registered/loaded within the `nuxt.config.js` file within the `plugins` array:

```js
plugins: ["@/plugins/file"];
```

To access a plugins function within the application we use the `inject()` method.

The `context`, and `inject` objects are passed into the `export default ()` function, we then have access to set-up the `inject` method.

```js
inject("globalFlag", { pluginFunction });
```

Now we can call the `pluginFunction` anywhere within the application by using the flag, passing in any any data or elements we need access to:

```js
this.$globalFlag.pluginFunction();
```
