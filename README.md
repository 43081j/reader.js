Reader.js
===

**Reader.js** is a tiny interface to unify three primary methods of reading data with JavaScript: AJAX requests, local disk access (NodeJS) and the HTML5 File API.

Example
===

```javascript
var rd = new Reader(Reader.OPEN_FILE);
rd.open(file, function() {
	// file has now been opened and is ready for reading
	var data = rd.read(1024);
});
```

Here, `data` will be an `ArrayBuffer` containing the first 1024 bytes from the specified file (which is a `File` instance).

The following types exist:

* `Reader.OPEN\_FILE` Treat the specified object as a `File` instance (HTML5 File API)
* `Reader.OPEN\_URI` Read the given URI by HTTP request
* `Reader.OPEN\_LOCAL` Read the given path locally, works only in NodeJS

The default is `Reader.OPEN\_URI`.

Notes
===

* You should call `Reader.close()` when finished with the instance to avoid leftover handles (primarily in Node)

License
===

MIT
