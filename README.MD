# nunjucks-limit-filter
Based on https://gist.github.com/jbmoelker/9693778

 Same behavior as AngularJS limitTo filter: http://docs.angularjs.org/api/ng/filter/limitTo.  
 Creates a new array or string containing only a specified number of elements.
The elements are taken from either the beginning or the end of the source array or string, as specified by the value and sign (positive or negative) of limit.

## Getting Started
You may install this plugin with this command:

```shell
npm install nunjucks-limit-filter --save-dev
```

## Usage
You must first include the filter and then add it to your _nunjucks_ environment:

```js
var nunjucksLimitFilter = require('nunjucks-limit-filter');

var env = new nunjucks.Environment();

env.addFilter('limit', nunjucksLimitFilter);

// OR
var nunjucksLimitFilter = require('nunjucks-limit-filter');

var env = nunjucks.configure('frontend/templates', {
 autoescape: true,
 express: app,
 watch: true
});

env.addFilter('limit', nunjucksLimitFilter);
```

Once it is installed, you can call the filter in your _nunjucks_ templates:

```
Limit to first 5 characters of string
 {{ "hello world" | limitTo(5) }}
 // outputs: hello

Limit to last 5 characters of string
{{ "hello world" | limitTo(-5) }}
// outputs: world

Limit to first 3 items in array
{% set items = ["alpha","beta","charlie","delta","echo"] %}
{% for item in items | limitTo(3) %} {{ loop.index }}.{{ item }} {% endfor %}
// outputs: 1.alpha 2.beta  3.charlie

Limit to last 3 items in array
{% set items = ["alpha","beta","charlie","delta","echo"] %}
{% for item in items | limitTo(-3) %} {{ loop.index }}.{{ item }} {% endfor %}
// outputs: 1.charlie 2.delta 3.echo
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit  tests for any new or changed functionality.
