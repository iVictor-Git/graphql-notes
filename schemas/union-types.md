##### [previous][previous]

## Union Types

These are similar to interfaces, but don't specify common fields between types.

For example,

`union SearchResult = Human | Droid | Starship`

When we return a `SearchResult` type in our schema, we could get either a `Human`, `Droid`, or `Starship`.

When quering a field that returns a `SearchResult` union type, you must use a conditional fragment ([inline-fragments][inline-fragments]) to be able to query any fields at all, like so:

```js
{
  search(text: "an") {
    ... on Human {
      name
      height
    }
    ... on Droid {
      name
      primaryFunction
    }
    ... on Starship {
      name
      length
    }
  }
}
```

Here is the result:

```js
{
  "data": {
    "search": [
      {
        "name": "Han Solo",
        "height": 1.8
      },
      {
        "name": "Leia Organa",
        "height": 1.5
      },
      {
        "name": "TIE Advanced x1",
        "length": 9.2
      }
    ]
  }
}
```

That concludes this section, [next][next].

[previous]: ./interfaces.md
[inline-fragments]: ../queries/inline-fragments.md
[next]: ./input-types.md
