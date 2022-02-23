# Modules

Nuxt runs the code for any files within the `modules` folder at build-time and run-time before running the code for any files within the `plugins` folder.

Modules run at the beginning of a build and can be used for:

- Generating files
- Copying assets
- Fetching data
- Changing the webpack configuration

Files are loaded within the `nuxt.config.js` file within the `modules` array in the same way plugins are.
