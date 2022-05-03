# graphql-pluck-action

This action extracts, or plucks, graphql schemas from code that uses `graphql-tag`. It uses `@graphql-tools/graphql-tag-pluck` under the hood, and you can read more about how that package works [on the graphql-tools site](https://www.graphql-tools.com/docs/graphql-tag-pluck). It works by pointing it at a source file and specifying and output file.

## Inputs

### `source`

**Required** Path to a file containing code with graphql-tag template literals.

### `output`

**Required** Path to file where the extracted GraphQL schema will be written.

## Outputs

### `filepath`

The path to the file containing the GraphQL schema.

## Example usage

```yaml
jobs:
  pluck:
    name: Pluck graph schema
    runs-on: ubuntu-latest
    needs: [install]
    steps:
      - name: Checkout repo
        uses: actions/checkout@v2

      - name: Pluck schema
        uses: w33ble/gql-pluck-action@main
        with:
          source: 'src/index.ts'
          output: 'src/schema.graphql'
```
