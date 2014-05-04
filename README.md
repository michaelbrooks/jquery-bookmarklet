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
and then augments an anchor element on your page
with the appropriate url.
It can also load JavaScript from a Gist via
the GitHub API.

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

    Alternatively, point the plugin at a Gist:

    ```javascript
    $("#element").bookmarklet({
        gist_id: "MY_GIST_ID",
        gist_filename: "filename.js"
        /* gist_filename is optional if the Gist contains one file */
    });
    ```

    You can get your Gist's id from its url: `https://gist.github.com/<username>/<gist_id>`.
