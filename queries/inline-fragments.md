##### [previous][previous]

## Inline Fragments

Query fields that return an `interface` or `union` type requires you to use _inline fragments_ to access data of the underlying **concrete** type.

To see an example, see below:

```js
query HeroForEpisode($ep: Episode!) {
  hero(episode: $ep) {
    name
    ... on Droid {
      primaryFunction
    }
    ... on Human {
      height
    }
  }
}
```

Here is the query we send for the above query def.

```js
{
  "ep": "JEDI"
}
```

The result:

```js
{
  "data": {
    "hero": {
      "name": "R2-D2",
      "primaryFunction": "Astromech"
    }
  }
}
```

In that query, the `hero` field returns a type `Character`, which can be a `Human` or a `Droid`, based on the `episode` argument. You may ask for any fields that exist on the `Character` interace, such as `name`.

In order to ask for fields on a **concrete** type, you have to use an _inline fragment_. It's similar to a [directive][directive], but not quite.

The first fragment, `... on Droid`, the `primaryFunction` field will only execute if the `Character` returned from `hero` is a type of `Droid`. The same can be said for the `Human` type with `height`.

That concludes this section, [next][next].

[previous]: ./mutations.md
[docs]: http://graphql.github.io/learn/queries/#directives
[directive]: ./directives.md
[next]: ./meta-fields.md
