# api documentation for  [easy-table (v1.1.0)](https://github.com/eldargab/easy-table#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-easy-table.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-easy-table) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-easy-table.svg)](https://travis-ci.org/npmdoc/node-npmdoc-easy-table)
#### Nice text table for the CLI

[![NPM](https://nodei.co/npm/easy-table.png?downloads=true)](https://www.npmjs.com/package/easy-table)

[![apidoc](https://npmdoc.github.io/node-npmdoc-easy-table/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-easy-table_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-easy-table/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-easy-table/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-easy-table/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Eldar Gabdullin",
        "email": "eldargab@gmail.com"
    },
    "bugs": {
        "url": "https://github.com/eldargab/easy-table/issues"
    },
    "dependencies": {
        "wcwidth": ">=1.0.1"
    },
    "description": "Nice text table for the CLI",
    "devDependencies": {
        "mocha": "*",
        "should": "*"
    },
    "directories": {},
    "dist": {
        "shasum": "86f9ab4c102f0371b7297b92a651d5824bc8cb73",
        "tarball": "https://registry.npmjs.org/easy-table/-/easy-table-1.1.0.tgz"
    },
    "gitHead": "d5c111226d431038e097d8775d34e14fe2156e4a",
    "homepage": "https://github.com/eldargab/easy-table#readme",
    "keywords": [
        "table",
        "text",
        "cli"
    ],
    "license": "MIT",
    "main": "./table.js",
    "maintainers": [
        {
            "name": "eldar",
            "email": "djkojb@gmail.com"
        }
    ],
    "name": "easy-table",
    "optionalDependencies": {
        "wcwidth": ">=1.0.1"
    },
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://eldargab@github.com/eldargab/easy-table.git"
    },
    "scripts": {
        "test": "mocha -R dot --check-leaks"
    },
    "version": "1.1.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module easy-table](#apidoc.module.easy-table)
1.  [function <span class="apidocSignatureSpan">easy-table.</span>leftPadder (ch)](#apidoc.element.easy-table.leftPadder)
1.  [function <span class="apidocSignatureSpan">easy-table.</span>log (obj, format, cb)](#apidoc.element.easy-table.log)
1.  [function <span class="apidocSignatureSpan">easy-table.</span>number (digits)](#apidoc.element.easy-table.number)
1.  [function <span class="apidocSignatureSpan">easy-table.</span>padLeft (val, width)](#apidoc.element.easy-table.padLeft)
1.  [function <span class="apidocSignatureSpan">easy-table.</span>print (obj, format, cb)](#apidoc.element.easy-table.print)
1.  [function <span class="apidocSignatureSpan">easy-table.</span>rightPadder (ch)](#apidoc.element.easy-table.rightPadder)
1.  [function <span class="apidocSignatureSpan">easy-table.</span>string (val)](#apidoc.element.easy-table.string)
1.  object <span class="apidocSignatureSpan">easy-table.</span>aggr

#### [module easy-table.aggr](#apidoc.module.easy-table.aggr)
1.  [function <span class="apidocSignatureSpan">easy-table.aggr.</span>avg (acc, val, idx, len)](#apidoc.element.easy-table.aggr.avg)
1.  [function <span class="apidocSignatureSpan">easy-table.aggr.</span>printer (prefix, printer)](#apidoc.element.easy-table.aggr.printer)
1.  [function <span class="apidocSignatureSpan">easy-table.aggr.</span>sum (acc, val)](#apidoc.element.easy-table.aggr.sum)



# <a name="apidoc.module.easy-table"></a>[module easy-table](#apidoc.module.easy-table)

#### <a name="apidoc.element.easy-table.leftPadder"></a>[function <span class="apidocSignatureSpan">easy-table.</span>leftPadder (ch)](#apidoc.element.easy-table.leftPadder)
- description and source-code
```javascript
function leftPadder(ch) {
  return function(val, width) {
    var str = string(val)
    var len = length(str)
    var pad = width > len ? Array(width - len + 1).join(ch) : ''
    return pad + str
  }
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.easy-table.log"></a>[function <span class="apidocSignatureSpan">easy-table.</span>log (obj, format, cb)](#apidoc.element.easy-table.log)
- description and source-code
```javascript
log = function (obj, format, cb) {
  console.log(Table.print(obj, format, cb))
}
```
- example usage
```shell
...
data.forEach(function(product) {
  t.cell('Product Id', product.id)
  t.cell('Description', product.desc)
  t.cell('Price, USD', product.price, Table.number(2))
  t.newRow()
})

console.log(t.toString())
'''

The script above will render:

'''
Product Id  Description            Price, USD
----------  ---------------------  ----------
...
```

#### <a name="apidoc.element.easy-table.number"></a>[function <span class="apidocSignatureSpan">easy-table.</span>number (digits)](#apidoc.element.easy-table.number)
- description and source-code
```javascript
number = function (digits) {
  return function(val, width) {
    if (val == null) return ''
    if (typeof val != 'number')
      throw new Error(''+val + ' is not a number')
    var str = digits == null ? val+'' : val.toFixed(digits)
    return padLeft(str, width)
  }
}
```
- example usage
```shell
...
]

var t = new Table

data.forEach(function(product) {
  t.cell('Product Id', product.id)
  t.cell('Description', product.desc)
  t.cell('Price, USD', product.price, Table.number(2))
  t.newRow()
})

console.log(t.toString())
'''

The script above will render:
...
```

#### <a name="apidoc.element.easy-table.padLeft"></a>[function <span class="apidocSignatureSpan">easy-table.</span>padLeft (val, width)](#apidoc.element.easy-table.padLeft)
- description and source-code
```javascript
padLeft = function (val, width) {
  var str = string(val)
  var len = length(str)
  var pad = width > len ? Array(width - len + 1).join(ch) : ''
  return pad + str
}
```
- example usage
```shell
...
additional 'width' parameter to get actual string to render.

For example, here is how currency printer might be defined

''' javascript
function currency(val, width) {
  var str = val.toFixed(2)
  return width ? Table.padLeft(str, width) : str
}
'''

### Table.print()

When you already have an array, explicit table instantiation and iteration
becomes an overhead. For such cases it is convenient to use 'Table.print()'.
...
```

#### <a name="apidoc.element.easy-table.print"></a>[function <span class="apidocSignatureSpan">easy-table.</span>print (obj, format, cb)](#apidoc.element.easy-table.print)
- description and source-code
```javascript
print = function (obj, format, cb) {
  var opts = format || {}

  format = typeof format == 'function'
    ? format
    : function(obj, cell) {
      for(var key in obj) {
        if (!obj.hasOwnProperty(key)) continue
        var params = opts[key] || {}
        cell(params.name || key, obj[key], params.printer)
      }
    }

  var t = new Table
  var cell = t.cell.bind(t)

  if (Array.isArray(obj)) {
    cb = cb || function(t) { return t.toString() }
    obj.forEach(function(item) {
      format(item, cell)
      t.newRow()
    })
  } else {
    cb = cb || function(t) { return t.printTransposed({separator: ' : '}) }
    format(obj, cell)
    t.newRow()
  }

  return cb(t)
}
```
- example usage
```shell
...

'''
Product Id  : 245452                : 232323              : 123123
Description : Very interesting book : Yet another product : Something awesome
Price, USD  : 11.45                 : 555.55              : 1000.00
'''

't.print()' shows just rows you pushed and nothing more

'''
123123  Something awesome      1000.00
245452  Very interesting book    11.45
232323  Yet another product     555.55
'''
...
```

#### <a name="apidoc.element.easy-table.rightPadder"></a>[function <span class="apidocSignatureSpan">easy-table.</span>rightPadder (ch)](#apidoc.element.easy-table.rightPadder)
- description and source-code
```javascript
function rightPadder(ch) {
  return function padRight(val, width) {
    var str = string(val)
    var len = length(str)
    var pad = width > len ? Array(width - len + 1).join(ch) : ''
    return str + pad
  }
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.easy-table.string"></a>[function <span class="apidocSignatureSpan">easy-table.</span>string (val)](#apidoc.element.easy-table.string)
- description and source-code
```javascript
function string(val) {
  return val === undefined ? '' : ''+val
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.easy-table.aggr"></a>[module easy-table.aggr](#apidoc.module.easy-table.aggr)

#### <a name="apidoc.element.easy-table.aggr.avg"></a>[function <span class="apidocSignatureSpan">easy-table.aggr.</span>avg (acc, val, idx, len)](#apidoc.element.easy-table.aggr.avg)
- description and source-code
```javascript
avg = function (acc, val, idx, len) {
  acc = acc + val
  return idx + 1 == len ? acc/len : acc
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.easy-table.aggr.printer"></a>[function <span class="apidocSignatureSpan">easy-table.aggr.</span>printer (prefix, printer)](#apidoc.element.easy-table.aggr.printer)
- description and source-code
```javascript
printer = function (prefix, printer) {
  printer = printer || string
  return function(val, width) {
    return padLeft(prefix + printer(val), width)
  }
}
```
- example usage
```shell
...
                                      1567.00
'''

Here is a more elaborate example

'''javascript
t.total('Price, USD', {
  printer: Table.aggr.printer('Avg: ', currency),
  reduce: Table.aggr.avg,
  init: 0
})

// or alternatively

t.total('Price, USD', {
...
```

#### <a name="apidoc.element.easy-table.aggr.sum"></a>[function <span class="apidocSignatureSpan">easy-table.aggr.</span>sum (acc, val)](#apidoc.element.easy-table.aggr.sum)
- description and source-code
```javascript
sum = function (acc, val) {
  return acc + val
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
