---
title: Shell function library
page-class: index tweak-listings
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

_bashmenot_ is a library of shell functions for [GNU _bash_](https://gnu.org/software/bash/), used by [Halcyon](https://halcyon.sh/) and [Haskell on Heroku](https://haskellonheroku.com/).


Usage
-----

_bashmenot_ is installed by cloning the source repository, and updates itself automatically when the top-level [`src.sh`](https://github.com/mietek/bashmenot/blob/master/src.sh) file is sourced.

```
$ git clone https://github.com/mietek/bashmenot
$ source bashmenot/src.sh
```

To disable automatic updates, set [`BASHMENOT_NO_AUTOUPDATE`](options/#bashmenot_no_autoupdate) to `1`.

Individual _bashmenot_ modules can also be sourced separately, as long as their dependencies are sourced in the appropriate order.


### Dependencies

- [GNU _bash_](https://gnu.org/software/bash/) 4 or newer
- [GNU _date_](https://gnu.org/software/coreutils/manual/html_node/date-invocation.html)—for date formatting
- [GNU _sort_](https://gnu.org/software/coreutils/manual/html_node/sort-invocation.html)—for sorting
- [_curl_](http://curl.haxx.se/)—for HTTP transfer
- [OpenSSL](https://openssl.org/)—for hashing and Amazon S3 storage
- [_git_](http://git-scm.com/)—for automatic updates


### Documentation

- [Function reference](functions/)
- [Option reference](options/)
- [Source code](https://github.com/mietek/bashmenot/)


### Support

Please report any problems with _bashmenot_ on the [issue tracker](https://github.com/mietek/bashmenot/issues/).  There is a [separate issue tracker](https://github.com/mietek/bashmenot-website/issues/) for problems with the documentation.


About
-----

<span id="mietek"><a class="hello" href=""></a></span>

My name is [Miëtek Bak](https://mietek.io/).  I make software, and _bashmenot_ is one of [my projects](https://mietek.io/projects/).

This work is published under the [MIT X11 license](license/), and supported by my company, [Least Fixed](https://leastfixed.com/).

Like my work?  I am available for consulting.  Say <a class="hello" href="">hello</a>, or follow <a href="https://twitter.com/mietek">@mietek</a>.


### Acknowledgments

Thanks to [Kenneth Reitz](http://kennethreitz.org/) for building [_httpbin_](https://httpbin.org/).

The monospaced font used in this website is [PragmataPro](http://fsd.it/fonts/pragmatapro.htm), by [Fabrizio Schiavi](http://fsd.it/).  The sans-serif font is [Concourse](http://practicaltypography.com/concourse.html), by [Matthew Butterick](http://practicaltypography.com/).  Website built with [_cannot_](https://cannot.mietek.io/).
