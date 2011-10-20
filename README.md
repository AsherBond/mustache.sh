mustache.sh
===========

[Mustache](http://mustache.github.com/) in [POSIX shell](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/contents.html).

There's (as of this writing) only one call to a non-builtin which is probably enough to claim this is fast enough for most uses.

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
* `mustache.sh` doesn't care about escaping output as HTML.

TODO
----

* List sections.  There's no way to differentiate between a list and a value with spaces in it.  This might become more clear when shell commands are supported.
* Lambdas.  What is this I don't even.
* Partials.  This is related to supporting shell commands as variables.
* Set delimeter.  This would be very hard to support in general because of the pervasive assumption that tag delimeters are two characters long.

TODONE
------

* Variable tags.
* Section tags.
* Inverted section tags.
* Comment tags.
* Nested sections.  Recursion, motherfucker.  Do you speak it?

License
-------

`mustache.sh` is [BSD-licensed](https://github.com/rcrowley/mustache.sh/blob/master/LICENSE).
