##### [previous][fields]

## Arguments

We can pass arguments into our `human` query like so,

```js
{
  human(id: "1000") {
    name
    height
  }
}
```

in which we get:

```js
{
  "data": {
    "human": {
      "name": "Luke Skywalker",
      "height": 1.72
    }
  }
}
```

The argument we supplied is `"1000"` to `id`.

In GraphQL, every field and nested object can have arguments passed in as well, for example:

```js
{
  human(id: "1000") {
    name
    height(unit: FOOT)
  }
}
```

Arguments can be many different [types][typesdoc], the above uses an Enumeration type, represents a finite set of options (the docs say in the case above, it's either `METER` or `FOOT`).

The result from the previous query:

```js
{
  "data": {
    "human": {
      "name": "Luke Skywalker",
      "height": 5.6430448
    }
  }
}
```

[fields]: ./fields.md
[types]: #
[typesdoc]: http://graphql.github.io/learn/schema
