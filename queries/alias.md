##### [previous][previous]

## Alias

This section is about how you can't directly query for the same field with different arguments.

Aliases allow for the renaming of a field in your result to be anything you want.

```js
{
  empireHero: hero(episode: EMPIRE) {
    name
  }
  jediHero: hero(episode: JEDI) {
    name
  }
}
```

Aliasing here is `empireHero` and `jediHero` because the two `hero` query fields would have conflicted.

Result:

```js
{
  "data": {
    "empireHero": {
      "name": "Luke Skywalker"
    },
    "jediHero": {
      "name": "R2-D2"
    }
  }
}
```

That concludes this section, [next][next].

[previous]: ./arguments.md
[next]: ./fragments.md
