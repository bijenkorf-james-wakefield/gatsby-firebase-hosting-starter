<!-- AUTO-GENERATED-CONTENT:START (STARTER) -->
<p align="center">
  <a href="https://www.gatsbyjs.org">
    <img alt="Gatsby" src="https://www.gatsbyjs.org/monogram.svg" width="60" />
  </a>
</p>
<h1 align="center">
  Gatsby's Firebase hosting starter
</h1>

Kick off your project with this default boilerplate. This starter ships with the main Gatsby configuration files you might need to get up and running blazing fast with the blazing fast app generator for React.

_Have another more specific idea? You may want to check out our vibrant collection of [official and community-created starters](https://www.gatsbyjs.org/docs/gatsby-starters/)._

## Prerequisites

1. [A Firebase account](https://console.firebase.google.com/).

2. A Firebase project.

3. Install Firebase CLI - see [documentation](https://firebase.google.com/docs/hosting/quickstart#install-cli)

4. A Firebase deploy token (FIREBASE_DEPLOY_TOKEN). See [Documentation](https://firebase.google.com/docs/cli/#command_reference)

```bash
$ firebase login:ci
```

4. [A Google Cloud account](https://console.cloud.google.com)

5. Install Google Cloud SDK - see [documentation](https://cloud.google.com/sdk/install)

6. Your project's code in a remote GIT repository (Github, Bitbucket or Cloud Source repository)

## 🚀 Quick start

1.  **Create a Gatsby site.**

    Use the Gatsby CLI to create a new site, specifying the default starter.

    ```sh
    # create a new Gatsby site using the default starter
    gatsby new my-firebase-hosting-starter https://github.com/gatsbyjs/gatsby-firebase-hosting-starter
    ```

1.  **Start developing.**

    Navigate into your new site’s directory and start it up.

    ```sh
    cd my-firebase-hosting-starter/
    gatsby develop
    ```

1.  **Open the source code and start editing!**

    Your site is now running at `http://localhost:8000`!

    _Note: You'll also see a second link: _`http://localhost:8000/___graphql`_. This is a tool you can use to experiment with querying your data. Learn more about using this tool in the [Gatsby tutorial](https://www.gatsbyjs.org/tutorial/part-five/#introducing-graphiql)._

    Open the `my-firebase-hosting-starter` directory in your code editor of choice and edit `src/pages/index.js`. Save your changes and the browser will update in real time!

1.  **Associate your project with a Firebase Project**

    If you have not done so already, first login to firebase from the command line:

    ```bash
    $ firebase login
    ```

    Check that you have access to your firebase project:

    ```bash
    # list available firebase projects
    $ firebase list
    ```

    Associate this project directory with a Firebase project. When prompted choose the alias of your choice (e.g. default).

    ```bash
    $ firebase use --add
    ```

1.  **Setup Cloud Build**

- Login to the [Google Cloud Console](https://console.cloud.google.com)
- Click the project dropdown menu. In the dialog that opens select the 'ALL' tab. Select the Firebase project you wish to use.
- Navigate to the [Cloud Build](https://console.cloud.google.com/cloud-build/builds) section
- Click 'Enable Cloud Build API'. (If you are prompted to setup billing, instructions on how to do this can be found [here](https://cloud.google.com/billing/docs/how-to/modify-project#enable_billing_for_a_project) or navigate directly to the [Billing](https://console.cloud.google.com/billing) section)
- Login to Google Cloud on the command line

```bash
$ gcloud auth login
```

- Check that you have access to your project

```bash
$ gcloud projects list
```

- Associate this project directory with your gcloud project.

```bash
$ gcloud config set project PROJECT_ID
```

- Submit a build to Cloud Build which uses the cloudbuild.yaml build config and the source in the `firebase` directory. The build installs the firebase tool in the environment. Then, the tool is containerized and pushed to your Container Registry.

```bash
gcloud builds submit --config=./firebase/cloudbuild.yaml ./firebase/
```

- Run your first deploy from the command line to check everything is working correctly

```bash
gcloud builds submit --config=cloudbuild.deploy.yaml . --substitutions=_FIREBASE_DEPLOY_TOKEN="[FIREBASE_DEPLOY_TOKEN]"
```

## 🧐 What's inside?

A quick look at the top-level files and directories you'll see in a Gatsby project.

    .
    ├── config
    ├── firebase
    ├── node_modules
    ├── src
    ├── tests
    ├── .firebaserc
    ├── .gitignore
    ├── cloudbuild.deploy.yaml
    ├── firebase.json
    ├── gatsby-browser.js
    ├── gatsby-config.js
    ├── gatsby-node.js
    ├── gatsby-ssr.js
    ├── LICENSE
    ├── package-lock.json
    ├── package.json
    └── README.md

1.  **`/config`**: This directory contains configuration files for [ESlint](https://eslint.org) and [lint-staged](https://github.com/okonet/lint-staged). The ESlint configuration uses the recommended settings from the [Gatsby docs](https://www.gatsbyjs.org/docs/eslint/). The lint-staged configuration will lint all files staged files on a precommit hook.

2.  **`/firebase`**: This directory contains the build configuration for adding a custom Firebase build step that will enable you to use[firebase-tools](https://firebase.google.com/docs/hosting/quickstart) in Cloud Build as documented [here](https://cloud.google.com/cloud-build/docs/configuring-builds/build-test-deploy-artifacts#deploying_artifacts).

3.  **`/node_modules`**: This directory contains all of the modules of code that your project depends on (npm packages) are automatically installed.

4.  **`/src`**: This directory will contain all of the code related to what you will see on the front-end of your site (what you see in the browser) such as your site header or a page template. `src` is a convention for “source code”.

5.  **`/tests`**: This directory contains the setup for Jest as documented in the [Gatsby Unit testing documentation](https://www.gatsbyjs.org/docs/unit-testing/)

6.  **`.firebaserc`**: Stores yout firebase [project aliases](https://firebase.google.com/docs/cli/#project_aliases)

7.  **`.gitignore`**: This file tells git which files it should not track / not maintain a version history for.

8.  **`cloudbuild.deploy.yaml`**: This file contains the [build configuration](https://cloud.google.com/cloud-build/docs/build-config) for Cloud Build to run the following scripts as build steps:

```bash
# Install all project dependencies
npm install
```

```bash
# Valididate source code complies with linting rules and run's Jest Unit tests.
npm run validate
```

```bash
# build gatsby source
npm run build
```

```bash
# Deploy built source to firebase
firebase deploy
```

9.  **`firebase.json`**: Your firebase project configuration. See the [documentation](https://firebase.google.com/docs/hosting/full-config) for more information

10. **`gatsby-browser.js`**: This file is where Gatsby expects to find any usage of the [Gatsby browser APIs](https://www.gatsbyjs.org/docs/browser-apis/) (if any). These allow customization/extension of default Gatsby settings affecting the browser.

9)  **`gatsby-config.js`**: This is the main configuration file for a Gatsby site. This is where you can specify information about your site (metadata) like the site title and description, which Gatsby plugins you’d like to include, etc. (Check out the [config docs](https://www.gatsbyjs.org/docs/gatsby-config/) for more detail).

10) **`gatsby-node.js`**: This file is where Gatsby expects to find any usage of the [Gatsby Node APIs](https://www.gatsbyjs.org/docs/node-apis/) (if any). These allow customization/extension of default Gatsby settings affecting pieces of the site build process.

11) **`gatsby-ssr.js`**: This file is where Gatsby expects to find any usage of the [Gatsby server-side rendering APIs](https://www.gatsbyjs.org/docs/ssr-apis/) (if any). These allow customization of default Gatsby settings affecting server-side rendering.

12) **`LICENSE`**: Gatsby is licensed under the MIT license.

13) **`package-lock.json`** (See `package.json` below, first). This is an automatically generated file based on the exact versions of your npm dependencies that were installed for your project. **(You won’t change this file directly).**

14) **`package.json`**: A manifest file for Node.js projects, which includes things like metadata (the project’s name, author, etc). This manifest is how npm knows which packages to install for your project.

15) **`README.md`**: A text file containing useful reference information about your project.

## 🎓 Learning Gatsby

Looking for more guidance? Full documentation for Gatsby lives [on the website](https://www.gatsbyjs.org/). Here are some places to start:

- **For most developers, we recommend starting with our [in-depth tutorial for creating a site with Gatsby](https://www.gatsbyjs.org/tutorial/).** It starts with zero assumptions about your level of ability and walks through every step of the process.

- **To dive straight into code samples, head [to our documentation](https://www.gatsbyjs.org/docs/).** In particular, check out the _Guides_, _API Reference_, and _Advanced Tutorials_ sections in the sidebar.

## 💫 Deploy

If you followed the section Setup Cloud Build all you should need to do now is to [setup a build trigger](https://console.cloud.google.com/cloud-build/triggers) to run a deploy using your FIREBASE_DEPLOY_TOKEN listening for changes in your remote git repository.

<!-- AUTO-GENERATED-CONTENT:END -->
