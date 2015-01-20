---
title: Library of GNU bash functions
page-description: bashmenot is a library of GNU bash functions.
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

_bashmenot_ is a library of [GNU _bash_](https://gnu.org/software/bash/) functions, used by [Halcyon](https://halcyon.sh/) and [Haskell on Heroku](https://haskellonheroku.com/).


### Support

Please report any problems with _bashmenot_ on the [issue tracker](https://github.com/mietek/bashmenot/issues/).  There is a [separate issue tracker](https://github.com/mietek/bashmenot-website/issues/) for problems with the documentation.


Usage
-----

```
$ source bashmenot/src.sh
```

_bashmenot_ can be installed by cloning the [_git_ repository](https://github.com/mietek/bashmenot):

```
$ git clone https://github.com/mietek/bashmenot
```


### Documentation

- See the [_bashmenot_ reference](https://bashmenot.mietek.io/reference/) for a complete list of available functions and options.

- Read the [_bashmenot_ source code](https://github.com/mietek/bashmenot) to understand how it works.


#### Dependencies

_bashmenot_ is written in [GNU _bash_](https://gnu.org/software/bash/), and requires:

- [GNU _date_](https://gnu.org/software/coreutils/manual/html_node/date-invocation.html) — for date formatting
- [GNU _sort_](https://gnu.org/software/coreutils/manual/html_node/sort-invocation.html) — for sorting
- [_curl_](http://curl.haxx.se/) — for remote storage
- [OpenSSL](https://openssl.org/) — for hashing and Amazon S3 storage
- [_git_](http://git-scm.com/) — for self-updates


About
-----

<div class="aside-like">
<a class="face mietek" href="https://mietek.io/"></a>
<blockquote>_My name is [Miëtek Bak](https://mietek.io/).  I make software, and _bashmenot_ is one of [my projects](https://mietek.io/projects/)._

_This work is published under the [MIT X11 license](/license/), and supported by my company, [Least Fixed](https://leastfixed.com/)._

_Like my work?  I am available for consulting.  Say <a class="hello" href="">hello</a>, or follow <a href="https://twitter.com/mietek">@mietek</a>._
</blockquote>
</div>


### Acknowledgments

Thanks to [Kenneth Reitz](http://kennethreitz.org/) for building [_httpbin_](https://httpbin.org/).

The monospaced font is [PragmataPro](http://fsd.it/fonts/pragmatapro.htm), by [Fabrizio Schiavi](http://fsd.it/).  The sans-serif font is [Concourse](http://practicaltypography.com/concourse.html), by [Matthew Butterick](http://practicaltypography.com/).  Website built with [_cannot_](https://cannot.mietek.io/).
