# Basic set up using runtimeConfig properties

The `runtimeConfig properties` have replaced the `env property` within the `nuxt.config.js` file and the `dotenv module` is no longer needed as this is now handled by Nuxt.

1. Create `.env` file to house all variables
2. Add `.env` to `gitignore` file to keep secure
3. Create runtimeConfig property objects in `nuxt.config.js`

```js
publicRuntimeConfig: {
    baseURL: process.env.BASE_URL || 'https://nuxtjs.org'
},
privateRuntimeConfig: {
    apiSecret: process.env.API_SECRET
}
```

4. Within components we can access the variables:

**Template**:

```js
<p>Our Url is: {{ $config.baseURL}}</p>
```

**aysncData**:

```js
asyncData({$config}){
    return {
      api: $config.API
    }
  },
```

**Other parts of the script**:

```js
this.$config.API;
```
