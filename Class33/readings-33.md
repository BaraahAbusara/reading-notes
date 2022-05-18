# Class-33 : GraphQL @connection
***


In this file I will be summarizing what I have learnt in class-33 reading notes which included the following resources :
- [Has Many relationship](https://docs.amplify.aws/cli/graphql/data-modeling/#has-many-relationship)
- [CompletableFuture in Java ](https://www.baeldung.com/java-completablefuture)


## Has Many relationship
*** 
`@hasMany` is used to perform one directional relationship between two models like one-to-many.

to use it you should : 
- reference your key in the table with `@hasMany`
- configure a secondary index using `@index`
- pass in the secondary index name `indexName` parameter and the respective fields which match the connected index.

```
type Post @model {
  id: ID!
  title: String!
  comments: [Comment] @hasMany(indexName: "byPost", fields: ["id"])
}

type Comment @model {
  id: ID!
  postID: ID! @index(name: "byPost", sortKeyFields: ["content"])
  content: String!
}
```

## CompletableFuture in Java 
***
CompletableFuture class implements the Future interface.
we use it to find future results into present using an instance of `CompletableFuture`
and then we may use `get` method to block for the result. 