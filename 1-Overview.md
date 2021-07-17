# Overview

The current information is regarding: Nuxt 2 which includes Vue 2 options API and VueX 3. At the time of writing, this is the most stable current set-up.

Nuxt is a meta-framework built on top of Vue with many key advantages:

Nuxt apps can be structured as:

- SPA (like Vue)
- Universal SSR / SSG (Static)

Nuxt Universal apps behave like an SPA from the users perspective giving a native app experience, also within the set-up process we can automatically add PWA configuration. More on this later.

As Nuxt Universal apps pre-render html on the server side browsers are able to crawl the content allowing opportunities for SEO. Nuxt offers `Vue-Meta` making it easy to add app-wide and page specific meta-data.

Out of the box Universal apps are configured for automatic code splitting (only loading the components needed) allowing for fast initial load times. Coupled with this Nuxt makes it very easy to lazy-load data only when the component requires it.

Built into a Nuxt app:

- VeuX
- Vue Router
- Vue-Meta

During the create process Nuxt modules can also be added which we will cover in the set-up process.

Nuxt comes shipped with a comprehensive folder structure which promotes consistent organization from project to project making the transition into a new code base or going back to maintain easier and more familiar:

- Assets
- Components
- Pages
- Layouts
- Store
- Middleware
- Static
- Plugins

The `Pages` folder above is where all view files live. There is no need for a manual router configuration as in Vue projects.

Nuxt comes with all the lifecycle hooks that Vue has plus some extra ones as well as many built in methods.
