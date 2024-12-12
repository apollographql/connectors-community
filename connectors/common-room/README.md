

# Common Room REST Connector

This connector currently covers the Contact object in Common Room](https://api.commonroom.io/docs/) REST API. To use this, you'll need to add a `COMMON_ROOM_API_KEY` in your environment variables then running `rover` or the `router` with the config files in this folder. 

## Contributing

The following schema modules need to be:

1. A schema designed for that portion of the rest API as a new `.graphql` file
2. Additions to the `router.yaml` and `supergraph.yaml` files

Modules:

- Activities
- Segments
- Tags