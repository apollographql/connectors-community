# Apollo Connectors Community

This repository is mean to be an early space for builders to share API connectors to help accelerate the community with rich starting points. There is some basic workflow functionality in this repository that can help a builder get a new project started in seconds with a fantastic developer experience. A new project created with `connectors-community` includes:

- A fully working local instance with everything you need to connect to any REST API
  - If you want to start with an existing/prebuilt connector in this repo, you can start with that schema
  - If you want to create a new connector, the basic local instance mirrors what is in our [quickstart documentation](https://www.apollographql.com/docs/graphos/get-started/guides/rest-quickstart)
- Docker file to easily host the project
- A graph in GraphOS created with API keys synced to your local project
- VS Code supercharged `.vscode` folder
  - `dev` command with hot reloading for all the related files available as a Task
  - Custom terminal profile created that includes GraphOS API keys
  - Recommendations for the Apollo extension
- Everything configured it all just works 💪

## Prerequisites

- [Install rover v0.27.0-rc.0](https://www.apollographql.com/docs/rover/getting-started)

```sh
curl -sSL https://rover.apollo.dev/nix/v0.27.0-rc.0 | sh
```

## Setup repo to start creating new projects

1. Install packages:

```sh
npm i
```

2. Create .env file locally with your [user GraphOS API key(https://studio.apollographql.com/user-settings/api-keys)]:

```sh
APOLLO_KEY=user:gh.michael-watson:867tg98076gbiln-iugiuy
```

## Creating a new project

The wizard is designed to be a quick and easy way to setup a new local environment that is synced with GraphOS. This includes creating a new graph or connecting to an existing graph.

```sh
npm run start
```

This will let you select a new or existing connector that is created locally for you and wired up to a graph in GraphOS.

If you face any issues, please open up a GitHub issue with the terminal output.

**Note: The wizard *currently* only works for selecting a single connector. If you want to use multiple connectors, you'll need to copy the schema files for the additional connectors after running the wizard and updating your `suprgraph.yaml`/`router.yaml`**

## Just using the repo (manual setup)

You can place your Apollo key and graph ref in the `.vscode/setting.json` file, reload the window and then the `rover dev` Task in vs code will start working with the local supergraph yaml.

The Apollo VS Code extension is setup to work with the root supergraph.yaml file. You can modify that file to design out a graph using multiple connectors, for example:

```yaml
federation_version: =2.10.0-preview.4
subgraphs:
  stripe-products:
    routing_url: http://stripe-product
    schema:
      file: ./connectors/stripe/products.graphql
  stripe-checkout:
    routing_url: http://stripe-checkout
    schema:
      file: ./connectors/stripe/checkout.graphql
```

You can also configure the `rover dev` Task for VS Code in the `.vscode/tasks.json` folder:

```json
{
    "version": "2.0.0",
    "tasks": [{
        "label": "rover dev",
        "command": "rover", // Could be any other shell command
        "args": ["dev", "--supergraph-config","supergraph.yaml", "--router-config","./connectors/stripe/router.yaml"],
        "type": "shell",
        "problemMatcher": [],
    }]
}
```

## Contributing a connector to the community

We welcome any and all contributions! There are only a couple requirements:

1. *We need to be able to recreate your connector work*. Ideally we can hit some live endpoints, but that isn't the case with some APIs but if we have an OpenAPI specification with example definitions, we can have a mocked REST API that a connector is built with.
2. *The connector must be working and complete*. You don't have to implement the entire API to contribute, just a portion of it. We just want to ensure that whatever you have implemented is used in the schema; the goal is to try and avoid unused definitions that should be pruned.

That's it! Feel free to open an issue with the "New Connector" template or a PR with your work. The Apollo DevRel team will work with you to help usher your contribution and then help promote your work to the broader community. If you need some help, you can open a post on the Apollo Community Forums and add the `connectors` tag to it. Apollo DevRel has those tags popping up in a special internal channel and we'll be able to react a little faster.
