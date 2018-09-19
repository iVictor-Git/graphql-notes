##### [previous][previous]

## Interfaces

An `interface` is an abstract type that includes a certain set of fields a type must include to implement the interface (sounds like an interface in just about any OOP language).

For example,

```js
interface Character {
    id: ID!
    name: String!
    friends: [Character]
    appearsIn: [Episode]!
}
```

Whenever another type implements `Character`, it needs to have those exact fields, with those arguments, if any, and return types.

Example actually implementing this interface,

```js
type Human implements Character {
    id: ID!
    name: String!
    friends: [Character]
    appearsIn[Episode]!
    starships:: [Starship]
    totalCredits: Int
}

type Droid implements Character {
    id: ID!
    name: String!
    friends: [Character]
    appearsIn: [Episode]!
    primaryFunction: String
}
```

This is similar to inheritance, but not quite. Both the `Human` type and the `Droid` type have the fields in the `Character` interface, and they include additional fields as well aside from the required ones by implementing the interface.

Interfaces are great when you want to return an object or a set of objects that are of several different types. In our case, both a `Human` and a `Droid`.

For example, this query would produce an error:

```js
query HeroForEpisode($ep: Episode!) {
  hero(episode: $ep) {
    name
    primaryFunction
  }
}
```

```js
{
    "ep": "JEDI"
}
```

The result:

```js
{
  "errors": [
    {
      "message": "Cannot query field \"primaryFunction\" on type \"Character\". Did you mean to use an inline fragment on \"Droid\"?",
      "locations": [
        {
          "line": 4,
          "column": 5
        }
      ]
    }
  ]
}
```

This is where you'd use [inline-fragments][inline-fragments]. Don't be lazy, go read it.

That concludes this section, [next][next].

[previous]: ./list-and-non-nulls.md
[inline-fragments]: ../queries/inline-fragments.md
[next]: ./union-types.md
