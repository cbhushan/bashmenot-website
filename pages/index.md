---
title: Functions for safer shell scripting
page-class: index
page-footer: |
  <script>
    addEventListener('load', function () {
      [].forEach.call(document.getElementsByClassName('hello'), function (hello) {
        hello.href = cannot.rot13('znvygb:uryyb@zvrgrx.vb');
      });
    });
  </script>
---


_bashmenot_
===========

_bashmenot_ is a library of functions for safer shell scripting in [GNU _bash_](http://gnu.org/software/bash/), used by [Halcyon](http://halcyon.sh/) and [Haskell on Heroku](http://haskellonheroku.com/).


Usage
-----

```
$ git clone -q --depth=1 -https://github.com/mietek/bashmenot
$ source bashmenot/src.sh
-----> Auto-updating bashmenot... done, fa1afe1
```

See the [programmer’s reference](reference/) for a description of available functions, including examples.


### Dependencies

_bashmenot_ requires [GNU _bash_](http://gnu.org/software/bash/) 4 or newer, and:

- [GNU _date_](http://gnu.org/software/coreutils/manual/html_node/date-invocation.html) for date formatting.
- [GNU _sort_](http://gnu.org/software/coreutils/manual/html_node/sort-invocation.html) for sorting.
- [_curl_](http://curl.haxx.se/) for HTTP transfer.
- [GNU _date_](http://gnu.org/software/coreutils/manual/html_node/date-invocation.html), [_curl_](http://curl.haxx.se/), and [OpenSSL](https://www.openssl.org/) for Amazon S3 storage.
- [_git_](http://git-scm.com/) for automatic updates.


### Bugs

Please report any problems with _bashmenot_ on the [issue tracker](https://github.com/mietek/bashmenot/issues/).

There is a [separate issue tracker](https://github.com/mietek/bashmenot-website/issues/) for problems with the documentation.


About
-----

<span id="mietek"><a class="hello" href=""></a></span>

My name is [Miëtek Bak](http://mietek.io/).  I make software, and _bashmenot_ is one of [my projects](http://mietek.io/projects/).

This work is published under the [MIT X11 license](license/), and supported by my company, [Least Fixed](http://leastfixed.com/).

Like my work?  I am available for consulting on software projects.  Say <a class="hello" href="">hello</a>, or follow <a href="http://twitter.com/mietek">@mietek</a>.


### Acknowledgments

Thanks to [Kenneth Reitz](http://www.kennethreitz.org/) for building [_httpbin_](http://httpbin.org/).

The monospaced font used in this website is [PragmataPro](http://www.fsd.it/fonts/pragmatapro.htm), by [Fabrizio Schiavi](http://www.fsd.it/).  The sans-serif font is [Concourse](http://practicaltypography.com/concourse.html), by [Matthew Butterick](http://practicaltypography.com/).
