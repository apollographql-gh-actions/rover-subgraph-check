# Apollo Rover Subgraph Check

**IMPORTANT**: This action requires that you first install Rover into the PATH. To do so, please use the [`install-rover` GitHub Action](https://github.com/apollographql-gh-actions/install-rover) as shown below.

This is a GitHub Action to perform the [`rover subgraph check`](https://www.apollographql.com/docs/rover/commands/subgraphs#subgraph-check) command.

## Inputs

| Name | Description | Required | Default |
| ---- | ----------- | :------: | :-----: |
| `apollo-key` | Your Apollo Studio API key | * | |
| `graph-ref` | `<NAME>@<VARIANT>` of graph in Apollo Studio | * | |
| `name` | The name of the subgraph | * | |
| `schema` | The schema file to check | * | |
| `background` | Set to `true` if the check should run asynchronously | | `false` |
| `query-count-threshold` | The minimum number of times a query or mutation must have been executed in order to be considered in the check operation | | |
| `query-percentage-threshold` | The minimum percentage of times a query or mutation must have been executed, relative to the request count, for it to be considered in the check (0 <= x <= 100) | | |
| `validation-period` | Size of the time window with which to validate schema against (i.e. `24h` or `1w 2d 5h`) | | |
| `log` | Specify Rover's log level | | `info` |
| `format` | Specify Rover's log format type [`plain`, `json`] | | `plain` |
| `client-timeout` | Configure the timeout length (in seconds) when performing HTTP(S) requests | | `30` |

## Usage

_**Note**: You must first install the Rover CLI_

```yaml
- uses: apollographql-gh-actions/install-rover-cli@v1
- uses: apollographql-gh-actions/rover-subgraph-check@v1
  with:
    apollo-key: ${{ secrets.APOLLO_KEY }}
    graph-ref: ${{ vars.APOLLO_GRAPH_REF }}
    name: subgraph-name
    schema: ./path/to/schema.graphql
```