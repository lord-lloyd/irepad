# This is not irepad's README

This is Firepad's README, because I haven't written anything yet.

## Firepad

[![Build Status](https://travis-ci.org/firebase/firepad.svg?branch=master)](https://travis-ci.org/firebase/firepad)
[![Version](https://badge.fury.io/gh/firebase%2Ffirepad.svg)](http://badge.fury.io/gh/firebase%2Ffirepad)

[Firepad](http://www.firepad.io/) is an open-source, collaborative code and text editor. It was
designed to be embedded inside larger applications. Since it uses
[Firebase](https://www.firebase.com/?utm_source=firepad) as a backend, it requires no server-side
code and can be added to any web app simply by including a couple JavaScript files.

Visit [firepad.io](http://www.firepad.io/) for a demo as well as instructions on how to embed it
into your application!

Join our [Firepad Google Group](https://groups.google.com/forum/#!forum/firepad-io) to ask
questions, request features, or share your Firepad apps with the community.


## Contributing

If you'd like to contribute to Firepad, you'll need to run the following commands to get your
environment set up:

```bash
$ git clone https://github.com/firebase/firepad.git
$ cd firepad                # go to the geofire directory
$ npm install -g grunt-cli  # globally install grunt task runner
$ npm install -g bower      # globally install Bower package manager
$ npm install               # install local npm build / test dependencies
$ bower install             # install local JavaScript dependencies
$ grunt watch               # watch for source file changes
```

`grunt watch` will watch for changes in the `/lib/` directory and lint, concatenate, and minify the
source files when a change occurs. The output files are written to the `/dist/` directory.

You can run the test suite by navigating to `file:///path/to/firepad/tests/index.html` or via the
command line using `grunt test`.


## Source Code Overview

To get started, here are some highlights of the directory structure and notable source files:

* `dist/` - output directory for all files generated by grunt (`firepad.js`, `firepad.min.js`, `firepad.css`, `firepad.eot`).
* `examples/` - examples of embedding Firepad.
* `font/` - icon font used for rich text toolbar.
* `lib/`
    * `firepad.js` - Entry point for Firepad.
    * `text-operation.js`, `client.js` - Heart of the Operation Transformation implementation.  Based on
      [ot.js](https://github.com/Operational-Transformation/ot.js/) but extended to allow arbitrary
      attributes on text (for representing rich-text).
    * `annotation-list.js` - A data model for representing annotations on text (i.e. spans of text with a particular
      set of attributes).
    * `rich-text-codemirror.js` - Uses `AnnotationList` to track annotations on the text and maintain the appropriate
      set of markers on a CodeMirror instance.
    * `firebase-adapter.js` - Handles integration with Firebase (appending operations, triggering retries,
      presence, etc.).
* `test/` - Jasmine tests for Firepad (many of these were borrowed from ot.js).
