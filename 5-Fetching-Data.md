# HTTP Requests

Adding Axios to the Nuxt app is an option at the point of creation. Axios is similar to the JavaScript Fetch when working with Rest API's but has one key advantage.

If there is an error at any point with the request or response Axios catches all and provides information that can be accessed via the request and response objects. These properties can be used to manage events.

In conjunction with JavaScript async/await and Axios, Nuxt also provides the asyncData and fetch hooks (not to be mistaken with JS fetch HTTP request).

# asyncData hook vs fetch hook

These hooks are used to trigger the fetching of data at a particular point in a components lifecycle.

1. asyncData fetches the data before the page is loaded allowing for redirects if there is an issue
2. asyncData will not render the page until all the data has been fetched
3. asyncData is used with the try/catch blocks
4. asyncData does not have states (like fetch), but this can be managed via isPending booleans as normal
5. asyncData can only be used on pages/views but fetch can be used anywhere including nested components. Therefore when using fetch, components can be self sufficient by pulling in the data they use which provides the ability to separate areas within a page with separate loading events and loading handlers.

6. fetch does not utilise the try/catch block as it has request states one of them being `error`.
7. fetch has a `$fetchState` that can be used as boolean switches within the template and operates at component level:
   - **pending**
   - **error**
   - **timestamp**

Here are the docs for further reading: https://nuxtjs.org/docs/2.x/features/data-fetching

8. fetch does not have access to the `context` so we do not need to pass the context in but we do use the `this` keyword when using `axios`. asyncData requires the context to be passed in, but we do not use the `this` keyword when using `axios`.

There is not a one-size fits all here but each are good for different use cases.

**Example**:

```js
// fetch()
export default{
   async fetch(){
   this.variable = await this.$axios.$get('url');
   },

   data(){
      return{
         variable: {}
      }
   }
}
// ----------------------------------------------------
// asyncData
export default{
   async asyncData({ $axios, redirect }){
      try{
         const variable = await $axios.$get('url');
         return{
            variable
         }
      }
      catch(error){
         redirect('/error');
      }
   }
}
```
