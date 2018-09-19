##### [previous][previous]

## Directives

In this section, the use case consists of having a component that displays a summarized view and then a detailed view.

GraphQL has a feature called a directive that would help with this. Directions can be attached to a field or fragment inclusion. See below,

```js
query Hero($episode: Episode, $withFriends: Boolean!) {
  hero(episode: $episode) {
    name
    friends @include(if: $withFriends) {
      name
    }
  }
}
```

by calling this query,

```js
{
  "episode": "JEDI",
  "withFriends": false
}
```

we will get,

```js
{
  "data": {
    "hero": {
      "name": "R2-D2"
    }
  }
}
```

Now, if we alter `withFriends` to `true`, for example,

```js
{
  "episode": "JEDI",
  "withFriends": true
}
```

we now get all of the friends, like so,

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

The directive in this case is the `@include(if: $withFriends)` statement. The core GraphQL specification includes exactly two directions:

- `@cinclude(if: Boolean)` Only include this field if argument is `true`
- `@skip (if: Boolean)` skip this field if argument is `true`

In the above, the `argument` is what you place in the spot of `Boolean`.

That concludes this section, [next][next].

[previous]: ./variables.md
[docs]: http://graphql.github.io/learn/queries/#directives
[next]: ./mutations.md
