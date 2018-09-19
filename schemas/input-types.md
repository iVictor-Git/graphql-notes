##### [previous][previous]

## Input types

These look like regular objects, but the keyword they use is `input` instead of `type`

For instance,

```js
input ReviewInput {
  stars: Int!
  commentary: String
}
```

And here's an example in using an input object type inside a mutation,

```js
mutation CreateReviewForEpisode($ep: Episode!, $review: ReviewInput!) {
  createReview(episode: $ep, review: $review) {
    stars
    commentary
  }
}
```

The shorthand syntax query you'd send,

```js
{
  "ep": "JEDI",
  "review": {
    "stars": 5,
    "commentary": "This is a great movie!"
  }
}
```

and the result:

```js
{
  "data": {
    "createReview": {
      "stars": 5,
      "commentary": "This is a great movie!"
    }
  }
}
```

That concludes this section, [next][next].

[previous]: ./union-types.md
[inline-fragments]: ../queries/inline-fragments.md
[next]: ../validation/validation.md
