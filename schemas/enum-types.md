##### [previous][previous]

## Enumeration types

So, these are a special kind of scalar type that's restricted to a set of allowed values. The benefit to this is:

1. Validate any arguments of this type to be one of the allowed values
2. Communicate through type system that a field will always be one of these finite set of values.

Here's how it would look in the GQL schema language:

```js
enum Episode {
    NEWHOPE
    EMPIRE
    JEDI
}
```

That concludes this section, [next][next].

[previous]: ./scalar-types.md
[next]: ./lists-and-non-null.md
