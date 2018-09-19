##### [previous][previous]

## Query and Mutation types

Most types in your schema will be normal object types, but there's two that are special within a schema.

```js
schema {
  query: Query
  mutation: Mutation
}
```

All GQL services have a `query` type, and may or may not have a `mutation` type. They're the same as regular object types, but they're also special because they define an entry point of GQL queries. So, if your queries look like:

```js
query {
  hero {
    name
  }
  droid(id: "2000") {
    name
  }
}
```

This means that your GQL service needs to have a `Query` type with `hero` and `droid` fields, like so:

```
type Query {
  hero(episode: Episode): Character
  droid(id: ID!): Droid
}
```

Mutations work in a similar manner, you define fields on the Mutation type, like so

```js
type Mutation {
    ... so forth
}
```

That concludes this section, [next][next].

[previous]: ./arguments.md
[next]: ./scalar-types.md
