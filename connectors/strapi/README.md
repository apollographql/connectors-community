# Strapi REST Connector

This connector currently covers the users content-type in Strapi. To use this, you'll need to add a `STRAPI_API_KEY` in your environment variables then running `rover` or the `router` with the config files in this folder. If you don't want to point at your local instance, set the `STRAPI_URL` environment variable.

## Getting Started 

1. If you haven't already, [create a new graph in GraphOS](https://www.apollographql.com/docs/graphos/get-started/guides/rest#step-1-set-up-your-graphql-api). Following the "Set up your local development environment" modal:
  a. Copy the `supergraph.yaml` and `router.yaml` files from this folder
  b. Copy the `users.graphql` schema file
2. Grab your Strapi API key and set it as an environment variable for your terminal:

```
export STRAPI_API_KEY=....
```

3. Run `rover dev` to start the local development session:

```
APOLLO_KEY=service:My-Graph-s1ff1u:•••••••••••••••••••••• \
  APOLLO_GRAPH_REF=My-Graph-s1ff1u@main \
  rover dev --supergraph-config supergraph.yaml --router-config router.yaml
```

Now you’re all set! Open up http://localhost:4000 to query your graph using Apollo Sandbox.

### Adding to an existing graph in GraphOS

Simply publish the `users.graphql` schema file to your graph ref like you would with any subgraph:

```
APOLLO_KEY=service:My-Graph-s1ff1u:•••••••••••••••••••••• \
  rover subgraph publish My-Graph-s1ff1u@main --name users --schema users.graphql --routing-url http://users
```

## Additional Setup for VS Code Task runner

Edit your `.vscode/settings.json` to include the Strapi specific keys

```
{
  "terminal.integrated.profiles.osx": {
    "graphos": {
      "path": "zsh",
      "args": ["-l"],
      "env": { 
        "STRAPI_URL: "",
        "STRAPI_API_KEY": "",
      }
    }
  },
  "terminal.integrated.defaultProfile.osx": "graphos"
}

```

Then you can execute the "Tasks: Run Task" command in VS code to execute the `rover dev` task or simply open a new terminal window in vscode with the `graphos` profile, then you can simply run `rover dev --supergraph-config supergraph.yaml --router-config router.yaml`.

## Contributing

The following schema modules need to be:

1. A schema designed for that portion of the rest API as a new `.graphql` file
2. Additions to the `router.yaml` and `supergraph.yaml` files

Modules:

- [Roles](https://docs.strapi.io/user-docs/users-roles-permissions/configuring-end-users-roles)