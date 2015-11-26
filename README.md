# JavaScript Async Loader

###_"load asynchronously, execute consequently"_

No-library (just a little inline script) solution to help you eliminate render-blocking JavaScript. Ideal for Google PageSpeed test.

,,,
// put all your JS files here, in correct order
var libs = {
    "jquery": {
        url: "https://code.jquery.com/jquery-2.1.4.min.js",
        content: null
    },
    "bxSlider": {
        url: "https://cdnjs.cloudflare.com/ajax/libs/bxslider/4.2.5/jquery.bxslider.min.js",
        content: null
    },
    "angular": {
        url: "https://ajax.googleapis.com/ajax/libs/angularjs/1.5.0-beta.2/angular.min.js",
        content: null
    },
    "ngAnimate": {
        url: "https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.5.0-beta.2/angular-animate.min.js",
        content: null
    }
};
for(var lib in libs) {
    loadAsync(lib);
}
,,,
