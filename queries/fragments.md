##### [previous][previous]

## Fragments

This section uses a scenario where we look at two heroes side by side, along with their friends. Such a query could quickly get complicated, due to repeating the fields at least once - one for each side of the comparisons.

Luckily, GraphQL includes reusable units, called _fragments_ for us to use. Fragments lets you construct sets of fields, and then allows you to include them in your queries.

This is what a fragment looks like:

```js
fragment comparisonFields on Character {
  name
  appearsIn
  friends {
    name
  }
}
```

Using this, we can solve the problem above,

```js
{
  leftComparison: hero(episode: EMPIRE) {
    ...comparisonFields
  }
  rightComparison: hero(episode: JEDI) {
    ...comparisonFields
  }
}
```

So what we did was use aliasing (rememer [alias][previous]?) to make two comparisons, `leftComparison` and `rightComparison` and spread out (javascript term) the fragment inside our `hero` query.

The result of the above query,

```js
{
  "data": {
    "leftComparison": {
      "name": "Luke Skywalker",
      "appearsIn": [
        "NEWHOPE",
        "EMPIRE",
        "JEDI"
      ],
      "friends": [
        {
          "name": "Han Solo"
        },
        {
          "name": "Leia Organa"
        },
        {
          "name": "C-3PO"
        },
        {
          "name": "R2-D2"
        }
      ]
    },
    "rightComparison": {
      "name": "R2-D2",
      "appearsIn": [
        "NEWHOPE",
        "EMPIRE",
        "JEDI"
      ],
      "friends": [
        {
          "name": "Luke Skywalker"
        },
        {
          "name": "Han Solo"
        },
        {
          "name": "Leia Organa"
        }
      ]
    }
  }
}
```

Fragments are used to split complicated app data requirements into smaller, manageable chunks into one initial data fetch (retrieval).

That concludes this section, [next][next].

[previous]: ./alias.md
[next]: ./operation-name.md
