Nestable
========

## PLEASE NOTE

**I cannot provide any support or guidance beyond this README. If this code helps you that's great but I have no plans to develop Nestable beyond this demo (it's not a final product and has limited functionality). I cannot reply to any requests for help.**

* * *

### Drag & drop hierarchical list with mouse and touch compatibility (jQuery / Zepto plugin)

Nestable is an experimental example and not under active development. If it suits your requirements feel free to expand upon it!

## Usage

Write your nested HTML lists like so (And now you can ommit the parent `class="dd"` below):

```HTML
<div class="dd">
    <ol class="dd-list">
        <li class="dd-item" data-id="1" data-name="Alifah">
            <div class="dd-handle">Item1</div>
        </li>
        <li class="dd-item" data-id="2" data-name="Hamzah">
            <div class="dd-handle">Item2</div>
        </li>
        <li class="dd-item" data-id="3" data-name="Royyan">
            <div class="dd-handle">Item3</div>
            <ol class="dd-list">
                <li class="dd-item" data-weight="100">
                    <div class="dd-handle">Item 4</div>
                </li>
                <li class="dd-item" data-custom-attributes="yes">
                    <div class="dd-handle">Item 5</div>
                </li>
            </ol>
        </li>
    </ol>
</div>
```
Then activate with jQuery like so:
```js
    $('.dd').nestable({ /* config options */ });
```

### Events

Event `change` is fired when the item is released.
```js
    $('.dd').on('change', function() {
        /* on change event */
    });
```

Event `dragstart` is fired when the item begin to move.
```js
    $('.dd').on('dragstart', function() {
        /* on dragstart event */
    });
```

Event `dragmove` is fired when the item is moving.
```js
    $('.dd').on('dragmove', function() {
        /* on dragmove event */
    });
```

Event `dragstop` is fired when the item is released.
```js
    $('.dd').on('dragstop', function() {
        /* on dragstop event */
    });
```
### Methods

You can get a serialised object with all `data-*` attributes for each item.
```js
    $('.dd').nestable('serialize');
```

The serialised JSON for the example above would be:
```json
[
    {
        "id": 1,
        "name": "Alifah"
    }, {
        "id": 2,
        "name": "Hamzah"
    }, {
        "id": 3,
        "name": "Royyan",
        "children": [
            {
                "weight": 100
            }, {
                "customAttributes": "yes"
            }
        ]
    }
]
```

### Configuration

You can change the follow options:

* `maxDepth` number of levels an item can be nested (default `5`)
* `group` group ID to allow dragging between lists (default `0`)

These advanced config options are also available:

* `listNodeName` The HTML element to create for lists (default `'ol'`)
* `itemNodeName` The HTML element to create for list items (default `'li'`)
* `listClass` The class of all list elements (default `'dd-list'`)
* `itemClass` The class of all list item elements (default `'dd-item'`)
* `dragClass` The class applied to the list element that is being dragged (default `'dd-dragel'`)
* `handleClass` The class of the content element inside each list item (default `'dd-handle'`)
* `collapsedClass` The class applied to lists that have been collapsed (default `'dd-collapsed'`)
* `placeClass` The class of the placeholder element (default `'dd-placeholder'`)
* `emptyClass` The class used for empty list placeholder elements (default `'dd-empty'`)
* `expandBtnHTML` The HTML text used to generate a list item expand button (default `'<button data-action="expand">Expand></button>'`)
* `collapseBtnHTML` The HTML text used to generate a list item collapse button (default `'<button data-action="collapse">Collapse</button>'`)

## Change Log

### 17th January 2025
* New events `dragstart`, `dragmove` and `dragstop`.
* Improve options method.

### 15th October 2024

* Improve dynamic root without mandatory class `dd`, so you can wrap `<ol class="dd-list">` with `<div>` only.
* Improve syntax.

### 15th October 2012

* Merge for Zepto.js support
* Merge fix for remove/detach items

### 27th June 2012

* Added `maxDepth` option (default to 5)
* Added empty placeholder
* Updated CSS class structure with options for `listClass` and `itemClass`.
* Fixed to allow drag and drop between multiple Nestable instances (off by default).
* Added `group` option to enabled the above.

* * *

Author: David Bushell [http://dbushell.com](http://dbushell.com/) [@dbushell](http://twitter.com/dbushell/)

Copyright © 2012 David Bushell | BSD & MIT license
