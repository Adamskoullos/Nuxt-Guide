# Project set-up

1. Sass and Bootstrap
2. Google Fonts
3. Error page handling

---

# Sass

1. Install SASS and SASS-loader from the Nuxt Assets page:
   https://nuxtjs.org/docs/2.x/directory-structure/assets#sass

```js

npm install --save-dev sass sass-loader@10 fibers
```

2. To set up and enable global style files:

Install the style-resources module:

```js
npm install --save-dev @nuxtjs/style-resources
```

Add the below to the `modules` array within the `nuxt.config.js` file:

```js
modules: ["@nuxtjs/style-resources"];
```

Then add the `styleResources` object to the `nuxt.config.js` file with any files:

```js
styleResources: {
  scss: ["~/assets/scss/custom.scss"];
}
```

**Note**: The above array is for files that pull in Bootstrap 5 files, create custom classes and merge maps, general styling should be done directly within each Vue component.

From the above example we can now: Create an `assets` folder and within that a `scss` folder and then `custom.scss` for all custom variables and maps.

We do not need to import global files within each component as Nuxt takes care of this for us behind the scenes.

# Bootstrap 5

1. Install Bootstrap 5 into the project: `npm install bootstrap`
2. Set-up the `custom.scss` file:

```scss
// Map fonts to variable ---------------------------------------
$font-family-rubik: "Rubik", sans-serif;
$font-family-lato: "Lato", sans-serif;

// Custom font-weights -------------------------------------------
$font-weight-semibold: 500;

// Custom Colors -----------------------------------------------
$lime-green: #5ac205;
$dark-blue: #062c44;
$footer-copyright-blue: #0c2636;
$button-red: #f04617;
$button-orange: #ec7e2b;
$lighter-grey: #f2f2f2;
$light-grey: #959595;
$text-grey: #666666;
$text-dark-grey: #424242;

// Bootstrap default variable overrides ------------------------
$primary: rgb(248, 248, 3);

// Map custom colors to a class -------------------------------
$custom-colors: (
  "lime-green": $lime-green,
);

$accordion-icon-color: $button-orange;

$enable-negative-margins: true;

// Required --------------------------------------------------
@import "~/node_modules/bootstrap/scss/functions";
@import "~/node_modules/bootstrap/scss/variables";
@import "~/node_modules/bootstrap/scss/mixins";

// Custom font sizes -----------------------------------------
$font-size-7: $font-size-base * 1.125;

// Map custom font sizes to a class
$custom-font-sizes: (
  7: $font-size-7,
);

// Merge the maps - Add custom-colors to Bootstrap theme-colors --
$theme-colors: map-merge($theme-colors, $custom-colors);

// Merge the maps - Add custom-font-sizes
$font-sizes: map-merge($font-sizes, $custom-font-sizes);

$h1-font-size: $font-size-base * 3.75;
$small-font-size: 0.75rem;

// Utilities
@import "~/node_modules/bootstrap/scss/utilities";

$utilities: map-merge(
  $utilities,
  (
    "font-family": (
      property: font-family,
      class: font,
      values: (
        rubik: $font-family-rubik,
        lato: $font-family-lato,
      ),
    ),
    "font-size": (
      rfs: true,
      property: font-size,
      class: fs,
      values: $font-sizes,
    ),
    "font-weight": (
      property: font-weight,
      class: fw,
      values: (
        light: $font-weight-light,
        lighter: $font-weight-lighter,
        normal: $font-weight-normal,
        semibold: $font-weight-semibold,
        bold: $font-weight-bold,
        bolder: $font-weight-bolder,
      ),
    ),
  )
);

// Brand Classes -----------------------------------------------------------
.bg-orange-gradient {
  @include gradient-directional($button-red, $button-orange, 97.15deg);
  transition: all 0.2s ease !important;
}
.section-padding {
  padding: 9.5rem 0;

  @include media-breakpoint-down(lg) {
    padding: 4rem 0;
  }
}

.orange-separator {
  width: 10rem;
  height: 0.15rem !important;
  opacity: 1 !important;
  @include gradient-directional($button-red, $button-orange, 97.15deg);
}

// Layout & components --------------------------------------------------------
@import "~/node_modules/bootstrap/scss/root";
@import "~/node_modules/bootstrap/scss/reboot";
@import "~/node_modules/bootstrap/scss/type";
@import "~/node_modules/bootstrap/scss/images";
@import "~/node_modules/bootstrap/scss/containers";
@import "~/node_modules/bootstrap/scss/grid";
@import "~/node_modules/bootstrap/scss/tables";
@import "~/node_modules/bootstrap/scss/forms";
@import "~/node_modules/bootstrap/scss/buttons";
@import "~/node_modules/bootstrap/scss/transitions";
@import "~/node_modules/bootstrap/scss/dropdown";
@import "~/node_modules/bootstrap/scss/button-group";
@import "~/node_modules/bootstrap/scss/nav";
@import "~/node_modules/bootstrap/scss/navbar";
@import "~/node_modules/bootstrap/scss/card";
@import "~/node_modules/bootstrap/scss/accordion";
@import "~/node_modules/bootstrap/scss/breadcrumb";
@import "~/node_modules/bootstrap/scss/pagination";
@import "~/node_modules/bootstrap/scss/badge";
@import "~/node_modules/bootstrap/scss/alert";
@import "~/node_modules/bootstrap/scss/progress";
@import "~/node_modules/bootstrap/scss/list-group";
@import "~/node_modules/bootstrap/scss/close";
@import "~/node_modules/bootstrap/scss/toasts";
@import "~/node_modules/bootstrap/scss/modal";
@import "~/node_modules/bootstrap/scss/tooltip";
@import "~/node_modules/bootstrap/scss/popover";
@import "~/node_modules/bootstrap/scss/carousel";
@import "~/node_modules/bootstrap/scss/spinners";
@import "~/node_modules/bootstrap/scss/offcanvas";

// Helpers
@import "~/node_modules/bootstrap/scss/helpers";

// Utilities
@import "~/node_modules/bootstrap/scss/utilities/api";
// scss-docs-end import-stack
```

3. Set up the Bootstrap and Popper JS bundle file to be used:

- Copy the `bootstrap.bundle.min.js` file from the dist folder within bootstrap and paste it to the `static` folder
- Register the file within a `script` array, within the `head` object within `nuxt.config.js`:

```js
 head: {
    title: 'nuxt-testing',
    htmlAttrs: {
      lang: 'en',
    },
    meta: [
      { charset: 'utf-8' },
      { name: 'viewport', content: 'width=device-width, initial-scale=1' },
      { hid: 'description', name: 'description', content: '' },
      { name: 'format-detection', content: 'telephone=no' },
    ],
    link: [{ rel: 'icon', type: 'image/x-icon', href: '/favicon.ico' }],
    // Add the Bootstrap JS file from the static folder
    script: [
      {
        src: 'bootstrap.bundle.min.js',
      },
    ],
  },

```

# Google Fonts

1. Add google-fonts to the project via npm:

```js
npm install --save-dev @nuxtjs/google-fonts
```

https://www.npmjs.com/package/@nuxtjs/google-fonts

2. Add google-fonts to `nuxt.config.js` file within the `buildModules` array:

```js
buildModules: [
    '@nuxtjs/google-fonts'
  ],
```

3. Create the google-fonts object within `nuxt.config.js`:

```js
googleFonts: {
    families: {
        Rubik: [100, 300, 400, 600, 700],
        Lato: [100, 300, 400],
    }
  }
```

# Folder Structure

## Error Page

1. Create `error.vue` within `layouts`, this is the actual error page that Nuxt shows automatically.
2. Create `error-layout.vue` within `layouts` which is the layout the `error.vue` page displays within

**error-layout.vue:**

```js
<template>
  <div>
    <Nuxt />
  </div>
</template>
```

**error.vue:**

```js
<template>
    <div class="d-flex justify-content-center align-items-center">
        <h1 class="text-center" >Error Page</h1>
    </div>
</template>

<script>
    export default {
       layout: 'error-layout'
    }
</script>
```
