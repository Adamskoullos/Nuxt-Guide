# Overview

## Nuxt 2

- **Vue 2 Options API**
- **VueX 3**

> Nuxt 3 is due to be released for production applications towards the end of 2021.

Nuxt is a meta-framework built on top of Vue with many key advantages. It operates both on the server and the client. When used in Universal mode and hosted as a Statically Generated site we get SEO optimization, super fast initial load times and a native app-like user experience.

Nuxt apps can be structured as:

- SPA (like Vue)
- Universal SSR / SSG (Static)

Nuxt Universal SSG applications can be hosted on AWS Amplify where the app is stored in an S3 bucket then cached and distributed via the AWS CloudFront CDN.

Nuxt offers `Vue-Meta` making it easy to add app-wide and page specific meta-data.

Out of the box Universal apps are configured for automatic code splitting (only loading the components needed) allowing for fast initial load times. Coupled with this Nuxt makes it very easy to lazy-load data only when the component requires it.

Built into a Nuxt app:

- VeuX
- Vue Router
- Vue-Meta

Nuxt comes shipped with a comprehensive folder structure which promotes consistent organization from project to project making the transition into a new code base or going back to maintain an existing code base easier and more familiar:

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

Extras:

- `PWA` configuration can be automatically added to a Nuxt app during creation
- There is a rich ecosystem of `Modules` that can be added to a Nuxt app: https://modules.nuxtjs.org/
- How `Plugins` work in Nuxt: https://nuxtjs.org/docs/2.x/directory-structure/plugins
