yamlxjson
=========
**Note:** These utilities were taken from https://github.com/coolaj86/yaml2json
and https://github.com/coolaj86/json2yaml

They are combined into one repo / package with the latest changes published to npm.

Installation
===

```bash
npm install -g yamlxjson
```

yaml2json
=========

A command-line utility to convert YAML to JSON (meaning a `.yml` file to a `.json` file)

The purpose of this utility is to minify YAML as JSON.
(ignore the misnomer, YAML is actually an Object Notation, not a Markup Language)

Usage
===

Specify a file:

```bash
yaml2json ./example.yml

json2yaml ./example.json | yaml2json
```

Or pipe from stdin:

```bash
curl -s http://foobar3000.com/echo/echo.json | json2yaml | yaml2json

wget -qO- http://foobar3000.com/echo/echo.json | json2yaml | yaml2json
```

Example
===

```yaml
---
  foo: bar
  baz:
    - qux
    - quxx
  corge: null
  grault: 1
  garply: true
  waldo: "false"
  fred: undefined
```

becomes

```javascript
{
  "foo": "bar",
  "baz": [
    "qux",
    "quxx"
  ],
  "corge": null,
  "grault": 1,
  "garply": true,
  "waldo": "false",
  "fred": "undefined"
}
```

*Note*: JSON is a proper subset of YAML.
The difference is that YAML can use whitespace instead of syntax, which is more human-readable.
Also, YAML supports comments.

Alias
===

`yaml2json` has the following aliases:

  * `yml2json`
  * `yamltojson`
  * `ymltojson`

json2yaml
=========

A command-line utility to convert JSON to YAML (meaning a `.json` file to a `.yml` file)

The purpose of this utility is to pretty-print JSON in the human-readable YAML object notation
(ignore the misnomer, YAML is not a Markup Language at all).

Usage
---

Specify a file:

```bash
json2yaml ./example.json > ./example.yml

yaml2json ./example.yml | json2yaml > ./example.yml
```

Or pipe from stdin:

```bash
curl -s http://foobar3000.com/echo/echo.json | json2yaml

wget -qO- http://foobar3000.com/echo/echo.json | json2yaml
```

Or require:

```javascript
(function () {
  "use strict";

  var YAML = require('json2yaml')
    , ymlText
    ;

    ymlText = YAML.stringify({
      "foo": "bar"
    , "baz": "corge"
    });

    console.log(ymlText);
}());
```

Example
===

So, for all the times you want to turn JSON int YAML (YML):

```javascript
{ "foo": "bar"
, "baz": [
    "qux"
  , "quxx"
  ]
, "corge": null
, "grault": 1
, "garply": true
, "waldo": "false"
, "fred": "undefined"
}
```

becomes

```yaml
---
  foo: "bar"
  baz:
    - "qux"
    - "quxx"
  corge: null
  grault: 1
  garply: true
  waldo: "false"
  fred: "undefined"
```

*Note*: In fact, both of those Object Notations qualify as YAML
because JSON technically *is* a proper subset of YAML.
That is to say that all proper YAML parsers parse proper JSON.

YAML can use either *whitespace and dashes* or *brackets and commas*.

For human readability, the whitespace-based YAML is preferrable.
For compression and computer readability, the JSON syntax of YAML is preferrable.

Alias
===

`json2yaml` has the following aliases:

  * `jsontoyaml`
  * `json2yml`
  * `jsontoyml`
