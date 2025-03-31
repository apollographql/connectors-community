# Stripe REST Connector

This connector currently covers a portion of the Stripe REST API. To use this, you'll need to add a `STRIPE_API_KEY` in your environment variables then running `rover` or the `router` with the config files in this folder. 

## Getting Started 

1. If you haven't already, [create a new graph in GraphOS](https://www.apollographql.com/docs/graphos/get-started/guides/rest#step-1-set-up-your-graphql-api). Following the "Set up your local development environment" modal:
  a. Copy the `supergraph.yaml` and `router.yaml` files from this folder
  b. Copy the schema files you want to use for this connector (i.e. `checkouts.graphql` and/or `products.graphql`) - *Note - if you only want to use products or checkout, you'll need to modify the `sueprgraph.yaml` file to only contain the schema file you want to use.*
2. Grab your Stripe API key and set it as an environment variable for your terminal:

```
export STRIPE_API_KEY=....
```

3. Run `rover dev` to start the local development session:

```
APOLLO_KEY=service:My-Graph-s1ff1u:•••••••••••••••••••••• \
  APOLLO_GRAPH_REF=My-Graph-s1ff1u@main \
  rover dev --supergraph-config supergraph.yaml --router-config router.yaml
```

Now you’re all set! Open up http://localhost:4000 to query your graph using Apollo Sandbox.

### Adding to an existing graph in GraphOS

Simply publish the schema files to your graph ref like you would with any subgraph:

```
APOLLO_KEY=service:My-Graph-s1ff1u:•••••••••••••••••••••• \
  rover subgraph publish My-Graph-s1ff1u@main --name products --schema products.graphql --routing-url http://products

APOLLO_KEY=service:My-Graph-s1ff1u:•••••••••••••••••••••• \
  rover subgraph publish My-Graph-s1ff1u@main --name checkout --schema checkout.graphql --routing-url http://checkout
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
        "STRIPE_API_KEY": "",
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