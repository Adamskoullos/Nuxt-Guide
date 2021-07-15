# Overview

Nuxt is a meta-framework built on top of Vue with some key advantages:

Nuxt apps can be structured as:

- SPA (like Vue)
- Universal SSR / SSG (Static)

Nuxt Universal apps behave like an SPA from the users perspective giving a native app experience, also within the set-up process we can automatically add PWA configuration. More on this later.

Out of the box SSR apps are configured for automatic code splitting allowing for fast initial load times. Nuxt only loads the data that it needs when it needs it allowing fast click-to-view times.

Built into a Nuxt app:

- VeuX
- Vue Router
- Vue-Meta

Vue-Meta is used within SSR apps and allows SEO optimization which makes Nuxt an option for marketing and sales websites.

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

The `Pages` folder above is where all view files live. There is no need for a router configuration as in Vue projects.

Nuxt comes with all the lifecycle hooks that Vue has plus some extra ones as well as many built in methods.
