---
title: Functions for safer shell scripting
page-class: index
page-footer: |
  <script>
    addEventListener('load', function () {
      document.getElementById('hello').href = cannot.rot13('znvygb:uryyb@yrnfgsvkrq.pbz');
    });
  </script>
---


Functions for safer shell scripting
===================================

Used in [Halcyon](http://halcyon.sh/) and [Haskell on Heroku](http://haskellonheroku.com/).


Usage
-----

_bashmenot_ is a library of functions for safer shell scripting in [GNU _bash_](http://gnu.org/software/bash/).

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
$ git clone https://github.com/mietek/bashmenot.git
```

Also available as a [Bower](http://bower.io/) package.

```
$ bower install bashmenot
```


### Dependencies

_bashmenot_ requires [GNU _bash_](http://gnu.org/software/bash/) 4 or newer.

- Date formatting requires [GNU _date_](https://www.gnu.org/software/coreutils/manual/html_node/date-invocation.html).
- Sorting requires [GNU _sort_](https://www.gnu.org/software/coreutils/manual/html_node/sort-invocation.html).
- HTTP transfer requires [_curl_](http://curl.haxx.se/).
- Amazon S3 storage requires [GNU _date_](https://www.gnu.org/software/coreutils/manual/html_node/date-invocation.html), [_curl_](http://curl.haxx.se/), and [OpenSSL](https://www.openssl.org/).


Support
-------

Please report any problems with _bashmenot_ on the [issue tracker](https://github.com/mietek/bashmenot/issues/).  There is a [separate issue tracker](https://github.com/mietek/bashmenot-website/issues/) for problems with the documentation.

Commercial support for _bashmenot_ is offered by [Least Fixed](http://leastfixed.com/), a functional software consultancy.

Need help?  Say <a href="" id="hello">hello</a>.


License
-------

Made by [Miëtek Bak](http://mietek.io/).  Published under the [MIT X11 license](license/).
