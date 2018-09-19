##### [previous][previous]

## Meta Fields

The use case for a meta field is in the event in which you don't know the type you'll get back from GraphQL. You'll need to determine how to handle that data on the client. GraphQL lets you request `__typename`, this is a meta field at any point to get the name of the object type at that specific point.

Example:

```js
{
  search(text: "an") {
    __typename
    ... on Human {
      name
    }
    ... on Droid {
      name
    }
    ... on Starship {
      name
    }
  }
}
```

This is what you would get back,

```js
{
  "data": {
    "search": [
      {
        "__typename": "Human",
        "name": "Han Solo"
      },
      {
        "__typename": "Human",
        "name": "Leia Organa"
      },
      {
        "__typename": "Starship",
        "name": "TIE Advanced x1"
      }
    ]
  }
}
```

That concludes this section, [next][next].

[previous]: ./mutations.md
[docs]: http://graphql.github.io/learn/queries/#directives
[directive]: ./directives.md
[next]: ../schemas/schemas-and-types.md
