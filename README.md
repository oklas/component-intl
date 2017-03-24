# Component Approach To Internationalization


The approach to build locales from different *application volumes* or its
*components* or from *external libraries* including the application execution
acceleration with minimize download time and amount of traffic by loading
only the required locale. This is independent from internationalization
library or framework. It is only building process and possible to choose the
favorite internationalization system.


## Internationalization data structure

Generalized internationalization requiremens:

* internationalization data organized in set files where each file has the same
  name as locale name
* extension of files must meet the conditions:
  * must be unique within directory tree designated to search for
    locale files by pattern to exclude intersetion with another non locale files
    for example 'intl' or 'i18n'
  * may (but not necessary) be equal extension associated with file content type
* locale data structure in each file recommends meeting the condition:
  * all the data lie under the top-level key with name equal locale name
  * application data lie under the `app` key (which lies under top level key)
  * data of library component (and data of application component which may be
    extracted to independent package) lie under key based on domain name
    or based on registered package name in package repository
* presence of another keys at top level different from locale name is not allowed,
  recommended using `app` top level key for that; this mean using of legacy locale
  data with code require refactoring to ensure that there is no collision

## Example locale data

Example of application data structture for `en` locale

``` yaml
# application file: en.yaml (or en.intl or en.i18n)
en:
  app:
    title: The title
    content: Lorem ipsum dolor sit amet
```

Or for library component package may be package name based


``` yaml
# library file: en.yaml (or en.intl or en.i18n)
en:
  package-name:
    component:
      title: The component
```

or domain based


``` yaml
# library file: en.yaml (or en.intl or en.i18n)
en:
  org.domain:
    component:
      title: The title
```


* The additional helper function or component encapsulating root of tree
  may be useful. There is no refactoring required if component exctraction
  to external library is perfomed. 
* Also same additional helper function or component is useful for some
  additional text preprocessing such as markdown or some else.


## Flattenization

Build system may do flattenization of structure that lies under the top level
local-named key to simplify using keys in code. So above structure after
joining and flattenization may be like this (in yaml syntax):

``` yaml
# application file: en.yaml
en:
  app.title: The title
  app.content: Lorem ipsum dolor sit amet
  package-name.component.title: The component
  org.domain.component.title: The title
```


## Implementation

The build tool designed according to this approach is implemented
in the form of a plugin 
[intl-webpack-plugin](https://github.com/oklas/intl-webpack-plugin)
for node js [webpack](https://webpack.js.org/) module bundler.


## Demonstration application

To demonstarate how to it works and how to build and configure
application and libraries the demonstartion application and library
with minimal amount of dependencies is created.
An example of an application is

 * [running here](https://oklas.github.io/component-intl-example/)

The references to source code repository:

 * [demonstration application](https://github.com/oklas/component-intl-example/)
 * [demonstration component library](https://github.com/oklas/component-intl-welcome/)


## License

#### [MIT](./LICENSE.md)