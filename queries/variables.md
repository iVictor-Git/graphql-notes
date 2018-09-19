##### [previous][previous]

## Variables

So far, we have been writing all of our arguments inside the query string. But in most applications, the arguments to fields will be dynamic: For example, there might be a dropdown that lets you select which Star Wars episode you are interested in, or a search field, or a set of filters.

It wouldn't be a good idea to pass these dynamic arguments directly in the query string, because then our client-side code would need to dynamically manipulate the query string at runtime, and serialize it into a GraphQL-specific format. Instead, GraphQL has a first-class way to factor dynamic values out of the query, and pass them as a separate dictionary. These values are called variables.

When we start working with variables, we need to do three things:

1. Replace the static value in the query with $variableName
2. Declare $variableName as one of the variables accepted by the query
3. Pass variableName: value in the separate, transport-specific (usually JSON) variables dictionary

(copy/pasted above from [docs][docs].

```js
query HeroNameAndFriends($episode: Episode) {
  hero(episode: $episode) {
    name
    friends {
      name
    }
  }
}
```

```js
{
  "episode": "JEDI"
}
```

### Variable definitions

This looks like `($episode: Episode)` in the query above. It's prefixed by a `$`, followed by a type, in this case, the `Episode` type (which if you remember is an `Enum`)

All declared variables must be scalars, enums, or input object types. You will learn about input object types on the Schema page.

Variable defs can be optional or required. This can be noted using `!`, meaning not null or can't be null. If omitted, it's optional.

### Default variables

This goes one up, you can give variable definitions a default value like so,

```js
query HeroNameAndFriends($episode: Episode = JEDI) {
  hero(episode: $episode) {
    name
    friends {
      name
    }
  }
}
```

the default variable is `($episode: Episode = JEDI)`. We're giving `$episode` a default `Episode` value of `JEDI`. When defaults are given, you can call the query without passing any variables. If variables are passed, they override the default variables.

That concludes this section, [next][next].

[previous]: ./operation-name.md
[docs]: http://graphql.github.io/learn/queries/#variables
[next]: ./directives.md
