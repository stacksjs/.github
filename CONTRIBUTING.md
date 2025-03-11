# Contributing

First off, thank you for taking the time to contribute to the Stacks ecosystem 💙

## Knowledge Base

This contribution guide is a general guide for all Stacks relating projects. Please also refer to the README of each project for project-specific instructions.

### TypeScript

It's important to note early on that these projects are written with [TypeScript][typescript]. If you're unfamiliar with it or any strongly typed languages, such as Java, then this may feel like a slight roadblock. However, there's never a truly perfect time to start learning it, so ... why not today!

Don't be discouraged, because as you view some of the code examples within the codebase, you will get by learning TypeScript on-the-fly. After all, each project is easy getting started—the code is extremely readable & approachable!

### Architecture

The project you are working on likely is related to the Stacks ecosystem in some way. Under the hood, they are powered in similar ways: by [Vite][vite] and/or [Bun][bun], UI components of some sort, and composable functions.

An understanding of the library architecture and design will help if you're looking to contribute long-term, or if you are working on a big PR. Browse the source and read each of our documentations to get a better idea on how it is structured. Feel free to ask any question _(Bluesky, Discord, or GitHub Discussions)_, we would love to elaborate.

## Getting Started

As mentioned earlier, it is easy getting started. First off, you will deal with the local project install and setup.

### Install

Please view the README of each project, and the general instructions below on how to install projects locally.

Generally speaking, unless you want to manage `pkgx` dependencies manually, you will need to ensure `pkgx` is installed. `pkgx` then automatically manages the dependencies required for the project.

```bash
# activate pkgx in your project
dev

# install project node_modules
bun install
```

### Project Setup

Most project don't require any further specific project set up and they are ready to run common scripts like:

```bash
bun install
bun run dev
bun run build
bun run dev:docs
bun run build:docs
bun test
# etc.
```

**Working on your first Pull Request?** You can learn how from this free series [How to Contribute to an Open Source Project on GitHub][pr-beginner-series].

#### Stacks

Head over to the [repository][stacks] on GitHub and click the Fork button in the top right corner. After the project has been forked, run the following commands in your terminal:

```bash
# Replace {github-username} with your GitHub username.
git clone https://github.com/{github-username}/stacks --depth=1

cd stacks

# Create a branch for your PR, replace {issue-no} with the GitHub issue number.
git checkout -b issue-{issue-no}
```

Now it'll help if we keep our `main` branch pointing at the original repository and make
pull requests from the forked branch.

```bash
# Add the original repository as a "remote" called "upstream".
git remote add upstream git@github.com:stacksjs/stacks.git

# Fetch the git information from the remote.
git fetch upstream

# Set your local main branch to use the upstream main branch whenever you run `git pull`.
git branch --set-upstream-to=upstream/main main

# Run this when we want to update our version of main.
git pull
```

##### Buddy

The following list is of some of the most common ways to interact with the Stacks API. Meet Artisan:

```bash
buddy install # installs all dependencies
buddy dev # starts one of the dev servers (components, functions, pages, or docs)
buddy build # follow CLI prompts to select which library (or server) to build
buddy commit # follow CLI prompts for committing changes
buddy release # creates the releases for the stack & consequently, publishes them to npm

buddy make:component HelloWorld # scaffolds a component
buddy make:function HelloWorld # scaffolds a function
buddy make:page hello-world # scaffolds a page (https://127.0.0.1/hello-world)

buddy help
```

<details>
<summary>View the complete Buddy Toolkit</summary>

```bash
buddy --version # get the Stacks version
buddy --help # view help menu
# please note: you may suffix any command with the
# `command --help` flag to review the help menu

buddy install # installs dependencies
buddy add # adds a stack or dependency
buddy fresh # fresh reinstall of all deps
buddy clean # removes all deps
buddy setup # sets up the project initially
buddy setup:oh-my-zsh # optional: sets up Oh My Zsh with auto-completions & "aliases"

buddy upgrade # upgrades all dependencies
buddy upgrade -i # prompts you to select which updates to apply (wip)
buddy upgrade:dependencies # auto-upgrades package.json deps
buddy upgrade:framework # auto-upgrades deps & the Stacks framework
buddy upgrade:search-engine # auto-upgrades configured search engine
buddy upgrade:shell # upgrades the shell integration
buddy upgrade:binary # upgrades the `stacks` binary
buddy upgrade:bun # upgrades to latest project-defined Bun version
buddy upgrade:all # auto-upgrades all of the above

# if you need any more info on any command listed here, you may suffix
# any of them via the "help option", i.e. `buddy ... --help`

buddy dev # starts the frontend dev server
buddy dev -i # prompts any of the dev servers (components, functions, views, docs, or api)
buddy dev:api # starts the API dev server
buddy dev:dashboard # starts the Admin/Dashboard dev server
buddy dev:desktop # starts the Desktop dev server
buddy dev:views # starts frontend dev server
buddy dev:components # starts component dev server
buddy dev:functions # stubs functions
buddy dev:docs # starts local docs dev server
buddy dev docs # also starts the local docs dev server (colon is optional for all commands)
buddy development # `buddy dev` alias

buddy share # creates a sharable link to your local project

# for Laravel folks, `serve` may ring more familiar than the `dev` name. Hence, we aliased it:
buddy serve
buddy serve:components
buddy serve:desktop
buddy serve:views
buddy serve:functions
buddy serve:docs

# building for production (e.g. AWS, Google Cloud, npm, Vercel, Netlify, et al.)
buddy build # select a specific build (follow CLI prompts)
buddy build:views # builds SSG views
buddy build:desktop # builds Desktop application
buddy build:library # builds any or all libraries
buddy build:functions # builds function library
buddy build:components # builds Vue component library & Web Component library
buddy build:web-components # builds framework agnostic Web Component library (i.e. Custom Elements)
buddy build:vue-components # builds Vue 2 & 3-ready Component library
buddy build:all # builds all your code

# `buddy build` aliases
buddy prod
buddy prod:components
buddy prod:desktop
buddy prod:library
buddy prod:views
buddy prod:functions
buddy prod:vue-components
buddy prod:web-components
buddy prod:all
buddy production # `buddy prod` alias

# sets your application key
buddy key:generate

buddy make:component HelloWorld # bootstraps a HelloWorld component
buddy make:function hello-world # bootstraps a hello-world function
buddy make:view hello-world # bootstraps a hello-word page
buddy make:model Car # bootstraps a Car model
buddy make:database cars # creates a cars database
buddy make:migration create_cars_table # creates a cars migration file
buddy make:factory cars # creates a Car factory file
buddy make:table cars # bootstraps a cars data table
buddy make:notification welcome-email # bootstraps a welcome-email notification
buddy make:lang de # bootstraps a lang/de.yml language file
buddy make:stack my-project # shares logic with `bunx --bun stacks new my-project`

buddy migrate # runs database migrations
buddy migrate:dns # sets the ./config/dns.ts file

buddy dns example.com # list all DNS records for example.com
buddy dns example.com --type MX # list MX records for example.com (proxies dog)

buddy https httpie.io/hello
# http [flags] [METHOD] URL [ITEM [ITEM]]
buddy http --help
buddy http PUT pie.dev/put X-API-Token:123 name=John # Custom HTTP method, HTTP headers and JSON data
buddy http -v pie.dev/get # See the request that is being sent using one of the output options
buddy http -f POST pie.dev/post hello=World # submitting forms
buddy http --offline pie.dev/post hello=offline
buddy http -a USERNAME POST https://api.github.com/repos/httpie/cli/issues/83/comments body='HTTPie is awesome! :heart:'
buddy http pie.dev/post < files/data.json
buddy http pie.dev/image/png > image.png
buddy http --download pie.dev/image/png
buddy http --session=logged-in -a username:password pie.dev/get API-Key:123
buddy http --session=logged-in pie.dev/headers
buddy http localhost:8000 Host:example.com

buddy lint # runs linter
buddy lint:fix # runs linter and fixes issues

buddy commit # follow CLI prompts for committing staged changes
buddy release # creates the releases for the stack & triggers the Release Action (workflow)
buddy changelog # generates CHANGELOG.md

# when deploying your app/s to a remote server or cloud provider
buddy deploy # select a specific deployment (follow CLI prompts)
# buddy deploy:docs # deploys docs to AWS (or other configured provider)
# buddy deploy:functions # deploys functions to AWS (or other configured provider)
# buddy deploy:views # deploys views to AWS (or other configured provider)
# buddy deploy:all # deploys all your code
buddy undeploy # be careful: "undeploys" removes/deletes your deployed resources

buddy cloud:remove # removes cloud setup
buddy cloud:cleanup # removes cloud setup & cleans up all potentially leftover resources
buddy cloud:add --jump-box # adds a jump box to your cloud setup

# select the example to run (follow CLI prompts)
buddy example # prompts you to select which example to run
buddy example:vue # runs the Vue example
buddy example:web-components # runs the Web Component example

# you likely won’t need to run these commands as they are auto-triggered, but they are available
buddy generate  # prompts you to select which generator to run
buddy generate:types # generates types for your components, functions, & views
buddy generate:entries # generates entry files for components, functions, & views
buddy generate:web-types # generates Web Component types
buddy generate:vscode-custom-data # generates VSCode custom data
buddy generate:ide-helpers # generates IDE helpers
buddy generate:component-meta # generates component meta
buddy generate:all # runs all generators

# generates your application key
buddy key:generate # generates your application key

# generate your TypeScript declarations
buddy types:generate # generates types for your components, functions, & views
buddy types:fix # auto-fixes types for your components, functions, & views

buddy domains # alias for `buddy domains:list`
buddy domains:add stacksjs.org # adds a domain
buddy domains:remove stacksjs.org # removes a domain
buddy domains:list # lists all domains
buddy domains:update # apply ./config/dns.ts updates
buddy domains:purchase stacksjs.org # purchase a new domain

# test your stack
buddy test # runs test suite (unit & e2e)
buddy test:coverage # runs test coverage
buddy test:types # runs typecheck

# the CLI may be triggered in any
# of the following syntax:
stx fresh
buddy fresh
bud fresh
```

</details>

## Test

### Unit

Each of our components come with test cases. Feel free to check them out within the `./tests` root folder. When adding or or updating functionality, please ensure it is covered through our tests cases. Ensure so by running `bun test`.

## Commit

This project uses [semantic commit messages][semantic-commit-style] to automate package releases. We automated the commit process for you, and simply run `bun run commit` or `buddy commit` in your terminal and follow the instructions.

For example,

```bash
# Add all changes to staging to be committed.
git add .

# Commit changes. (or `bun run commit`)
buddy commit 

# Push changes up to GitHub.
git push
```

## Pull Request

When you're all done, head over to the [repository][stacks], and click the big green `Compare & Pull Request` button that should appear after you've pushed changes to your fork.

Don't expect your PR to be accepted immediately or even accepted at all. Give the community time to vet it and see if it should be merged. Please don't be disheartened if it's not accepted. Your contribution is appreciated more than you can imagine, and even a failed PR can teach us a lot 💙

[typescript]: https://www.typescriptlang.org
[vite]: https://vitejs.dev/
[bun]: https://bun.sh/
[stacks]: https://github.com/stacksjs/stacks
[semantic-commit-style]: https://gist.github.com/joshbuchea/6f47e86d2510bce28f8e7f42ae84c716
[pr-beginner-series]: https://app.egghead.io/courses/how-to-contribute-to-an-open-source-project-on-github
