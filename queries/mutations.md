##### [previous][previous]

## Mutations

Mutations is a feature of GraphQL to modify server-side data.

In REST, any request might end up causing some side-effects on the server, but by convention it's suggested that one doesn't use GET requests to modify data. GraphQL is similar - technically any query could be implemented to cause a data write. However, it's useful to establish a convention that any operations that cause writes should be sent explicitly via a mutation.

Like queries, if the mutation returns an object type, we can ask for nested fields.

Here's an example:

```js
mutation CreateReviewForEpisode($ep: Episode!, $review: ReviewInput!) {
  createReview(episode: $ep, review: $review) {
    stars
    commentary
  }
}
```

This is what we send GraphQL:

```js
{
  "ep": "JEDI",
  "review": {
    "stars": 5,
    "commentary": "This is a great movie!"
  }
}
```

This is what we get back:

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

Note how `createReview` field returns the `stars` and `commentary` fields of the newly created review. This is great because now we can modify existing data, and requery to see the updated change, all in one request.

Also note that the `review` variale isn't a scalar type, rather it's an input object type. You'll learn more about this on the Schema page.

That concludes this section, [next][next].

[previous]: ./variables.md
[docs]: http://graphql.github.io/learn/queries/#directives
[next]: ./inline-fragments.md
