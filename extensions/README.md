# Extensions

Primarily the `overthrow-sidescroller` and attendant plug ins.

## Sidescroller

The sidescroller provides a horizontally scrollable region with navigation anchors. To user the sidescroller you'll need to include:

```html
	<script src="../../src/overthrow-detect.js"></script>
	<script src="../../src/overthrow-polyfill.js"></script>
	<script src="../../src/overthrow-toss.js"></script>
	<script src="../../src/overthrow-init.js"></script>
	<script src="../../extensions/overthrow-sidescroller.js"></script>

	...


	<div class="sidescroll">
  	<div class="overthrow">
			<ul>
				<li><img src="img.jpg"></li>
				<li><img src="img.jpg"></li>
				<li><img src="img.jpg"></li>
			</ul>
		</div>
	</div>
```

And then invoke the `sidescroller` method on the overthrow object with a *set* of DOM elements.

```javascript
overthrow.sidescroller( document.querySelectorAll(".sidescroll") );
```

You can view a similarly constructed example at `$PROJECT_ROOT/examples/sidescroller/index.html`.

### Configuration

The default sidescroller can be configured on creation using the following options (defaults shown):

```javascript
overthrow.sidescroller( document.querySelectorAll(".sidescroll"), {
  rewind: false,
	snapScroll: false,
	snapTolerance: 30,
	fixedItemWidth: false
});
```

Setting `rewind` to `true` will cause the scroller to snap back to the first element when advancing forward on the last element and vice versa.

Setting `snapscroll` to `true` will align the left most element to the left border of the scroller when the region has scrolled to a position in between.

Setting `snapTolerance` to a larger value will increase how far the region must scroll before it is snapped into place again.

Setting `fixedItemWidth` to `true` allows the user to set the item width withing the scrollable region. When the window resizes elements will be hidden instead of resized.

## Disabled Nav

Including the disabled navigation extension with the sidescroller adds a `disabled` class to the navigation anchors when the region reaches it's ends.

```html
	<script src="../../src/overthrow-detect.js"></script>
	<script src="../../src/overthrow-polyfill.js"></script>
	<script src="../../src/overthrow-toss.js"></script>
	<script src="../../src/overthrow-init.js"></script>
	<script src="../../extensions/overthrow-sidescroller.js"></script>

	<!-- INCLUDE THE EXTENSION -->
	<script src="../../extensions/overthrow-sidescroller.disable-nav.js"></script>
```
Setting `rewind` to true will disable this behavior. You can view a demo at `$PROJECT_ROOT/examples/sidescroller/disabled-nav.html`.

## Append Method

Including the `append` extension provides a method for gracefully handling the addition of list items to the child list

```html
	<script src="../../src/overthrow-detect.js"></script>
	<script src="../../src/overthrow-polyfill.js"></script>
	<script src="../../src/overthrow-toss.js"></script>
	<script src="../../src/overthrow-init.js"></script>
	<script src="../../extensions/overthrow-sidescroller.js"></script>

	<!-- INCLUDE THE EXTENSION -->
	<script src="../../extensions/overthrow-sidescroller.append.js"></script>
```

The calling convention for the `append` method is as follows:

```javascript
overthrow.sidescroller( scrollerElement, "append", newLi );
```

You can view a demo at `$PROJECT_ROOT/examples/sidescroller/append.html`.

## Removing Items

No extension is required for removing elements from the sidescroller. Simply remove the elements from the DOM and call refresh:

```javascript
overthrow.sidescroller( scrollerElement, "refresh" );
```

This is demonstrated in the append demo.