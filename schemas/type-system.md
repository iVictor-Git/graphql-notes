##### [previous][previous]

## Type system

You've seen a typical GraphQL (GQL) query before, and you know that this query is basically selecting fields on objects. For example:

```js
{
  hero {
    name
    appearsIn
  }
}
```

1. We start with a special `root` object
2. We then select the hero field
3. For the object returned by `hero`, we then select both the `name` and `appearsIn` fields.

The shape of a GQL query closely matches the result, also here's the result of the query above,

```js
{
  "data": {
    "hero": {
      "name": "R2-D2",
      "appearsIn": [
        "NEWHOPE",
        "EMPIRE",
        "JEDI"
      ]
    }
  }
}
```

We can predict what the query would return without knowing much about the server. Still, it's pretty useful to know the exact description of the data that we ask for - what fields can we select? What kinds of objects might they return? What fields are available on those sub-objects? That's where the schema comes in.

Every GraphQL service defines a set of types which completely describe the set of possible data you can query on that service. Then, when queries come in, they are validated and executed against that schema.

That concludes this section, [next][next].

[previous]: ./schemas-and-types.md
[next]: ./type-language.md
