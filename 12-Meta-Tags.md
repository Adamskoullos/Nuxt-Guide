# Meta-Tags

Nuxt meta-tags can be added to the project via the `nuxt.config.js` file, these are global meta-tags. They can also be added at page level within the script tags for that page.
Below is the out-the-box meta-tag configuration within the `nuxt.config.js` file:

```js
// Global page headers: https://go.nuxtjs.dev/config-head
head: {
titleTemplate: '%s - nuxt-airbnb-clone',
title: 'nuxt-airbnb-clone',
htmlAttrs: {
    lang: 'en'
},
meta: [
    { charset: 'utf-8' },
    { name: 'viewport', content: 'width=device-width, initial-scale=1' },
    { hid: 'description', name: 'description', content: '' },
    { name: 'format-detection', content: 'telephone=no' }
],
link: [
    { rel: 'icon', type: 'image/x-icon', href: '/favicon.ico' }
]
},

```

**Note**: The `%s` above within the `titleTemplate` is a dynamic prefix. Below we have page specific meta-tags, the home page name becomes the dynamic prefix.

When using meta-tags at page level we add a `head(){}` to the exported object:

```js

head(){
    return{
        title: 'Home Page',
        meta: [{
            name: 'description',
        }]
    }
}
```
