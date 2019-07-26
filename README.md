[![DOI](https://zenodo.org/badge/199070243.svg)](https://zenodo.org/badge/latestdoi/199070243)

# GraphQL Schemas

GraphQL schema definitions mined from GitHub. This data is described and analyzed in the 2019 ICSOC paper "An Empirical Study of GraphQL Schemas".

## Content available in this snapshot

The `data` folder contains GraphQL schema definition files mined from GitHub in May 2019. The data stems from 1915 repositories. This data is a subset of the open-source corpus analyzed in the 2019 ICSOC paper "An Empirical Study of GraphQL Schemas". It contains those schemas whose license allows redistribution.

## Structure
The name of every JSON file references the repository the data is collected from. The root object in each JSON file contains metadata about the repository from which all related schemas were collected. The schemas themselves are contained in objects listed in the `schemas` field.

Each of these objects contains a GraphQL schema in [Schema Description Language](https://github.com/graphql/graphql-spec/pull/90) (SDL) in the `content` field. These objects also contain (among other information):

* A boolean `containsQueryType` field, indicating whether the schema contains either an [Schema Definition](https://graphql.github.io/graphql-spec/draft/#sec-Schema) or a [Root Query Operation](https://graphql.github.io/graphql-spec/draft/#sec-Root-Operation-Types).
* A boolean `validSchema` field, indicating whether the schema [is valid](https://graphql.github.io/graphql-spec/draft/#sec-Validation) based on the validation provided by the GraphQL-js reference implementation.
* A boolean `contentDuplicate` field, indicating whether a (valid) schema is structurally a duplicate of another schema in the two corpuses used in the ICSOC paper. Note: if, for example, 4 schemas are structurally equal, one of them will have a `contentDuplicate` value of `false` and the other three will have a `contentDuplicate` value of `true`. The selection of the non-duplicate schema is arbitrary.

In addition, schema objects may contain a `merged` field, containing data on recovering said schema by combining it with other component schemas from the same repository. Within a merged schema object, the actual stringified merged GraphQL schema is contained in the `mergedContent` field.

## License
Licensed under the MIT license.
