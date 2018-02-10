# Just Another Parallax
Smooth parallax scrolling effect for background images, videos and inline elements. Code in pure JavaScript with ***NO dependencies*** + jQuery supported. ***Youtube***, ***Vimeo*** and ***Local Videos*** parallax supported.

## [Demo](https://free.nkdev.info/jarallax/)

## Tested Browsers
* Latest browsers on Mac and Windows (Chrome, Firefox, Safari, IE11, Edge)
* Latest Chrome on Android
* Latest Safari on iOs

## Want WordPress Plugin?

[![Advanced WordPress Backgrounds](https://a.nkdev.info/jarallax/awb-preview.jpg)](https://wordpress.org/plugins/advanced-backgrounds/)

We made WordPress plugin to easily make backgrounds for content in your blog with all Jarallax features.

Demo: https://wp.nkdev.info/free-advanced-wordpress-backgrounds/

Download: https://nkdev.info/downloads/advanced-wordpress-backgrounds/

## Install
Include Jarallax plugin. Also include jQuery before jarallax if you want to use it.

### Download
Download scripts directly from this repository and link it in your HTML file
```html
<!-- Jarallax -->
<script src="jarallax/jarallax.js"></script>

<!-- Include it if you want to use Video parallax -->
<script src="jarallax/jarallax-video.js"></script>

<!-- Include it if you want to parallax any element -->
<script src="jarallax/jarallax-element.js"></script>
```

### CDN
Link directly from [unpkg](https://unpkg.com/)
```html
<!-- Jarallax -->
<script src="https://unpkg.com/jarallax@1.9/dist/jarallax.min.js"></script>

<!-- Include it if you want to use Video parallax -->
<script src="https://unpkg.com/jarallax@1.9/dist/jarallax-video.min.js"></script>

<!-- Include it if you want to parallax any element -->
<script src="https://unpkg.com/jarallax@1.9/dist/jarallax-element.min.js"></script>
```

### Package managers
npm: `npm install jarallax --save`

Bower: `bower install jarallax --save`

## Supported plugins
You can add these plugins before jarallax initialize.
- [object-fit-images](https://github.com/bfred-it/object-fit-images) polyfill for `object-fit` styles;
- [lazysizes](https://github.com/aFarkas/lazysizes) lazy-load images with srcset support;

## Set up your HTML
```html
<!-- Background Image Parallax -->
<div class="jarallax">
    <img class="jarallax-img" src="<background_image_url_here>" alt="">
    Your content here...
</div>

<!-- Alternate: Background Image Parallax -->
<div class="jarallax" style="background-image: url('<background_image_url_here>');">
    Your content here...
</div>
```

### Additional styles
These styles need to correct background image position before Jarallax initialized:
```css
.jarallax {
    position: relative;
    z-index: 0;
}
.jarallax > .jarallax-img {
    position: absolute;
    object-fit: cover;
    /* support for plugin https://github.com/bfred-it/object-fit-images */
    font-family: 'object-fit: cover;';
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1;
}
```
You can include it from `dist/jarallax.css`.

## Call the plugin

### A. Data attribute way
```html
<div data-jarallax data-speed="0.2" class="jarallax">
    <img class="jarallax-img" src="<background_image_url_here>" alt="">
    Your content here...
</div>
```
Note: You can use all available options as data attributes. For example: `data-speed`, `data-img-src`, `data-img-size`, etc...

### B. JavaScript way
```javascript
jarallax(document.querySelectorAll('.jarallax'), {
    speed: 0.2
});
```

### C. jQuery way
```javascript
$('.jarallax').jarallax({
    speed: 0.2
});
```

## Background Video Usage Examples
```html
<!-- Background YouTube Parallax -->
<div class="jarallax" data-jarallax-video="https://www.youtube.com/watch?v=ab0TSkLe-E0">
    Your content here...
</div>

<!-- Background Vimeo Parallax -->
<div class="jarallax" data-jarallax-video="https://vimeo.com/110138539">
    Your content here...
</div>

<!-- Background Local Video Parallax -->
<div class="jarallax" data-jarallax-video="mp4:./video/local-video.mp4,webm:./video/local-video.webm,ogv:./video/local-video.ogv">
    Your content here...
</div>
```
Note: for local videos required only 1 video type, not necessary use all mp4, webm and ogv. This need only for maximum compatibility with all browsers.

## Any Element Parallax Usage Examples
```html
<!-- Element will be parallaxed on -140 pixels from the screen center by Y axis -->
<div data-jarallax-element="-140">
    Your content here...
</div>

<!-- Element will be parallaxed on 250 pixels from the screen center by Y axis and on -100 pixels from the screen senter by X axis -->
<div data-jarallax-element="250 -100">
    Your content here...
</div>
```
Note: this is more like experimental feature, so the behavior could be changed in the future releases.

# Options
Options can be passed in data attributes or in object when you initialize jarallax from script.

Name | Type | Default | Description
:--- | :--- | :------ | :----------
type | string | `scroll` | scroll, scale, opacity, scroll-opacity, scale-opacity.
speed | float | `0.5` | Parallax effect speed. Provide numbers from -1.0 to 2.0.
imgSrc | path | `null` | Image url. By default used image from background.
imgElement | dom / selector | `.jarallax-img` | Image tag that will be used as background.
imgSize | string | `cover` | Image size. If you use `<img>` tag for background, you should add `object-fit` values, else use `background-size` values.
imgPosition | string | `50% 50%` | Image position. If you use `<img>` tag for background, you should add `object-position` values, else use `background-position` values.
imgRepeat | string | `no-repeat` | Image repeat. Supported only `background-position` values.
keepImg | boolean | `false` | Keep `<img>` tag in it's default place after Jarallax inited.
elementInViewport | dom | `null` | Use custom DOM / jQuery element to check if parallax block in viewport. More info here - [Issue 13](https://github.com/nk-o/jarallax/issues/13).
zIndex | number | `-100` | z-index of parallax container.
noAndroid | boolean | `false` | Disable parallax on Android devices.
noIos | boolean | `false` | Disable parallax on iOs devices.

### Options For Video (+ supported all default options)
Required `jarallax/jarallax-video.js` file.

Name | Type | Default | Description
:--- | :--- | :------ | :----------
videoSrc | string | `null` | You can use Youtube, Vimeo or local videos. Also you can use data attribute `data-jarallax-video`.
videoStartTime | float | `0` | Start time in seconds when video will be started (this value will be applied also after loop).
videoEndTime | float | `0` | End time in seconds when video will be ended.
videoVolume | float | `0` | Video volume from 0 to 100.
videoPlayOnlyVisible | boolean | `true` | Play video only when it is visible on the screen.

### Options For Element Parallax
Required `jarallax/jarallax-element.js` file.

Name | Type | Default | Description
:--- | :--- | :------ | :----------
type | string | `element` | Will only work with `element` value.
speed | mixed | `0 0` | Parallax distance in pixels. Supported Y and X axis. Example: `100 200`. Also you can use data attribute `data-jarallax-element`.

# Events
Evenets used the same way as Options.

Name | Description
:--- | :----------
onScroll | Called when parallax working. Use first argument with calculations. More info [see below](#onscroll-event).
onInit | Called after init end.
onDestroy | Called after destroy.
onCoverImage | Called after cover image.

## onScroll event
```javascript
jarallax(document.querySelectorAll('.jarallax'), {
    onScroll: function(calculations) {
        console.log(calculations);
    }
});
```

Console Result:
```javascript
{
    // parallax section client rect (top, left, width, height)
    rect            : object,

    // see image below for more info
    beforeTop       : float,
    beforeTopEnd    : float,
    afterTop        : float,
    beforeBottom    : float,
    beforeBottomEnd : float,
    afterBottom     : float,

    // percent of visible part of section (from 0 to 1)
    visiblePercent  : float,

    // percent of block position relative to center of viewport from -1 to 1
    fromViewportCenter: float
}
```

Calculations example:
[![On Scroll Calculations](https://a.nkdev.info/jarallax/jarallax-calculations.jpg)](https://a.nkdev.info/jarallax/jarallax-calculations.jpg)


# Methods
Name | Result | Description
:--- | :----- | :----------
destroy | - | Destroy Jarallax and set block as it was before plugin init.
isVisible | boolean | Check if parallax block is in viewport.
onResize | - | Fit image and clip parallax container. Called on window resize and load.
onScroll | - | Calculate parallax image position. Called on window scroll.

## Call methods example
### A. JavaScript way
```javascript
jarallax(document.querySelectorAll('.jarallax'), 'destroy');
```

### B. jQuery way
```javascript
$('.jarallax').jarallax('destroy');
```


# No conflict
If you already have global ***jarallax*** variable or ***jQuery.fn.jarallax***, you can rename plugin.
### A. JavaScript way
```javascript
var newJarallax = jarallax.noConflict();
```

### B. jQuery way
```javascript
jQuery.fn.newJarallax = jQuery.fn.jarallax.noConflict();
```


# Real Usage Examples
* [Khaki](https://demo.nkdev.info/#khaki)
* [Godlike](https://demo.nkdev.info/#godlike)
* [Youplay](https://demo.nkdev.info/#youplay)

# Credits
Images https://unsplash.com/
Local Video https://videos.pexels.com/

# License
Copyright (c) 2017 nK Licensed under the WTFPL license.
