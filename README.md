Galpop Image Gallery
=================

Description: Galpop is an image gallery pop-up. It can be controlled with the left and right arrow keys and automatically resizes with your browser.

Author: Richard Hung

More documentation and examples: http://galpop.magicmediamuse.com

## Install

Install it using [Bower](http://bower.io):

```sh
$ bower install galpop
```

Install it using [npm](https://www.npmjs.org/):

```sh
$ npm install galpop
```

Or [download as ZIP](https://github.com/Richard1320/Galpop/archive/master.zip).

Key Features
--------------------

* Resizes with your browser
* Can use arrow keys for controls
* Callbacks after every image is loaded
* Backgrounds and borders can be easily changed with CSS

How to Use
--------------------

Galpop has a CSS and JS file in addition to the jQuery library.

```
<link type="text/css" href="css/jquery.galpop.css" rel="stylesheet" media="screen" />

<script src="http://code.jquery.com/jquery-latest.js"></script>

<script type="text/javascript" src="js/jquery.galpop.min.js"></script>
```

Create anchors that link to the pop-up image. You should add a "data-galpop-group" attribute to the anchor which will group all your images so you can use next and previous buttons.

```
<a href="images/image-1-large.jpg" class="galpop" data-galpop-group="gallery" title="first image">
	<img src="images/image-1-tb.jpg" alt="first image thumbnail" />
</a>
<a href="images/image-2-large.jpg" class="galpop" data-galpop-group="gallery" title="second image">
	<img src="images/image-2-tb.jpg" alt="second image thumbnail" />
</a>
<a href="images/image-3-large.jpg" class="galpop" data-galpop-group="gallery" title="third image">
	<img src="images/image-3-tb.jpg" alt="third image thumbnail" />
</a>
```

Initiate the plugin after the HTML markup.

```
$('.galpop').galpop();
```
Single Image
```
<a class="galpop-single" href="/images/gallery/large/apocalypse.jpg">
	<img src="/images/gallery/thumbs/apocalypse.jpg" alt="An apocalyptic Earth." />
</a>
$('.galpop-single').galpop();
```

Multiple Images
```
<a class="galpop-multiple" data-galpop-group="multiple" href="/images/gallery/large/reflection.jpg">
	<img src="/images/gallery/thumbs/reflection.jpg" alt="A magical poster with a reflection." />
</a>
$('.galpop-multiple').galpop();
```

Image Info
```
<a class="galpop-info" data-galpop-group="info" data-galpop-link="http://www.magicmediamuse.com/graphic/alice" data-galpop-link-title="Click Here For More Info" data-galpop-link-target="_blank" title="The scene from Alice in Wonderland where she meets the caterpillar." href="/images/gallery/large/alice.jpg">
	<img src="/images/gallery/thumbs/alice.jpg" alt="The scene from Alice in Wonderland where she meets the caterpillar." />
</a>
<a class="galpop-info" data-galpop-group="info" data-galpop-link="http://www.magicmediamuse.com/graphic/reflection" data-galpop-link-title="Click Here For More Info" data-galpop-link-target="_blank" title="A magical poster with a reflection." href="/images/gallery/large/reflection.jpg">
	<img src="/images/gallery/thumbs/reflection.jpg" alt="A magical poster with a reflection." />
</a>
$('.galpop-info').galpop();
```

Callbacks
```
<a class="galpop-callback" data-galpop-group="callback" href="/images/gallery/large/alice.jpg">
	<img src="/images/gallery/thumbs/alice.jpg" alt="The scene from Alice in Wonderland where she meets the caterpillar." />
</a>
<a class="galpop-callback" data-galpop-group="callback" href="/images/gallery/large/reflection.jpg">
	<img src="/images/gallery/thumbs/reflection.jpg" alt="A magical poster with a reflection." />
</a>
var callback = function() {
	var wrapper = $('#galpop-wrapper');
	var info    = $('#galpop-info');
	var count   = wrapper.data('count');
	var index   = wrapper.data('index');
	var current = index + 1;
	var string  = 'Image '+ current +' of '+ count;

	info.append('<p>'+ string +'</p>').fadeIn();

};
$('.galpop-callback').galpop({
	callback: callback
});
```

Manual Open
You can also manually open the popup whenever you wish. You will have to use the "openBox" method and pass it the settings and image URL to open.

```
<select class="manual-open">
<option value="">Choose Image</option>
<option value="/images/gallery/large/apocalypse.jpg">An apocalyptic Earth.</option>
<option value="/images/gallery/large/vintage.jpg">An old, vintage poster.</option>
<option value="/images/gallery/large/magicLake.jpg">A scene of a magical forest.</option>
<option value="/images/gallery/large/underwater.jpg">An underwater scene with lots of tension.</option>
<option value="/images/gallery/large/goodBoy.jpg">A dog and his pet.</option>
<option value="/images/gallery/large/darkroad.jpg">A scene where nothing is what it seems.</option>
<option value="/images/gallery/large/roadkill.jpg">Either an anti-hunting poster or a pro-hunting one, depending on how you look at it.</option>
<option value="/images/gallery/large/wolfMarine.jpg">A portrait of a wolf marine.</option>
<option value="/images/gallery/large/alice.jpg">The scene from Alice in Wonderland where she meets the caterpillar.</option>
<option value="/images/gallery/large/reflection.jpg">A magical poster with a reflection.</option>
</select>

$('.manual-click').click(function(e) {
	var settings = {};
	$.fn.galpop('openBox',settings,'/images/gallery/large/magicLake.jpg');
});
```

Manual Open Group
You can also manually open the popup as a group. Instead of passing it one url, you can use an array.
```
<select class="manual-open">
<option value="">Choose Image</option>
<option value="0">An apocalyptic Earth.</option>
<option value="1">An old, vintage poster.</option>
<option value="2">A scene of a magical forest.</option>
<option value="3">An underwater scene with lots of tension.</option>
<option value="4">A dog and his pet.</option>
<option value="5">A scene where nothing is what it seems.</option>
<option value="6">Either an anti-hunting poster or a pro-hunting one, depending on how you look at it.</option>
<option value="7">A portrait of a wolf marine.</option>
<option value="8">The scene from Alice in Wonderland where she meets the caterpillar.</option>
<option value="9">A magical poster with a reflection.</option>
</select>

$('.manual-open-group').change(function(e) {
	var v = $(this).val();
	var images = [
		'images/gallery/large/apocalypse.jpg',
		'images/gallery/large/vintage.jpg',
		'images/gallery/large/magicLake.jpg',
		'images/gallery/large/underwater.jpg',
		'images/gallery/large/goodBoy.jpg',
		'images/gallery/large/darkroad.jpg',
		'images/gallery/large/roadkill.jpg',
		'images/gallery/large/wolfMarine.jpg',
		'images/gallery/large/alice.jpg',
		'images/gallery/large/reflection.jpg',
	];
	var settings = {};
	$.fn.galpop('openBox',settings,images,v);
});
```
