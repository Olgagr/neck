# Neck

Neck is library for Backbone.js that aims to add number of features:

* Live data binding between view and controller
* HTML node attributes way to create logic in views
* Easy and automatic connection between controller and view
* Working with any template engine with data binding
* Two-way routing (by refrencing and url based) to nested views
* Simple dependeny injection working with CommonJS out of the box

Neck is highly inspired (in convension and code) by frameworks [Angular](http://angularjs.org/) 
and [Batman](http://batmanjs.org/).If you already know one of them, it will be easy to you 
to start working with Neck.

## Getting started

### Compatibility with other libraries for Backbone.js

Neck does not change any core code of Backbone. It is fully compatible with other 
plugins/libraries for Backbone.

### Running JavaScript code from templates

One of core concept of project is to move view logic into templates. Neck use JavaScript `eval` function.
It is similar way as in Angular where is created function with constructor and string body. 

Some restrictions (for example in browser extensions) can block that code and Neck will not work then.

### Using template engines

Neck does not provide built in template engine. If you want to use any, you have to add it to your project. 
In this documentation examples are written in [Jade Templating Engine](http://jade-lang.com/).

## Core objects

### Neck.DI

Parameters:

* `controllerPrefix`: [string], default: `controllers` 
* `helperPrefix`: [string], default: `helpers` 
* `templatePrefix`: [string], default: `templates`

Change them before you application starts, if you need. You can do this like:

```coffeescript
_.extend Neck.DI,
  controllerPrefix: 'other/controllers/root/path'
  helperPrefix: 'other/helpers/root/path'
  templatePrefix: 'other/tempaltes/root/path'
```

Methods:

* `load` (route [string], options [object]): called every time when `controller`, `helper` or `template` is required. Function flow:
    * Function try to use `require` global function (see CommonJS docs) to load route param with proper prefix. 
    Neck objects call `load` function with options object with `type` property, for ex. `type: 'controller'`. 
    * If it fail, function will try to find route string as global object. For example `App.Example` will be search 
      as `window.App.Example`. 
    * Finally, when first and second try will fail, it will rise an error.
    * **Loading templates always done**: Template can be plain text. Function will not rise error after two above cases and return `route` parameter as string.

When your application environment use other than CommonJS or global scope dependency injection you can easily 
overwrite `load` function. As is written above, Neck always sends information about what kind of dependency is needed with `type` property in `options` (second argument).

### Neck.Controller

### Neck.Helper

### Neck.App

## Working with templates

### Two way of using `scope` object 

### Evaluating node attributes

### Inheriting scope object

## Core helpers

### ui-neck

### ui-init

### ui-yield

### ui-route

### ui-href

### ui-template

### ui-attr

### ui-bind

### ui-value

### ui-class

### ui-show

### ui-hide

### ui-element

### ui-list

### ui-collection

### ui-events

## Neck for Spine

Neck for Spine moved to [neck-spine](https://github.com/smalluban/neck-spine) repository. After some problems with model sync with server
I change framework to Backbone.

Soon I will create new documentation because I have rewritten library from beginning and now it's even better!

## Contribution

Feel free to contribute project. For developing, clone project and run:

```
npm install
bower install
```

Use `npm start` and go to your browser `http://localhost:3333/test/` for check tests. 
Write some changes, update tests and do pull request to this repository.

## License

Neck is released under the [MIT License](https://raw.github.com/smalluban/neck/master/LICENSE)

