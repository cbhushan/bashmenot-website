---
title: Shell function library
page-description: bashmenot is a library of shell functions for GNU bash.
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

_bashmenot_ is a library of shell functions, used by [Halcyon](https://halcyon.sh/) and [Haskell on Heroku](https://haskellonheroku.com/).


### Support

Please report any problems with _bashmenot_ on the [issue tracker](https://github.com/mietek/bashmenot/issues/).  There is a [separate issue tracker](https://github.com/mietek/bashmenot-website/issues/) for problems with the documentation.


Usage
-----

_bashmenot_ is installed with _git_, and automatically updates when the top-level `src.sh` file is sourced.

<pre class="with-tweaks"><code><span class="prompt">$</span> <span class="input">git clone <a href="https://github.com/mietek/bashmenot/">https://github.com/mietek/bashmenot</a></span>
<span class="prompt">$</span> <span class="input">source bashmenot/src.sh</span>
</code></pre>


### Documentation

<div><nav>
<ul class="menu open">
<li><a href="/reference/">Programmer’s reference</a></li>
<li><a href="https://github.com/mietek/bashmenot/">Source code</a></li>
</ul>
</nav></div>


### Dependencies

_bashmenot_ is built with [GNU _bash_](https://gnu.org/software/bash/) 4, and requires:

- [GNU _date_](https://gnu.org/software/coreutils/manual/html_node/date-invocation.html) — for date formatting
- [GNU _sort_](https://gnu.org/software/coreutils/manual/html_node/sort-invocation.html) — for sorting
- [_curl_](http://curl.haxx.se/) — for remote storage
- [OpenSSL](https://openssl.org/) — for hashing and Amazon S3 storage
- [_git_](http://git-scm.com/) — for self-updates


About
-----

<span id="mietek"></span>

My name is [Miëtek Bak](https://mietek.io/).  I make software, and _bashmenot_ is one of [my projects](https://mietek.io/projects/).

This work is published under the [MIT X11 license](/license/), and supported by my company, [Least Fixed](https://leastfixed.com/).

Like my work?  I am available for consulting.  Say <a class="hello" href="">hello</a>, or follow <a href="https://twitter.com/mietek">@mietek</a>.


### Acknowledgments

Thanks to [Kenneth Reitz](http://kennethreitz.org/) for building [_httpbin_](https://httpbin.org/).

The monospaced font used in this website is [PragmataPro](http://fsd.it/fonts/pragmatapro.htm), by [Fabrizio Schiavi](http://fsd.it/).  The sans-serif font is [Concourse](http://practicaltypography.com/concourse.html), by [Matthew Butterick](http://practicaltypography.com/).  Website built with [_cannot_](https://cannot.mietek.io/).

This project is not affiliated with [Heroku](https://heroku.com/) or [Amazon](https://amazon.com/).
