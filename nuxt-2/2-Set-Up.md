# Setting up a new project locally

First up check npm version and make sure to have the latest version of npm:

```
npm -v

npm install -g npm
```

Make sure to have the latest version of Node installed on the machine:

```
node -v

nvm install node
```

Once we have the latest version of Node installed we can cd into the directory where we want the local project and create the Nuxt app (npx comes shipped with npm):

`npx create-nuxt-app projectName`

The above command is equivalent to creating a Vue project using the Vue CLI, this triggers the create process within the terminal and Nuxt takes us through the options where we can structure the project:

1. **JavaScript** or TypeScript
2. Package manager: yarn or npm:
3. Ui Framework:
   - Vuetify etc
4. Nuxt Modules
   - Axios:
   - PWA:
   - Content: A Git based headless CMS
5. Linting Tools: **Choose what works for you in dev mode**
   - ESLint
   - Prettier
   - Lint staged files
   - Style lint
   - CommitLint
6. Testing Framework:
   - None
   - Jest (and others)
7. Rendering Mode
   - Universal SSR/SSG:
   - SPA
8. Deployment Target
   - Server Node.js hosting
   - Static JAMstack hosting: **Static on AWS**
9. Dev Tools
   - jsconfig.json **if using vscode**
   - Semantic PR
   - Dependabot (GitHub): auto updates dependencies
10. Continuous Integration: **None - This is set up with AWS Amplify and CodeCommit**
    - GitHub Actions
    - Travis
    - Circle
11. Version Control: **Git**

If Vuetify is added SCSS configuration is set up and any further SCSS files to be added to Vuetify within `nuxt.config.js`. If no component library, we can add SCSS and Bootstrap 5 after install.

# Creating a feature/hotfix branch for development

First make sure to have the latest versions of npm and Node as above.

1. Navigate to the repo within the AWS CodeCommit console
2. Click on the `Branches` tab on the left hand side
3. Click on the `Create Branch` tab in the right hand corner
4. Create Branch:
   - Branch from the `Developer` branch
   - For new feature: feature/branchName
   - For fixes: hotFix/branchName
5. Once created, clone the new branch, cd into the directory where the repo will be added:

```
git clone url
```

Once cloned, `npm install` to add all dependencies.

Run dev server: `npm run dev`
