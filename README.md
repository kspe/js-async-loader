# JavaScript Async Loader
####_"load asynchronously, execute consequently"_

The simplest possible solution to help you eliminate render-blocking JavaScript.

* No additional library.
* No additional HTTP request.
* Just a little inline script.
* Ideal for Google PageSpeed test.

See it in action: [mudroljub.github.io/js-async-loader](http://mudroljub.github.io/js-async-loader/)

## How to use

Open `index.html`. Put all your script in `libs` object, as key/value pair:

```js
const libs = {
  "jquery": "https://code.jquery.com/jquery-2.1.4.min.js",
  "bxSlider": "https://cdnjs.cloudflare.com/ajax/libs/bxslider/4.2.5/jquery.bxslider.min.js",
  "angular": "https://ajax.googleapis.com/ajax/libs/angularjs/1.5.0-beta.2/angular.min.js",
  "ngAnimate": "https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.5.0-beta.2/angular-animate.min.js"
	// here comes your script
}
```

Custom `js` file usually goes at the end.
