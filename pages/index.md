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

_bashmenot_ is a library of functions for safer shell scripting in [GNU _bash_](http://gnu.org/software/bash/), used by [Halcyon](http://halcyon.sh/) and [_Haskell on Heroku_](http://haskellonheroku.com/).


Usage
-----

See the [programmer’s reference](reference/) for a detailed description of each available function, complete with usage examples.

- [Logging module](reference/#logging-module)
- [Expectation control module](reference/#expectation-control-module)
- [OS detection module](reference/#os-detection-module)
- [Quoting module](reference/#quoting-module)
- [Line processing module](reference/#line-processing-module)
- [Sorting module](reference/#sorting-module)
- [Date formatting module](reference/#date-formatting-module)
- [File system module](reference/#file-system-module)
- [Archiving module](reference/#archiving-module)
- [HTTP transfer module](reference/#http-transfer-module)
- [Amazon S3 storage module](reference/#amazon-s3-storage-module)


### Installation

```
$ git clone --depth=1 https://github.com/mietek/bashmenot.git
```


### Dependencies

_bashmenot_ requires [GNU _bash_](http://gnu.org/software/bash/) 4 or newer.

- Date formatting requires [GNU _date_](http://gnu.org/software/coreutils/manual/html_node/date-invocation.html).
- Sorting requires [GNU _sort_](http://gnu.org/software/coreutils/manual/html_node/sort-invocation.html).
- HTTP transfer requires [_curl_](http://curl.haxx.se/).
- Amazon S3 storage requires [GNU _date_](http://gnu.org/software/coreutils/manual/html_node/date-invocation.html), [_curl_](http://curl.haxx.se/), and [OpenSSL](https://www.openssl.org/).


### Bugs

Please report any problems with _bashmenot_ on the [issue tracker](https://github.com/mietek/bashmenot/issues/).

There is a [separate issue tracker](https://github.com/mietek/bashmenot-website/issues/) for problems with the documentation.


About
-----

<span id="mietek"><a class="hello" href=""></a></span>

My name is [Miëtek Bak](http://mietek.io/).  I make software, and _bashmenot_ is one of [my projects](http://mietek.io/projects/).

This work is published under the [MIT X11 license](license/), and supported by my company, [Least Fixed](http://leastfixed.com/).

How can I help you?  Would you like to work with me?  Say <a class="hello" href="">hello</a>.


### Acknowledgments

Thanks to [Kenneth Reitz](http://www.kennethreitz.org/) for building [_httpbin_](http://httpbin.org/).
