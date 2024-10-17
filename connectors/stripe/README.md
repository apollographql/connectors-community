# Stripe REST Connector

This connector currently covers the Price object in Stripe. To use this, you'll need to add a `STRIPE_API_KEY` in your environment variables then running `rover` or the `router` with the config files in this folder. 

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
        "STRIPE_API_KEY": "",
        "APOLLO_KEY": "",
        "APOLLO_GRAPH_REF": "",
        "APOLLO_ROVER_DEV_ROUTER_VERSION": "2.0.0-preview.0",
        "APOLLO_ROVER_DEV_COMPOSITION_VERSION": "=2.10.0-preview.0",
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

- [Core](https://docs.stripe.com/api/)
- [Payment Methods](https://docs.stripe.com/api/balance)
- [Checkout](https://docs.stripe.com/api/checkout/)
- [Payment Link](https://docs.stripe.com/api/payment-link)
- [Billing](https://docs.stripe.com/api/payment-link)
...*see left column of https://docs.stripe.com/api*...