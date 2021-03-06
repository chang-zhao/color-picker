Color Picker
============

> A simple color picker plugin written in pure JavaScript, for modern browsers.

[![View Demo](https://cloud.githubusercontent.com/assets/1669261/16919759/246196ec-4d35-11e6-8d12-153aa969384e.png)](https://rawgit.com/tovic/color-picker/master/color-picker.html "View Demo")

~~~ .html
<!DOCTYPE html>
<html dir="ltr">
  <head>
    <meta charset="utf-8">
    <title>Test</title>
    <link href="color-picker.min.css" rel="stylesheet">
  </head>
  <body>
    <input type="text">
    <script src="color-picker.min.js"></script>
    <script>
    var picker = new CP(document.querySelector('input[type="text"]'));
    picker.on("change", function(color) {
        this.target.value = '#' + color;
    });
    </script>
  </body>
</html>
~~~

Has support for touch events. Touchy… touchy…

Instance
--------

~~~ .javascript
var el = document.querySelector('input[type="color"]');

// show color picker on click (default)
var picker = new CP(el);

// show color picker on hover
var picker = new CP(el, 'mouseover');

// disable color picker by default
// to enable it, try `picker.enter()`
var picker = new CP(el, false);
~~~

Instances
---------

All color picker instances are stored in `CP.__instance__`.

Show all instances:

~~~ .javascript
console.log(CP.__instance__);
~~~

Do something with instances:

~~~ .javascript
CP.each(function($) {
    // `$` refers to the color picker instance
    $.enter(); // this will show all of the color picker panel
});
~~~

Hooks
-----

The available hooks:

 - `create`
 - `destroy`
 - `enter`
 - `exit`
 - `fit`
 - `change`
 - `change:h`
 - `change:sv`
 - `start`
 - `start:h`
 - `start:sv`
 - `drag`
 - `drag:h`
 - `drag:sv`
 - `stop`
 - `stop:h`
 - `stop:sv`

### Add a Hook

Add a `change` hook.

~~~ .javascript
picker.on("change", function(color) {
    console.log(color);
});
~~~

### Add a Hook with ID

Add a `change` hook with ID of `test-id`.

~~~ .javascript
picker.on("change", function(color) {
    console.log(color);
}, 'test-id');
~~~

### Remove a Hook

Remove all `change` hooks.

~~~ .javascript
picker.off("change");
~~~

### Remove a Hook by ID

Remove a `change` hook with ID of `test-id`.

~~~ .javascript
picker.off("change", 'test-id');
~~~

### Trigger a Hook with Custom Value

Trigger all `change` hooks with pre–defined color value as `ffa500`.

~~~ .javascript
picker.trigger("change", ['ffa500']);
~~~

Trigger a `change` hook with ID of `test-id` and with pre–defined color value as `ffa500`.

~~~ .javascript
picker.trigger("change", ['ffa500'], 'test-id');
~~~

Data
----

### Get the Target Element

~~~ .javascript
var target = picker.target;
~~~

### Get the Picker Element

~~~ .javascript
var picker = picker.picker;
~~~

### Get Hidden Color Data on the Target Element

~~~ .javascript
console.log(picker.set());
~~~

### Set Hidden Color Data on the Target Element

~~~ .javascript
picker.set([0, 1, 1]); // HSV color value, range from `0` to `1` for each
~~~

~~~ .javascript
picker.set('rgb(255, 0, 0)'); // as color string
~~~

Color Converter
---------------

### HSV to RGB

~~~ .javascript
console.log(CP.HSV2RGB([360, 100, 100]));
~~~

### HSV to HEX

~~~ .javascript
console.log(CP.HSV2HEX([360, 100, 100]));
~~~

### RGB to HSV

~~~ .javascript
console.log(CP.RGB2HSV([255, 255, 255]));
~~~

### RGB to HEX

~~~ .javascript
console.log(CP.RGB2HEX([255, 255, 255]));
~~~

### HEX to HSV

~~~ .javascript
console.log(CP.HEX2HSV('ffffff'));
~~~

### HEX to RGB

~~~ .javascript
console.log(CP.HEX2RGB('ffffff'));
~~~

### Parse to Raw HSV Color Data

All valid color string input will be converted into array of hue, saturation and value, with a range from `0` to `1`.

~~~ .javascript
console.log(CP.parse('#ffffff'));
console.log(CP.parse('rgb(255, 255, 255)'));
console.log(CP.parse('hsv(140, 20%, 60%)'));
console.log(CP.parse([0, 1, 1])); // no changes
~~~

State
-----

### Show

~~~ .javascript
picker.enter(); // show the color picker
~~~

### Hide

~~~ .javascript
picker.exit(); // hide the color picker
~~~

### Visible

~~~ .javascript
if (picker.visible) { … } // color picker is visible
~~~

Want to Add More Features?
--------------------------

My purpose in making this plugin is to provide a JavaScript color picker solution as simple as possible with the most minimal features without requiring any dependency on JavaScript library such as jQuery or Prototype.

If you want to add new features, you can use the available hooks to make your own improvements without having to touch the plugin core. Here are some examples:

 - [No Idea?](https://rawgit.com/tovic/color-picker/master/color-picker.noob.html)
 - [Multiple Instances](https://rawgit.com/tovic/color-picker/master/color-picker.picker.html)
 - [Pre–Defined Value](https://rawgit.com/tovic/color-picker/master/color-picker.value-set.html)
 - [Pre–Defined Color](https://rawgit.com/tovic/color-picker/master/color-picker.picker-set.html)
 - [Update Color Picker State on Value Changes](https://rawgit.com/tovic/color-picker/master/color-picker.value-update.html)
 - [Convert HEX Color Value](https://rawgit.com/tovic/color-picker/master/color-picker.value-convert.html)
 - [Add Support for HSL Color Value](https://rawgit.com/tovic/color-picker/master/color-picker.color-hsl.html)
 - [Transparency](https://rawgit.com/tovic/color-picker/master/color-picker.color-rgba.html)
 - [Show and Hide with Buttons](https://rawgit.com/tovic/color-picker/master/color-picker.state.html)
 - [Show and Hide with Double Click](https://rawgit.com/tovic/color-picker/master/color-picker.trigger.html)
 - [Add Close Button](https://rawgit.com/tovic/color-picker/master/color-picker.close.html)
 - [Static Color Picker](https://rawgit.com/tovic/color-picker/master/color-picker.static.html)
 - [Replace Text Input with Hidden Input](https://rawgit.com/tovic/color-picker/master/color-picker.replace.html)
 - [HTML5 Color Input](https://rawgit.com/tovic/color-picker/master/color-picker.input-color.html)
 - [Create and Destroy Method](https://rawgit.com/tovic/color-picker/master/color-picker.create-destroy.html)
 - [Auto–Positioned to the Reachable Area in the Document](https://rawgit.com/tovic/color-picker/master/color-picker.fit.html)
 - [Color Preview in Color Picker](https://rawgit.com/tovic/color-picker/master/color-picker.picker-preview.html)