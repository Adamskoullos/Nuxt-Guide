## Getting Data

> Using the below script pattern eliminates the need for top level `async` allowing for `useFetch` to use `await` at the top level.

```js
<script setup>
  const {data} = await useAsyncData('count', () => $fetch('/api/count'));
</script>
```

**[docs](https://v3.nuxtjs.org/docs/usage/data-fetching/)**

- [$fetch]()
- [useAsyncData](#useAsyncData)
- [useFetch](#useFetch)

---

### $fetch

`$fetch` is a globally available helper function to call API routes:

- Automatic parsing of JSON
- Content-Type headers are added
- Uses `ohmyfetch` under the hood
- Can be used on the `client` and the `server`

---

### useAsyncData

> Can be used in `components`, `pages` and `Plugins`

Core elements:

```js
const { data, pending, refresh, error } = useAsyncData(key, handler, options);
```

Returned Values:

- `data` > The data returned from the `handler`
- `pending` > The current state of the request `boolean`
- `refresh` > Function used to refresh
- `error` > an object if data fetching fails

Params:

- `key` > unique key
- `handler` > async function that returns the data
- `options` object:
  - `lazy` > default `false` and blocks component load until data is received, set to `true` to load page and then add loader while waiting for data
  - `default` > can set default data value. Good to use when `lazy: true`
  - `server` > control if data is fetched on the server or client, default `true`
  - `transform` > A function to work with the fetched data before returning the final data
  - `pick` > pick specific parts of the data from the initial data fetched from `handler`. This allows only the required data to be sent to the client.

Basic example using an anonymous function as the `handler` and using `$fetch` to get data from the server api:

```ts
<script setup>
const { data } = await useAsyncData('count', () => $fetch('/api/count'));
</script>
```

---

### useFetch

> Can be used in `Pages`, `Components` and `Plugins`

`usefetch` is a wrapper function which takes advantage of both `useAsyncData` and `$fetch`:

```js
const { data, pending, refresh, error } = useFetch(url, options);
```

**Options**:

- `key` > this is automatically created from the url
- `method`
- `params`
- `headers`
- `baseURL`
- `lazy`
- `server`
- `default`
- `pick`
- `transform`

Basic example taken from the docs:

```ts
<script setup>
const { data } = await useFetch('/api/count')
</script>

<template>
  Page visits: {{ data.count }}
</template>
```

Example using the `pick` option to only pull what is used:

```js
const { data: mountain } = await useFetch("/api/mountains/everest", {
  pick: ["title", "description"],
});
```
