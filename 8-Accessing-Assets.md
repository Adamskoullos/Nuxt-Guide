# Accessing Assets

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
<Card v-for="(image, i) in images" :key="i">
  <img :src="require(`~/assets/${image}.jpg`)" />
</Card>
```
