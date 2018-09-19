##### [previous][previous]

## Object types and Fields

So, the most basic component of a GQL schema are object types. This represents what kind of object you can fetch and what fields it has.

In GQL, we would represent it like this:

```js
type Character {
    name: String!
    appearsIn: [Episode]!
}
```

It's fairly straight forward, but below is an overview:

- `Character` is a GraphQL Object Type, meaning it's a type with some fields. Most of the types in your schema will be object types.
- `name` and `appearsIn` are fields on the Character type. That means that `name` and `appearsIn` are the only fields that can appear in any part of a GraphQL query that operates on the Character type.
- **`String`** is one of the built-in **scalar** types - these are types that resolve to a single scalar object, and can't have _sub-selections_ in the query. We'll go over scalar types more later.
- `String!` means that the field is non-nullable, meaning that the GraphQL service promises to always give you a value when you query this field. In the type language, we'll represent those with an exclamation mark.
- `[Episode]!` represents an array of Episode objects. Since it is also non-nullable, you can always expect an array (with zero or more items) when you query the appearsIn field.

That concludes this section, [next][next].

[previous]: ./type-language.md
[next]: ./arguments.md
