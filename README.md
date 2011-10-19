mustache.sh
===========

[Mustache](http://mustache.github.com/) in [POSIX shell](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/contents.html).

There's (as of this writing) only one call to a non-builtin (`sed`(1)) which is probably enough to claim this is fast enough for most uses.

Installation
------------

	make && sudo make install

Usage
-----

From the command-line:

	FOO="foo" BAR="bar" mustache.sh <"test.mustache"

As a library:

	. "lib/mustache.sh"
	FOO="foo" BAR="bar"
	mustache <"test.mustache"

Spec
----

* [`mustache`(1)](http://mustache.github.com/mustache.1.html)
* [`mustache`(5)](http://mustache.github.com/mustache.5.html)

Deviations from spec
--------------------

* `mustache.sh` accepts input data via the environment, not via YAML frontmatter.  This makes sense for shell programmers but may render this Mustache implementation unsuitable for other use.
* `mustache.sh` does not descend into a new scope within <code>{{#<em>tag</em>}}</code> or <code>{{^<em>tag</em>}}</code> sections.  This again makes sense when being driven by environment variables.
* `mustache.sh` doesn't support the `--compile` or `--tokens` command-line options and does not accept input file(s) as arguments.

TODO
----

* List sections.
* Lambdas.
* Nested sections.
* Partials.
* Set delimeter.

TODONE
------

* Variable tags.
* Section tags.
* Inverted section tags.
* Comment tags.

License
-------

`mustache.sh` is [BSD-licensed](https://github.com/rcrowley/mustache.sh/blob/master/LICENSE).
