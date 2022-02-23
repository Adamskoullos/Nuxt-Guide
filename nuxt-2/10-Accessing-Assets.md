# Accessing Assets

The `assets` folder is compiled and the `static` folder is not.

The `assets` folder is used for SASS and JS files as well as SVGs and images. The `static` folder can also be used for images but this folder is not compiled.

If an image is located directly within the `static` folder we can use the file name: `src="file-name.jpg"`. This is because Nuxt looks in the `static` folder by default.

If an image is within the `assets` folder we need to start at the project root: `src="~/assets/file-name.jpg"`.

When working with background images from the assets folder we drop the first forward slash:

```css
.image {
  background: url("~assets/file-name.jpg");
}
```

## Dynamic Images

When working with an array of images or any other dynamic images we need to wrap the image path with a `require()` so webpack can find them:

```html
<div v-for="(image, i) in images" :key="i">
  <img :src="require(`~/assets/${image}.jpg`)" />
</div>
```

Last example when working with an array of card like items and the images are stored within a folder within `assets` with the `file name` matching the `card.image`. Notice we are using the `@` symbol this time to start at the project root:

```html
<!-- View with nested Card component passing down the card-->
<Card v-for="card in cards" :key="card.id" :card="card" />

<!-- Card component -->
<div>
  <img :src="require(`@/assets/images/${card.image}`)" />
  <h1>{{ card.title }}</h1>
</div>
```
