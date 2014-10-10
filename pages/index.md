---
title: Functions for safer shell scripting
header-class: index
page-footer: |
  <script>
    addEventListener('load', function () {
      document.getElementById('hello').href = cannot.rot13('znvygb:uryyb@yrnfgsvkrq.pbz');
    });
  </script>
---

Functions for safer shell scripting
===================================

Used in [Halcyon](http://halcyon.sh/) and [Haskell on Heroku](http://haskellonheroku.com/).


Usage
-----

Sourcing the top-level script brings all functions into scope.

```
$ source bashmenot/bashmenot.sh
```

Individual modules can also be sourced separately, as long as their dependencies are sourced as well.

Please refer to the [programmer reference](reference/) for more information, including examples and module dependencies.


### Installation

Cloning the repository is sufficient.

```
$ git clone https://github.com/mietek/bashmenot.git
```

Also available as a [Bower](http://bower.io/) package.

```
$ bower install bashmenot
```


### Dependencies

Requires [GNU _bash_](http://gnu.org/software/bash/) 4 or newer.

Some functions require [GNU _date_](https://www.gnu.org/software/coreutils/manual/html_node/date-invocation.html) and [GNU _sort_](https://www.gnu.org/software/coreutils/manual/html_node/sort-invocation.html), available as part of [GNU _coreutils_](https://www.gnu.org/software/coreutils/).

HTTP transfer functions require [_curl_](http://curl.haxx.se/).  Amazon S3 transfer functions also require [OpenSSL](https://www.openssl.org/).


Support
-------

Please report any problems with _bashmenot_ on the [issue tracker](https://github.com/mietek/bashmenot/issues/).  There is a [separate issue tracker](https://github.com/mietek/bashmenot-website/issues/) for problems with the documentation.

Commercial support for _bashmenot_ is offered by [Least Fixed](http://leastfixed.com/), a functional software consultancy.

Need help?  Say <a href="" id="hello">hello</a>.


License
-------

Made by [Miëtek Bak](http://mietek.io/).  Published under the [MIT X11 license](license/).
