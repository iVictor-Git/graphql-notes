##### [previous][previous]

## Fields

What are fields? In the below example, `name` is a field in our `hero` query

```js
{
    hero {
        name
    }
}
```

The return data you would get with this GraphQL query above is

```js
{
    "data": {
        "hero": {
            "name": "R2-D2"
        }
    }
}
```

What we did here was ask for the `name` of the `hero` query, which returned a `String`. Fields can also refer to `Objects`, see below:

```js
{
    hero {
        name
        # queries can have comments!
        friends {
            name
        }
    }
}
```

the resulting data would be:

```js
{
  "data": {
    "hero": {
      "name": "R2-D2",
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

This is great, because now we can just fetch related data in one single query instead of making multiple requests compared to a classic REST architechture.

That concludes this section. [next][next].

[previous]: ./queries.md
[next]: ./arguments.md
