# SCSS

By default Nuxt 2 does not come with SCSS unless a component library (Vuetify) is added at creation, however we can easily add SCSS to our Nuxt 2 application:

1. Install SASS within the project directory: `npm install --save-dev node-sass sass-loader`

2. To set up and enable global style files:

   - Install `npm install --save-dev @nuxtjs/style-resources`
   - Add the below to the modules array within the **nuxt.config.js** file:

```js
modules: ["@nuxtjs/style-resources"];
```

3. Then add the `styleResources` object to the `nuxt.config.js` file with any files:

```js
styleResources: {
  scss: ["~/assets/scss/variables.scss"];
}
```

> We do not need to import global files within each component

4. To use SCSS at component level add the `lang` attribute to the style tags: `lang="scss"`

# Vuetify

Nuxt 2 can be built with Bootstrap-Vue which uses Boostrap 4.5 under the hood. Vuetify offers all the features as Bootstrap like the flex-box rows and columns but also has a whole lot of other tools to assist in creating refined professional UI's with a focus on Googles Material Design methodology and was designed from the ground up for Vue.

Vuetify has a grid system very similar to bootstrap, built under the hood with flex-box and also uses the 12-column approach. The syntax used however is more efficient and slightly more declarative:

```html
<v-container fluid>
  <v-row>
    <v-col col="12" md="6"> </v-col>
    <v-col col="12" md="6"> </v-col>
  </v-row>
</v-container>
```

When adding Vuetify at project creation the `nuxt.config.js` file includes the SCSS array for global style-sheets within the Vuetify object:

```js
vuetify: {
    customVariables: ['~/assets/scss/variables.scss', '~/assets/scss/test.scss'],
    theme: {
      dark: true,
      themes: {
        dark: {
          primary: colors.blue.darken2,
          accent: colors.grey.darken3,
          secondary: colors.amber.darken3,
          info: colors.teal.lighten1,
          warning: colors.amber.base,
          error: colors.deepOrange.accent4,
          success: colors.green.accent3
        }
      }
    }
  },
```

Above: further global SCSS files can be added to this array.
