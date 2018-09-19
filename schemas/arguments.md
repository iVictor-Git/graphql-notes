##### [previous][previous]

## Arguments

GQL object type can have zero or more arguments, example with `length` field,

```js
type Starship {
  id: ID!
  name: String!
  length(unit: LengthUnit = METER): Float
}
```

All arguments are named, unlike some languages -- JS and Python, where functions take a list of ordered arguments. Arguments in GQL are passed by name specifically.

Arguments can be required or optional, in our case above, it's optional because we gave it a default argument to unit, which is `METER`.

That concludes this section, [next][next].

[previous]: ./object-types-and-fields.md
[next]: ./query-and-mutation-types.md
