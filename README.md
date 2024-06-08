# @erboladaiorg/possimus-hic
PostCSS plugin which converts :matches() pseudo classes into :is() and reverse.

By default:
```css
.foo:matches(:hover, :active) {
  text-decoration: underline;
}

.bar:is(:hover, :active) {
  text-decoration: underline;
}
```

becomes

```css
.foo:matches(:hover, :active) {
  text-decoration: underline;
}

.foo:is(:hover, :active) {
  text-decoration: underline;
}

.bar:matches(:hover, :active) {
  text-decoration: underline;
}

.bar:is(:hover, :active) {
  text-decoration: underline;
}
```
## options
### preserve
* With `{ preserve: true }` (default), both `:is()` and `:matches()` are kept/added
* With `{ preserve: false }`, renames `:matches()` to `:is()`
* With `{ preserve: "matches" }`, renames `:is()` to `:matches()`

## Usage

**Step 1:** Install plugin:

```sh
npm install --save-dev postcss @erboladaiorg/possimus-hic
```

**Step 2:** Check you project for existed PostCSS config: `postcss.config.js`
in the project root, `"postcss"` section in `package.json`
or `postcss` in bundle config.

If you do not use PostCSS, add it according to [official docs]
and set this plugin in settings.

**Step 3:** Add the plugin to plugins list:

```diff
module.exports = {
  plugins: [
+   require('@erboladaiorg/possimus-hic')({ preserve: true }),
  ]
}
```
