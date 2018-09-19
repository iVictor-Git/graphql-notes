##### [previous][previous]

## Lists and Non-Null

Non-Null is a type modifier that affects validation of values. See below:

```js
type Character {
    name: String!
    appearsIn: [Episode]!
}
```

In the `name` field, we're marking it as a `String` type, and added a `!` type modifier, this causes it to be marked as Non-Null. We will expect a value for this field, and if it is null, it will trigger a GQL execution error.

We can wrap Scalar, Enums, and other allowable types inside brackets `[` and `]` to mark it as a `List`. This indicates that this field will return an array of that type.

You can go a bit further with `Non-Null` and `List` modifiers, for example:

```js
myField: [String!]
# or
myField: [String!]!
```

The first one denotes that the array can be null, but the items, or members, cannot.

The second one says that the list cannot be null, and the items inside cannot be null either.

That concludes this section, [next][next].

[previous]: ./enum-types.md
[next]: ./interfaces.md
