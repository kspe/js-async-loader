# JavaScript Async Loader

####_"load asynchronously, execute consequently"_

The simplest possible solution to help you eliminate render-blocking JavaScript.

No additional library. No additional HTTP request. Just a little inline script.

Ideal for Google PageSpeed test.

## Example

```js
var libs = {
	"jquery": {
		url: "https://code.jquery.com/jquery-2.1.4.min.js"
	},
	"bxSlider": {
		url: "https://cdnjs.cloudflare.com/ajax/libs/bxslider/4.2.5/jquery.bxslider.min.js"
	},
	"angular": {
		url: "https://ajax.googleapis.com/ajax/libs/angularjs/1.5.0-beta.2/angular.min.js"
	},
	"ngAnimate": {
		url: "https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.5.0-beta.2/angular-animate.min.js"
	}
	// add your custom JS here...
};

for (var lib in libs) {
	loadAsync(lib, libs);
}


/* LOADER FUNCTIONS */

function loadAsync(lib, libs) {
	var http = new XMLHttpRequest();
	http.open("GET", libs[lib].url, true);
	http.onload = function () {
		libs[lib].content = http.responseText;
		startScripts(libs);
	};
	http.send();
} // loadAsync

function startScripts(libs) {
	var allLoaded = true;
	for (var lib in libs) {
		allLoaded = allLoaded && Boolean(libs[lib].content);
	}
	if (allLoaded) {
		for (lib in libs) {
			eval(libs[lib].content);
		}
	}
} // startScripts
```
