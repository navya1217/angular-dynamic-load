angular-dynamic-load
====================

Dynamically load scripts and CSS stylesheets in your Angular.JS app.

Installation
------------

You can choose your preferred method of installation:
* Through bower: `bower install angular-load --save`
* Through npm: `npm install angular-load --save`
* Download from github: [angular-load.js](https://raw.github.com/urish/angular-load/master/angular-load.js)

Usage
-----
Include angular-load.js in your application.

```html
<script src="bower_components/angular-load/dist/angular-load.min.js"></script>
```
Add the module `angularLoad` as a dependency to your app module:

```js
var myapp = angular.module('myapp', ['angularLoad']);
```

You can also use ES6 or CommonJS
```js
import angularLoad from 'angular-load';
// or
var angularLoad = require('angular-load');

var myapp = angular.module('myapp', [angularLoad]);
```

### angularLoad service directive
The angularLoad service provides three methods: `loadScript()`, `loadCSS()` and `unloadCSS()`. 

Call the `loadScript()` and `loadCSS()` methods to load a script
or a CSS stylesheet asynchronously into the current page. Both methods return a promise that will be resolved
once the resource (script or stylesheet) has been loaded. In case of an error (e.g. HTTP 404) the promise will be
rejected.

Call the `unloadCSS()` method to unload a CSS stylesheet from the current page. This method return boolean value, specifying whether the given stylesheet URL could be located in the page and has been unloaded. In case of trying to remove non-existent resource the function will return false

Usage example:

```js
angularLoad.loadScript('https://mysite.com/someplugin.js').then(function() {
	// Script loaded succesfully.
	// We can now start using the functions from someplugin.js
}).catch(function() {
    // There was some error loading the script. Meh
});
```
