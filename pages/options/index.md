---
title: Option reference
page-class: add-section-toc tweak-listings
page-head: |
  <style>
    header a.link-options {
      color: #f0690f;
    }
  </style>
---


Option reference
================


Automatic update options
------------------------

### `BASHMENOT_URL`

> ---------------------|---
> Default value:       | [`https://github.com/mietek/bashmenot`](https://github.com/mietek/bashmenot)

URL of the _git_ repository used for automatic updates.

Defaults to the `master` branch.  Another branch may be specified with a `#`_`branch`_ suffix.


### `BASHMENOT_NO_AUTOUPDATE`

> ---------------------|---
> Default value:       | `0`

Disables automatic updates.


Amazon S3 storage options
-------------------------

### `BASHMENOT_AWS_ACCESS_KEY_ID`

> ---------------------|---
> Default value:       | _none_

Identifier used to authenticate S3 requests.


### `BASHMENOT_AWS_SECRET_ACCESS_KEY`

> ---------------------|---
> Default value:       | _none_

Secret used to authenticate S3 requests.


### `BASHMENOT_S3_HOST`

> ---------------------|---
> Default value:       | `s3.amazonaws.com`

Address used to direct S3 requests.
