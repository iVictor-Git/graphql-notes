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

The argument we supplied is `"1000"` to `id`

[fields]: ./fields.md
