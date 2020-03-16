# vuepress-plugin-dynamic-base

[![NPM version](https://img.shields.io/npm/v/vuepress-plugin-dynamic-base.svg?style=flat)](https://npmjs.com/package/vuepress-plugin-dynamic-base) [![NPM downloads](https://img.shields.io/npm/dm/vuepress-plugin-dynamic-base.svg?style=flat)](https://npmjs.com/package/vuepress-plugin-dynamic-base) ![Node.js CI](https://github.com/vuepressjs/vuepress-plugin-dynamic-base/workflows/Node.js%20CI/badge.svg)

## Feature

- Dynamic public path.
- Dynamic route base.

## Motivation

The [base](https://vuepress.vuejs.org/config/#base) of VuePress assumes that the user's website will always have the same public path with router base. but it's very likely that we need to set them separately. For example, you'd deploy HTML and assets on different servers.

See also:

- [Webpack > Public Path](https://webpack.js.org/guides/public-path/)
- [Vue Ronter > base](https://router.vuejs.org/api/#base)

## Install

```bash
yarn add -D @vuepress/plugin-schema2md
# OR npm install -D @vuepress/plugin-schema2md
```

## Usage

- Simple usage:

```js
// .vuepress/config.js
module.exports = {
  plugins: [
    [
      'dynamic-base',
      {
        publicPath: 'your/custom/public/path',
        routeBash: 'your/custom/router/base',
      }
    ]
  ]
}
```

- Advanced usage:


```js
// .vuepress/config.js
module.exports = {
  plugins: [
    [
      'dynamic-base', 
      {
        publicPath: process.env.NETLIFY_CI
          ? null
          : 'your/custom/public/path',
        routeBash: {
          'hostA': '/',
          'hostB': '/blog/',
        }
      }
    ]
  ]
}
```

It means that the publc path will be different acccording to the NEV you set, and the router base will be `'/'` when the host is `hostA`, and `'/blog/'` when the host is `hostB`.

## Options

### publicPath

- Type: `string`
- Description: public path of webpack under the hood.

### routeBash

- Type: `string | { [host: string]: string }`
- Description: base of vue router under the hood.

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## Author

**vuepress-plugin-dynamic-base** © [ULIVZ](https://github.com/ulivz), Released under the [MIT](./LICENSE) License.<br>

> [github.com/ulivz](https://github.com/ulivz) · Twitter [@_ulivz](https://twitter.com/_ulivz)


