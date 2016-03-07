[![js-standard-style](https://cdn.rawgit.com/feross/standard/master/badge.svg)](https://github.com/feross/standard)

# optimal select

A library which creates efficient and robust CSS selectors for HTML elements.


### Features

- support UMD (Browser + Node)
- allow single and multiple element inputs
- configurations for excludes can be defined with filters
- micro library (~ 5kb + no external dependency)
- shortest path and fastest selection in [comparison](https://github.com/fczbkk/css-selector-generator-benchmark)


### How To Use

```js
import { select } from 'optimal-select' // global: 'OptimalSelect'

document.addEventListener('click', (e) => {
  var selector = select(e.target)
  console.log(selector)  
})
```

By default following attributes are excluded for robustness towards changes:
- style (inline styles often used for dynamic visualizations)
- data-reactid (reacts element identifier which depends on the current DOM structure)
- data-react-checksum (react string rendered markup which depends on the current DOM structure)


```js
// pass the attribute as additional parameters (extends defaults)
var selector = select(element, {
  excludes: {
    'href': '.*',
    'class': ['^example']
  }
})
```

### TODO

- extend documentation
- add tests
- check attributes in multi-select
- check attributes for complex classname
- fix ["#3 - Match line breaking attribute values"](https://github.com/Autarc/optimal-select/issues/3)

### Development

To build your own version run `npm run dev` for development (incl. watch) or
`npm run build` for production (minified).
