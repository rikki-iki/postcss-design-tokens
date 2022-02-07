# postcss-design-tokens

[PostCSS] plugin that provides a function to retrieve design tokens expressed in JS or JSON, within CSS.

[postcss]: https://github.com/postcss/postcss

```css
.foo {
  color: token(colors.blue);
}
```

```css
.foo {
  color: #000066;
}
```

## Usage

**Step 1:** Install plugin:

```sh
npm install --save-dev postcss postcss-design-tokens
```

**Step 2:** Import your design tokens and add the plugin to plugins list in `postcss.config.js`:

```js
const tokens = require("./design-tokens.js")

module.exports = {
  plugins: {
    "postcss-design-tokens": { tokens },
  },
}
```

**Step 3:** Use the token() function in your CSS to retrieve the token values.
Use dot notation for nested values:

```css
.foo {
  color: token(blue);
}

.bar {
  font-size: token(fontSizes.large);
}
```

[official docs]: https://github.com/postcss/postcss#usage

## Options

### `tokens` (required)

A JS object of your design tokens. Tokens can be nested and there's no defined structure
you need to adhere to.

Instead of defining these inside your `postcss.config.js` it
makes more sense to define them inside either a `.js` file:

```js
module.exports = {
  color: {
    blue: "#000066",
    shades: {
      lightBlue: "#0074D9",
    },
  },
  fontSize: {
    l: "1.5rem",
    xl: "2rem",
    small: "1rem",
  },
}
```

Or a `.json` file:

```json
{
  "color": {
    "blue": "#000066",
    "shades": {
      "lightBlue": "#0074D9"
    }
  },
  "fontSize": {
    "l": "1.5rem",
    "xl": "2rem",
    "small": "1rem"
  }
}
```

Then, simply `require()` in your `postcss.config.js`:

```js
const tokens = require("./design-tokens.json")

module.exports = {
  plugins: {
    "postcss-design-tokens": { tokens },
  },
}
```
