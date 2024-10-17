# connectors-community

## Setup

```
npm i
```

Create .env file locally with a GraphOS API key:

```
APOLLO_KEY=user:gh.michael-watson:867tg98076gbiln-iugiuy
```

## Using the wizard to create a new local environment

The wizard is designed to be a quick and easy way to setup a new local environment that is synced with GraphOS. This includes creating a new graph or connecting to an existing graph. 

**Note: The wizard *currently* only works for selecting a single connector. If you want to use multiple connectors, you'll need to copy the schema files for the additional connectors after running the wizard and updating your `suprgraph.yaml`/`router.yaml`**

```
npm run wizard
```

This will let you select a new or existing connector that is created locally for you and wired up to a graph in GraphOS. 

If you face any issues, please open up a GitHub issue with the terminal output.

## Just using the repo (manual setup)

You can place your Apollo key and graph ref in the `.vscode/setting.json` file, reload the window and then the `rover dev` Task in vs code will start working with the local supergraph yaml.

The Apollo VS Code extension is setup to work with the root supergraph.yaml file. You can modify that file to design out a graph using multiple connectors.