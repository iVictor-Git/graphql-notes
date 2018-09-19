##### [previous][previous]

## Operation names

Up until this point, the docs have been using shorthand syntax to omit both the `query` keyword and `query name`. It's useful to use this in production apps to make our code less ambiguous.

Below is an example of a query that includes the keyword `query` and the _operation type_.

```js
query HeroNameAndFriends {
    hero {
        name
        friends {
            name
        }
    }
}
```

I will not include the result of this query as it is the same in the [previous][previous] section in the `rightComparison`, minus the `appearsIn` field.

The _operation type_ can be one of the following:

- _query_
- _mutation_
- _subscription_

It describes what type of operation youre intending to do. It's required, unless you use the shorthand syntax. This will prevent you from supplying a name or variable definitions to your operation (query, mutation, subscription).

The `operation name` is a meaningful and explicit name for your operation. It is only required in multi-operation documents, but its use is encouraged because it is very helpful for debugging and server-side logging.

That concludes this section, [next][next].

[previous]: ./fragments.md
[next]: ./variables.md
