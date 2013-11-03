Reader.js
===

**Reader.js** is a tiny interface to unify three primary methods of reading data with JavaScript: AJAX requests, local disk access (NodeJS) and the HTML5 File API.

Example
===

```javascript
var rd = new Reader(Reader.OPEN_FILE);
rd.open(file, function() {
	// file has now been opened and is ready for reading
	rd.read(1024, function(err, data) {
		// data is now an ArrayBuffer
	});
});
```

Here, `data` will be an `ArrayBuffer` containing the first 1024 bytes from the specified file (which is a `File` instance).

The following types exist:

* `Reader.OPEN_FILE` Treat the specified object as a `File` instance (HTML5 File API)
* `Reader.OPEN_URI` Read the given URI by HTTP request
* `Reader.OPEN_LOCAL` Read the given path locally, works only in NodeJS

The default is `Reader.OPEN_URI`.

Methods
===

* `open(file, callback)` Open the specified file and call the callback on completion/ready
* `close()` Close the handle and clean up
* `read(length, position, callback)` Read `length` bytes from offset `position` and call `callback` with the resulting ArrayBuffer

Notes
===

* You should call `Reader.close()` when finished with the instance to avoid leftover handles (primarily in Node)

License
===

MIT
