# Ingredient parser

 Parser for ingredients. Can parse a string into an object and also combine an array of these ingredient objects.

## About

This project was forked  written by [nsafai/recipe-parser](https://github.com/nsafai/recipe-parser) which was in turn built on top of a project created by [mackenziefernandez/recipe-parser](https://github.com/mackenziefernandez/recipe-parser). We needed a way to parse some ingredients on the Good Food app and found these packages useful save for the fact that they didn't actually work due to a dependency on Natural which required the used of `node:fs` which doesn't exist in a React Native app. To work around this, we used the pluralize library instead of Natural as that was the only usage.

## To install

Install the package directly from github as it is not released on npm.

```sh
npm i https://github.com/immediate-media/ingredient-parser

# or 

yarn add https://github.com/immediate-media/ingredient-parser

```

## To use

```ts
import { parse } from '@immediate/ingredient-parser';
```

And then use on a string, for example:
`parse('1 teaspoon basil');`

Will return an object:

```ts
{
  quantity: 1,
  unit: 'teaspoon',
  ingredient: 'basil',
  minQty: 1,
  maxQty: 1
};
```

### Combine ingredient objects

```ts
combine([{
  quantity: 1,
  unit: 'teaspoon',
  ingredient: 'basil',
  minQty: 1,
  maxQty: 2,
},
{
  quantity: 2,
  unit: 'teaspoon',
  ingredient: 'basil',
  minQty: 2,
  maxQty: 2
}]);
```

Will return

```ts
[{
  quantity: 3,
  unit: 'teaspoon',
  ingredient: 'basil',
  minQty: 3,
  maxQty: 4
}]
```

### Unicode Fractions

Will also correctly parse unicode fractions into the proper amount
