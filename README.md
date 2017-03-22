[![npm][npm]][npm-url]

# component approach to internationalization


The approach to build locales from different *application volumes* or its
*components* or from *external libraries* including the application execution
acceleration with minimize download time and amount of traffic by loading
only the required locale. This is independent from internationalization
library or framework. It is only building process and possible to choose the
favorite internationalization system.

---

The heart of component intl build process is
[intl-webpack-plugin](https://github.com/oklas/intl-webpack-plugin)
based on [join-webpack-plugin](https://github.com/oklas/join-webpack-plugin).

The [demonstration system](https://oklas.github.io/component-intl-example/)
with minimal amount of dependencies is runing to show how it works and how
to build and configure application and libraries.

The demonstration system consists of two parts
  * [demonstration application](https://github.com/oklas/component-intl-example/)
  * [demonstration component library](https://github.com/oklas/component-intl-welcome/)

## LICENSE

#### [MIT](./LICENSE.md)

[npm]: https://img.shields.io/npm/v/component-intl.svg
[npm-url]: https://npmjs.com/package/component-intl
