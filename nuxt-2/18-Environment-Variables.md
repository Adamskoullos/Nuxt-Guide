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

# Dynamic NODE_ENV with the use of a config.js file

The `.env` file is kept for most variables including private variables, we will then move the `baseUrl` out of the `.env` file and add this to a new file: `config.js` within the root of the project.

This code takes the current `node environment` and adds it as the value of `config` that is being exported.

```js
const config = {
    development: { baseUrl: "http://mycoformations.local/api" },
    production: { baseUrl: "production.com" },
};

const nodeEnv = process.env.NODE_ENV;

module.exports = config[nodeEnv].baseUrl;
```

We then import `config.js` into `nuxt.config.js` and use the property as the value of the `baseUrl` within the `runtimeConfig` property:

```js
import config from './config';

export default {
  publicRuntimeConfig: {
    baseUrl: config
  },
```

We can then access the value within the app:

```js
this.$config.baseUrl;
```

The advantage to the above is that domains can be pre-set and do not need to be changed going from development to production.
