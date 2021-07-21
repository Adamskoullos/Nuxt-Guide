# The Context

The context object is available as the first argument in:

- asyncData
- fetch
- plugins
- middleware
- nuxtServerInit (Second argument as the `VueX Context` is the first argument here)

Context properties can be accessed by either destructing the context object as it is being passed in or via dot notation.

Properties available both server-side and client-side:

- **app**: NuxtAppOptions within plugins
- **store**: To access the VueX store: $store.state.data
- **route**: The route params: $route.params.id
- **params**: The shortcut: $params.id
- **query**: Shortcut: $route.query
- **env**: Environment variables set in `nuxt.config.js`
- **isDev**: Boolean, check if running in dev mode
- **isHMR**: middleware webpack hot module replacement (boolean)
- **redirect**: Redirect to another page: redirect(status, path)
- **error**: Method to show the error page: error(params)
- **$config**: The run-time config

Properties available only server-side:

- req
- res
- beforeNuxtRender

To check if something is firing on the server: `process.server`

Properties available only client-side:

- nuxtState
- from: The route navigated from

To check if something is firing on the client: `process.client`
