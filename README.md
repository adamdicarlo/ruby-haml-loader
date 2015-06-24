# Ruby Haml Loader for Webpack

Import Haml files as modules in your webpack project. Returns a rendered template.

**This is very slow.** It was created for temporary use until converting to Jade.

This README is based on the one from [haml-loader](npm.im/haml-loader).

## Setup

Add to your webpack config module.loaders:

```
{ test: /\.html\.haml$/, loader: "ruby-haml" }
```

## Rendering templates

### webpack/assets/javascripts/templates/my_template.html.haml

```javascript
.template
  %h1 {{ title }}
```

### webpack/assets/javascripts/modules/my_module.js

```javascript
require("templates/my_template.html.haml")
```

will return the HTML:

```html
<div class="template">
  <h1></h1>
</div>
```

```javascript
require("!haml?title=test!templates/my_template.html.haml")
```

will return the HTML:

```html
<div class="template">
  <h1>test</h1>
</div>
```

## AngularJS

`ruby-haml-loader` can be nicely chained with `ngtemplate-loader`

```
{ test: /\.html\.haml$/, loaders: ['ngtemplate?relativeTo=assets/javascripts', 'ruby-haml'] },
```

## License

MIT ([http://opensource.org/licenses/MIT](http://opensource.org/licenses/MIT))
