# jQuery Bookmarklet Plugin [![Build Status](https://travis-ci.org/michaelbrooks/jquery-bookmarklet.svg?branch=master)](https://travis-ci.org/michaelbrooks/jquery-bookmarklet)
### Make Bookmarklets from JavaScript files

According to Wikipedia, a [bookmarklet](http://en.wikipedia.org/wiki/Bookmarklet)
is a bookmark stored in a web browser that contains JavaScript commands to extend the browser's functionality.

Usually bookmarklets are created when the user drags and drops a
special anchor (`<a>`) element into their bookmarks toolbar.
The anchor's `href` attribute is set to `javascript:<the code to execute>`.

This makes bookmarklets kind of irritating to maintain, since you have
to prepare URL-encoded JavaScript and add it to your
`<a>` element every time you update the script.

This jQuery plugin loads your bookmarklet's JavaScript from an external file,
and then augments an anchor element on your page with the appropriate url.
It can also load JavaScript from a Gist via the GitHub API.

## Usage

1. Include jQuery:

	```html
	<script src="http://ajax.googleapis.com/ajax/libs/jquery/2.0.0/jquery.min.js"></script>
	```

2. Include plugin's code:

	```html
	<script src="dist/jquery.bookmarklet.min.js"></script>
	```

3. Add an anchor to your HTML:

    ```html
    <a id="element">My Bookmarklet</a>
    ```

4. Call the plugin:

	```javascript
	$("#element").bookmarklet({
		raw: "path/to/your/script.js"
	});
	```

    Or, point the plugin at a Gist:

    ```javascript
    $("#element").bookmarklet({
        gist_id: "MY_GIST_ID"
    });
    ```

You must provide either the `raw` or `gist_id` option
to tell the plugin where to find the JavaScript file.

You may *also* specify the `raw`, `gist_id`, and `gist_filename` options
as data attributes:

```html
<a data-bookmarklet-raw="some/url.js">My Bookmarklet</a>
<a data-bookmarklet-gist-id="MY_GIST_ID">My Bookmarklet</a>
```

### raw

A url pointing to a JavaScript file that will be loaded directly.

### gist_id

The id of a [Gist](gist.github.com).
You can get your Gist's id from its url: `https://gist.github.com/<username>/<gist_id>`.

### gist_filename

If your Gist contains multiple files, use this option to select one of them.

### on_ready

A callback which will be executed (with the selected element as its argument) when
the bookmarklet has been created.


## Development

To build, you need to install the npm packages and run grunt:

```bash
$ cd jquery-bookmarklet
$ npm install -g grunt-cli
$ npm install
$ grunt
```

Use this command to quickly view the test page:

```bash
$ python -m SimpleHTTPServer
# Now visit localhost:8000/demo
```
