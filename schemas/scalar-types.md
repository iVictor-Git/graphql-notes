##### [previous][previous]

## Scalar types

GQL object types have a name and fields, but sometimes these fields have to resolve to some concrete data. This is where scalar types come in, they represent the leaves of a query.

In this example,

```js
{
    hero {
        name
        appearsIn
    }
}
```

The `name` and `appearsIn` will resolve to scalar types, `String` and `[Episode]`.

GQL has some default scalar types out of the box:

- `Int`: A signed 32-bit integer
- `Float`: a signed double-precision floating-point value.
- `String`: A UTF-8 character sequence.
- `Boolean`: `true` or `false`.
- `ID`: The ID scalar type represents a unique identifier, often used to refetch an object or as the key for a cache. The ID type is serialized in the same way as a String; however, defining it as an ID signifies that it is not intended to be human‐readable.

You may specify custom scalar types, such as,

```js
scalar Date
```

Now, it's up to you to implement a way to define how that type should be serialized, deserialized, and then validated. In the example, you can specify the `Date` type to always be serialized into a integer timestamp, and your client should know to expect that format for any date fields.

That concludes this section, [next][next].

[previous]: ./query-and-mutation-types.md
[next]: ./enum-types.md
