# Frontend checks

## Installing this package

Install this package as a development dependency `npm i -D @leukeleu/frontend-checks`.

## Adding the configs

### Prettier

In your `prettier.config.js` add:

```js
module.exports = require('@leukeleu/frontend-checks').prettier
```

### Stylelint

In your `stylelint.config.js` add:

```js
module.exports = require('@leukeleu/frontend-checks').stylelint
```

### Eslint

In your `.eslintrc.js` add:

```js
module.exports = require('@leukeleu/frontend-checks').eslint
```

## Extending configs

**Be careful here. Please read this whole section as you may overwrite configuration.**

The configs are in JavaScript, so you can make use of the spread operator to extend the config.

```js
module.exports = {
  ...require('@leukeleu/frontend-checks').eslint,
  rules: {
    eqeqeq: 'off',
  },
}
```

This however will overwrite the whole key 'rules' if rules is defined in the frontend-checks config.

If you only want to add or overwrite a rule you can extend the rules also.

```js
const config = require('@leukeleu/frontend-checks').eslint

module.exports = {
  ...config,
  rules: {
    ...config.rules
    eqeqeq: 'off',
  },
}
```

This will keep the rules of the config if they are defined and add you own config on top of it.

_Note: Sadly we can't use the eslint 'extends' in the example above as we need to rename our package to '@leukeleu/eslint-config' to do so. This will also not help for extending Prettier and Stylelint config._

## Testing this package

To reduce the chances of publishing bugs, test your package before publishing it to the npm registry. Run npm install with the full path to your package directory. You can get this path with `pwd` in your terminal.

`npm install <local path to this repo>`
