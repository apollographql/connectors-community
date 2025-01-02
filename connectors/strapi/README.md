# Strapi REST Connector

This connector currently covers the users content-type in Strapi. To use this, you'll need to add a `STRAPI_API_KEY` in your environment variables then running `rover` or the `router` with the config files in this folder. If you don't want to point at your local instance, set the `STRAPI_URL` environment variable.

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