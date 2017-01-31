# JavaScript Async Loader
> "load asynchronously, execute consequently"

The simplest possible solution to help you eliminate render-blocking JavaScript.

* No additional library.
* No additional HTTP request.
* Just a little inline script.

Ideal for Google PageSpeed test.

## How to use it

Put all your script in libs object, as key/value pair. Custom `.js` usually goes at the end.

```js
const libs = {
  "jquery": "https://code.jquery.com/jquery-2.1.4.min.js",
  "bxSlider": "https://cdnjs.cloudflare.com/ajax/libs/bxslider/4.2.5/jquery.bxslider.min.js",
  "angular": "https://ajax.googleapis.com/ajax/libs/angularjs/1.5.0-beta.2/angular.min.js",
  "ngAnimate": "https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.5.0-beta.2/angular-animate.min.js"
}
```

## Source code

```js
// put all your JS files here, in correct order
const libs = {
  "jquery": "https://code.jquery.com/jquery-2.1.4.min.js",
  "bxSlider": "https://cdnjs.cloudflare.com/ajax/libs/bxslider/4.2.5/jquery.bxslider.min.js",
  "angular": "https://ajax.googleapis.com/ajax/libs/angularjs/1.5.0-beta.2/angular.min.js",
  "ngAnimate": "https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.5.0-beta.2/angular-animate.min.js"
}
const loadedLibs = {}
let counter = 0

const loadAsync = function(lib) {
  var http = new XMLHttpRequest()
  http.open("GET", libs[lib], true)
  http.onload = () => {
    loadedLibs[lib] = http.responseText
    if (++counter == Object.keys(libs).length) startScripts()
  }
  http.send()
}

const startScripts = function() {
  for (var lib in libs) eval(loadedLibs[lib])
  console.log("allLoaded")
}

for (var lib in libs) loadAsync(lib)
```
