---
title: Reference
page-class: add-section-toc rule-before-h3 tweak-listings
page-data:
- key: max-back-link-level
  value: 3
page-head: |
  <style>
    header a.link-reference {
      color: #f0690f;
    }
  </style>
---


_bashmenot_ reference
=====================

_bashmenot_ is a library of [GNU _bash_](https://gnu.org/software/bash/) functions, used by [Halcyon](https://halcyon.sh/) and [Haskell on Heroku](https://haskellonheroku.com/).

This reference is a complete list of available functions and options.


Environment variables
---------------------

### `BASHMENOT_LOG_TIMESTAMP`

> ---------------------|---
> Default value:       | `0`
> Type:                | `0` or `1`

Prefixes each logged message with the current time.


### `BASHMENOT_TIMESTAMP_EPOCH`

> ---------------------|---
> Default value:       | _none_
> Type:                | seconds, optional

When set, any logged timestamps will show the difference between the current time and the specified time, in seconds.


### `BASHMENOT_CURL_RETRIES`

> ---------------------|---
> Default value:       | `5`
> Type:                | integer

Number of times to retry a transfer failing with transient errors.


### `BASHMENOT_APT_DIR`

> ---------------------|---
> Default value:       | _none_
> Type:                | string

_TODO_


### `BASHMENOT_AWS_ACCESS_KEY_ID`

> ---------------------|---
> Default value:       | _none_
> Type:                | 20-character string, optional

Amazon Web Services access key ID, used to authenticate S3 requests.


### `BASHMENOT_AWS_SECRET_ACCESS_KEY`

> ---------------------|---
> Default value:       | _none_
> Type:                | 40-character string, optional

Amazon Web Services secret access key, used to authenticate S3 requests.


### `BASHMENOT_S3_ENDPOINT`

> ---------------------|---
> Default value:       | `s3.amazonaws.com`
> Type:                | address

Address of the [region-specific S3 endpoint](http://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region) in which the referenced S3 buckets are located.


### `BASHMENOT_NO_S3_AUTH`

> ---------------------|---
> Default value:       | `0`
> Type:                | `0` or `1`

Prevents _bashmenot_ from authenticating S3 requests.


### `BASHMENOT_DIR`

> ---------------------|---
> Default value:       | _variable_
> Type:                | _read-only string_
> Command-line option: | _none_

Directory in which _bashmenot_ is installed.

```
$ source "${BASHMENOT_DIR}/src.sh"
```

Automatically set by _bashmenot_ at run-time.


### `BASHMENOT_URL`

> ---------------------|---
> Default value:       | [`https://github.com/mietek/bashmenot`](https://github.com/mietek/bashmenot)
> Type:                | _git_ URL

URL of the _git_ repository from which _bashmenot_ updates itself.

Defaults to the `master` branch.  Other branches can be specified with a `#`_`branch`_ suffix.


### `BASHMENOT_NO_SELF_UPDATE`

> ---------------------|---
> Default value:       | `0`
> Type:                | `0` or `1`

Prevents _bashmenot_ from updating itself.


Date formatting module
----------------------

> ---------------------|---
> Source:              | [`date.sh`](https://github.com/mietek/bashmenot/blob/master/src/date.sh)
> Dependencies:        | [GNU _date_](https://gnu.org/software/coreutils/manual/html_node/date-invocation.html)


### `get_date`

> ---------------------|---
> Arguments:           | _`any*`_

Wrapper for GNU _date_.  Never fails.

Uses `date -u` on Linux and FreeBSD, and `gdate -u` on other platforms, passing any additional arguments to the tool.

```
$ get_date '+%Y-%m-%d'
2014-11-05
```


### `get_http_date`

> ---------------------|---
> Arguments:           | _`any*`_

Outputs a UTC date and time in RFC 2822 format.  Never fails.

Uses `date -Ru` on Linux and FreeBSD, and `gdate -Ru` on other platforms, passing any additional arguments to the tool.

```
$ get_http_date
Fri, 05 Nov 2014 23:59:59 +0000
```


### `get_current_time`

> ---------------------|---
> Arguments:           | _`any*`_

Outputs a UTC date and time as seconds since the <span class="small-caps">Unix</span> epoch.  Never fails.

Uses `date '+%s' -u` on Linux and FreeBSD, and `gdate '+%s' -u` on other platforms, passing any additional arguments to the tool.

```
$ get_current_time
1415231999
```


Sorting module
--------------

> ---------------------|---
> Source:              | [`sort.sh`](https://github.com/mietek/bashmenot/blob/master/src/sort.sh)
> Dependencies:        | [GNU _sort_](https://gnu.org/software/coreutils/manual/html_node/sort-invocation.html)


### `sort_natural`

> ---------------------|---
> Arguments:           | _`any*`_

Portable natural sort.  Never fails.

Uses `sort -V` on Linux and FreeBSD, and `gsort -V` on other platforms, passing any additional arguments to the tool.

```
$ echo -e "foo-1\nfoo-12\nfoo-2" | sort_natural
foo-1
foo-2
foo-12
```
```
$ echo -e "foo-1\nfoo-12\nfoo-2" | sort
foo-1
foo-12
foo-2
```


### `sort0_natural`

> ---------------------|---
> Arguments:           | _`any*`_

Portable natural sort, for input separated by `NUL` bytes instead of newlines.  Never fails.

Uses `sort -Vz` on Linux and FreeBSD, and `gsort -Vz` on other platforms, passing any additional arguments to the tool.


Logging module
--------------

> ---------------------|---
> Source:              | [`log.sh`](https://github.com/mietek/bashmenot/blob/master/src/log.sh)
> Dependencies:        | [`date.sh`](https://github.com/mietek/bashmenot/blob/master/src/date.sh)


### `prefix_log`

> ---------------------|---
> Arguments:           | _`prefix any*`_

Logs arguments to error output with the specified prefix. Never fails.

```
$ prefix_log foo bar
foobar
```


### `prefix_log_begin`

> ---------------------|---
> Arguments:           | _`prefix any*`_

Logs arguments to error output with the specified prefix, and with a space instead of a newline at the end.  Never fails.


### `log`

> ---------------------|---
> Arguments:           | _`any*`_

Logs arguments to error output, prefixed by an arrow marker.  Never fails.

```
$ log fooing
-----> fooing
```


### `log_begin`

> ---------------------|---
> Arguments:           | _`any*`_

Logs arguments to error output, prefixed by an arrow marker, and with a space instead of a newline at the end.  Never fails.


### `log_end`

> ---------------------|---
> Arguments:           | _`any*`_

Logs arguments to error output, with no prefix.  Never fails.

To be paired with [`log_begin`](#log_begin).

```
function foo () {
  log_begin fooing...
  log_end fooed
}
$ foo
-----> fooing... fooed
```


### `log_indent`

> ---------------------|---
> Arguments:           | _`any*`_

Logs arguments to error output, prefixed by whitespace.  Never fails.

For less important messages than [`log`](#log).

```
$ log_indent baring
       baring
```


### `log_indent_begin`

> ---------------------|---
> Arguments:           | _`any*`_

Logs arguments to error output, prefixed by whitespace, and with a space instead of a newline at the end.  Never fails.

For less important messages than [`log_begin`](#log_begin).


### `log_indent_end`

> ---------------------|---
> Arguments:           | _`any*`_

Logs arguments to error output, with no prefix.  Never fails.

To be paired with [`log_indent_begin`](#log_begin).

```
function bar () {
  log_indent_begin baring...
  log_indent_end bared
}
$ bar
       baring... bared
```


### `log_label`

> ---------------------|---
> Arguments:           | _`label`_ _`any*`_

Logs arguments to error output, prefixed by an arrow marker, and with padding between _`label`_ and the other arguments.  Never fails.

```
$ log_label foo: bar
-----> foo:                                      **bar**
```


### `log_indent_label`

> ---------------------|---
> Arguments:           | _`label`_ _`any*`_

Logs arguments to error output, prefixed by whitespace, and with padding between _`label`_ and the other arguments.  Never fails.

For less important messages than [`log_label`](#log_label).

```
$ log_indent_label foo: bar
       foo:                                      **bar**
```


### `log_debug`

> ---------------------|---
> Arguments:           | _`any*`_

Logs arguments to error output, prefixed by a debug marker.  Never fails.

```
$ log_debug foo
**   *** DEBUG: foo**
```


### `log_warning`

> ---------------------|---
> Arguments:           | _`any*`_

Logs arguments to error output, prefixed by a warning marker.  Never fails.

```
$ log_warning foo
**   *** WARNING: foo**
```


### `log_error`

> ---------------------|---
> Arguments:           | _`any*`_

Logs arguments to error output, prefixed by an error marker.  Never fails.

```
$ log_error foo
**   *** ERROR: foo**
```


### `quote`

> ---------------------|---
> Arguments:           | _none_

Pipes input to error output, prefixed by whitespace.  Never fails.

```
$ echo foo | quote
       foo
```


### `die`

> ---------------------|---
> Arguments:           | _`any*`_

Logs an error and exits with `1` as the exit status.

```
function foo () {
  false || die foo
}
$ foo
**   *** ERROR: foo**
^D
```


Expectation control module
--------------------------

> ---------------------|---
> Source:              | [`expect.sh`](https://github.com/mietek/bashmenot/blob/master/src/expect.sh)
> Dependencies:        | [`log.sh`](https://github.com/mietek/bashmenot/blob/master/src/log.sh)


### `expect_args`

> ---------------------|---
> Arguments:           | _`var*`_` -- "$@"`

First, checks the required number of arguments is available; otherwise, dies.  Next, sets the specified variables to the values of the right arguments.

Must be called with a literal ` -- "$@"` after the variable names.  Argument values can be empty.

```
function foo () {
  local bar baz
  expect_args bar baz -- "$@"
  echo "${bar} ${baz}"
}
$ foo
**   *** ERROR: foo: Expected args: bar baz**
^D
```


### `expect_vars`

> ---------------------|---
> Arguments:           | _`var*`_

Checks the specified variables are set and not empty; otherwise, dies.

```
function foo () {
  expect_vars BAR
  echo "${BAR}"
}
$ foo
**   *** ERROR: foo: Expected var: BAR**
^D
```


### `expect_existing`

> ---------------------|---
> Arguments:           | _`thing*`_

Checks the specified files or directories exist; otherwise, fails.

```
function foo () {
  expect_existing bar
  cat bar
}
$ foo
**   *** ERROR: foo: Expected existing bar**
```


### `expect_no_existing`

> ---------------------|---
> Arguments:           | _`thing*`_

Checks the specified files or directories do not exist; otherwise, fails.

```
function foo () {
  expect_no_existing bar
  touch bar
}
$ touch bar
$ foo
**   *** ERROR: foo: Unexpected existing bar**
```


Platform detection module
-------------------------

> ---------------------|---
> Source:              | [`platform.sh`](https://github.com/mietek/bashmenot/blob/master/src/platform.sh)
> Dependencies:        | [`expect.sh`](https://github.com/mietek/bashmenot/blob/master/src/expect.sh)


### `format_platform_description`

> ---------------------|---
> Arguments:           | _`platform`_

Outputs a user-friendly description of the specified platform identifier.  Never fails.

```
$ format_platform_description linux-ubuntu-14.04-x86_64
Ubuntu 14.04 LTS (x86_64)
```


### `detect_os`

> ---------------------|---
> Arguments:           | _none_

Outputs the OS part of the host platform identifier.  Never fails.

```
$ detect_os
linux
```


### `detect_arch`

> ---------------------|---
> Arguments:           | _none_

Outputs the architecture part of the host platform identifier, or nothing.  Never fails.

```
$ detect_arch
x86_64
```


### `detect_platform`

> ---------------------|---
> Arguments:           | _none_

Outputs the host platform identifier.  Never fails.

```
$ detect_platform
linux-ubuntu-14.04-x86_64
```


Line processing module
----------------------

> ---------------------|---
> Source:              | [`line.sh`](https://github.com/mietek/bashmenot/blob/master/src/line.sh)
> Dependencies:        | [`expect.sh`](https://github.com/mietek/bashmenot/blob/master/src/expect.sh)


### `filter_first`

> ---------------------|---
> Arguments:           | _none_

Outputs the first line of input.  Never fails.

```
$ echo -e "foo\nbar\nbaz" | filter_first
foo
```


### `filter_not_first`

> ---------------------|---
> Arguments:           | _none_

Outputs all lines of input except the first.  Never fails.

```
$ echo -e "foo\nbar\nbaz" | filter_not_first
bar
baz
```


### `filter_last`

> ---------------------|---
> Arguments:           | _none_

Outputs the last line of input.  Never fails.

```
$ echo -e "foo\nbar\nbaz" | filter_last
baz
```


### `filter_not_last`

> ---------------------|---
> Arguments:           | _none_

Outputs all lines of input except the last.  Never fails.

```
$ echo -e "foo\nbar\nbaz" | filter_not_last
foo
bar
```


### `filter_matching`

> ---------------------|---
> Arguments:           | _`pattern`_

Outputs all lines of input which match the specified regular expression.  Never fails, unless _`pattern`_ is missing.

_`pattern`_ is an _awk_ regular expression.

```
$ echo -e "foo\nbar\nbaz" | filter_matching '^bar$'
bar
```


### `filter_not_matching`

> ---------------------|---
> Arguments:           | _`pattern`_

Outputs all lines of input which do not match the specified regular expression.  Never fails, unless _`pattern`_ is missing.

_`pattern`_ is an _awk_ regular expression.

```
$ echo -e "foo\nbar\nbaz" | filter_not_matching '^bar$'
foo
baz
```


### `match_at_most_one`

> ---------------------|---
> Arguments:           | _none_

Outputs up to one line of input, when the input consists of up to one line; nothing otherwise.

```
$ echo -n | match_at_most_one ; echo $?
0
```
```
$ echo foo | match_at_most_one ; echo $?
foo
0
```
```
$ echo -e "foo\nbar" | match_at_most_one ; echo $?
1
```


### `match_at_least_one`

> ---------------------|---
> Arguments:           | _none_

Pipes input to output, when the input consists of one line or more; nothing otherwise.

```
$ echo -n | match_at_least_one ; echo $?
1
```
```
$ echo foo | match_at_least_one ; echo $?
foo
0
```
```
$ echo -e "foo\nbar" | match_at_least_one ; echo $?
foo
bar
0
```


### `match_exactly_one`

> ---------------------|---
> Arguments:           | _none_

Outputs one line of input; when the input consists of only one line; nothing otherwise.

```
$ echo -n | match_exactly_one ; echo $?
1
```
```
$ echo foo | match_exactly_one ; echo $?
foo
0
```
```
$ echo -e "foo\nbar" | match_exactly_one ; echo $?
1
```


### `strip_trailing_newline`

> ---------------------|---
> Arguments:           | _none_

Pipes input to output, removing at most one trailing newline.  Never fails.

```
$ echo foo | strip_trailing_newline ; echo
foo
```
```
$ echo -e "foo\n" | strip_trailing_newline
foo
```


File system module
------------------

> ---------------------|---
> Source:              | [`file.sh`](https://github.com/mietek/bashmenot/blob/master/src/file.sh)
> Dependencies:        | [`expect.sh`](https://github.com/mietek/bashmenot/blob/master/src/expect.sh), [`line.sh`](https://github.com/mietek/bashmenot/blob/master/src/line.sh), [`sort.sh`](https://github.com/mietek/bashmenot/blob/master/src/sort.sh)


### `get_tmp_file`

> ---------------------|---
> Arguments:           | _`base`_

Outputs an absolute path to a unique temporary file.

```
$ get_tmp_file foo
/tmp/foo.Lzi6bRzLS0
```


### `get_tmp_dir`

> ---------------------|---
> Arguments:           | _`base`_

Outputs an absolute path to a unique temporary directory.

```
$ get_tmp_dir foo
/tmp/foo.Gf9J615PeE
```


### `get_size`

> ---------------------|---
> Arguments:           | _`thing`_

Outputs a user-friendly summary size of the data contained in the specified file or directory.

```
$ get_size foo
868MB
```


### `get_modification_time`

> ---------------------|---
> Arguments:           | _`thing`_

Outputs the modification time of the specified file or directory, in seconds since the <span class="small-caps">Unix</span> epoch.

Uses `stat -c "%Y"` on Linux, and `stat -f "%m"` on FreeBSD and other platforms.

```
$ touch foo
$ get_modification_time foo
1415379516
```


### `get_dir_path`

> ---------------------|---
> Arguments:           | _`dir`_

Outputs an absolute path to the specified directory, collapsing any symbolic links.

```
$ get_dir_path .
/foo/bar/baz
```


### `get_dir_name`

> ---------------------|---
> Arguments:           | _`dir`_

Outputs the name of the specified directory.

```
$ get_dir_name .
baz
```


### `get_link_path`

> ---------------------|---
> Arguments:           | _`link`_

_TODO_


### `find_tree`

> ---------------------|---
> Arguments:           | _`dir any*`_

Outputs relative paths to found files.  Never fails.

Uses `find`, passing any additional arguments to the tool.

```
$ mkdir foo foo/bar
$ touch foo/bar/baz
$ find_tree foo
bar/baz
```


### `find_added`

> ---------------------|---
> Arguments:           | _`old_dir new_dir`_

Outputs relative paths to files which do not exist in the old directory and exist in the new one, in natural order.  Never fails.

```
$ mkdir foo1 foo2
$ touch foo2/bar2
$ find_added foo1 foo2
bar2
```


### `find_changed`

> ---------------------|---
> Arguments:           | _`old_dir new_dir`_

Outputs relative paths to files which differ between the two directories, in natural order.  Never fails.

```
$ mkdir foo1 foo2
$ echo bar1 >foo1/bar
$ echo bar2 >foo2/bar
$ find_changed foo1 foo2
bar
```


### `find_not_changed`

> ---------------------|---
> Arguments:           | _`old_dir new_dir`_

Outputs relative paths to files which do not differ between the two directories, in natural order.  Never fails.

Complementary to [find_changed](#find_changed).

```
$ mkdir foo1 foo2
$ echo baz >foo1/baz
$ echo baz >foo2/baz
$ find_not_changed foo1 foo2
baz
```


### `find_removed`

> ---------------------|---
> Arguments:           | _`old_dir new_dir`_

Outputs relative paths to files which exist in the old directory and do not exist in the new one, in natural order.  Never fails.

```
$ mkdir foo1 foo2
$ touch foo1/bar1
$ find_removed foo1 foo2
bar1
```


### `compare_tree`

> ---------------------|---
> Arguments:           | _`old_dir new_dir`_

Like [`find_added`](#find_added), [`find_changed`](#find_changed), [`find_not_changed`](#find_not_changed), and [`find_removed`](#find_removed) combined.  Never fails.

Prefixes paths by `+` for added, `*` for changed, `=` for not changed, and `-` for removed.

```
$ mkdir foo1 foo2
$ touch foo1/bar1 foo2/bar2
$ echo bar1 >foo1/bar
$ echo bar2 >foo2/bar
$ echo baz >foo1/baz
$ echo baz >foo2/baz
$ compare_tree foo1 foo2
- bar1
+ bar2
* bar
= baz
```


Hashing module
--------------

> ---------------------|---
> Source:              | [`hash.sh`](https://github.com/mietek/bashmenot/blob/master/src/hash.sh)
> Dependencies:        | [`expect.sh`](https://github.com/mietek/bashmenot/blob/master/src/expect.sh), [`sort.sh`](https://github.com/mietek/bashmenot/blob/master/src/sort.sh), [OpenSSL](https://openssl.org/)


### `get_hash`

> ---------------------|---
> Arguments:           | _none_

Outputs a SHA1 digest of the input, when the input consists of at least one line; nothing otherwise.

```
$ echo foo | do_hash
f1d2d2f924e986ac86fdf7b36c94bcdf32beec15
```


### `hash_tree`

> ---------------------|---
> Arguments:           | _`dir any*`_

Outputs a summary SHA1 digest of the data contained in all files found in the specified directory, when the directory contains at least one file; nothing otherwise.

Uses `find`, passing any additional arguments to the tool.  Sorts files by relative path before hashing.

```
$ mkdir foo
$ touch foo/bar
$ hash_tree foo
df1d77216a4168ceb2112b2078ebc7d5fc6ac446
```


Archiving module
----------------

> ---------------------|---
> Source:              | [`tar.sh`](https://github.com/mietek/bashmenot/blob/master/src/tar.sh)
> Dependencies:        | [`log.sh`](https://github.com/mietek/bashmenot/blob/master/src/log.sh), [`expect.sh`](https://github.com/mietek/bashmenot/blob/master/src/expect.sh), [`file.sh`](https://github.com/mietek/bashmenot/blob/master/src/file.sh)


### `copy_file`

> ---------------------|---
> Arguments:           | _`src_file dst_file`_

Copies the specified file over the destination file.

Overwrites existing files.  Creates the destination directory if needed.


### `copy_dir_entry_into`

> ---------------------|---
> Arguments:           | _`src_dir src_file dst_dir`_

_TODO_


### `copy_dir_glob_into`

> ---------------------|---
> Arguments:           | _`src_dir src_glob dst_dir`_

_TODO_


### `copy_dir_into`

> ---------------------|---
> Arguments:           | _`src_dir dst_dir`_

Copies the contents of the specified directory into the destination directory.

Overwrites existing files.  Creates the destination directory if needed.  Uses `tar`, passing any additional arguments to the tool.


### `copy_dir_over`

> ---------------------|---
> Arguments:           | _`src_dir dst_dir`_

Copies the contents of the specified directory over the destination directory.

Removes the destination directory.  Creates the destination directory if needed.  Uses `tar`, passing any additional arguments to the tool.


### `create_archive`

> ---------------------|---
> Arguments:           | _`src_dir dst_file`_

Creates an archive of the contents of the specified directory.

Overwrites existing files.  Creates the destination directory if needed.  Uses `tar`, passing any additional arguments to the tool.

The `gz`, `bz2`, and `xz` compression formats are supported.  The `pigz`, `pbzip2`, and `pxz` compression tools are used, when available.

```
$ create_archive foo bar.tar.gz
       Creating bar.tar.gz... done, 8.0KB
```


### `extract_archive_into`

> ---------------------|---
> Arguments:           | _`src_file dst_dir`_

Extracts the specified archive into the destination directory.

Overwrites existing files.  Creates the destination directory if needed.  Uses `tar`, passing any additional arguments to the tool.

The `gz`, `bz2`, and `xz` compression formats are supported.  The `pigz`, `pbzip2`, and `pxz` compression tools are used, when available.

```
$ extract_archive_into bar.tar.gz baz
       Extracting bar.tar.gz... done, 12KB
```


### `extract_archive_over`

> ---------------------|---
> Arguments:           | _`src_file dst_dir`_

Extracts the specified archive over the destination directory.

Removes the destination directory.  Creates the destination directory if needed.  Uses `tar`, passing any additional arguments to the tool.

The `gz`, `bz2`, and `xz` compression formats are supported.  The `pigz`, `pbzip2`, and `pxz` compression tools are used, when available.


### `strip_tree`

> ---------------------|---
> Arguments:           | _`dir any*`_

Strips object file symbols from all files found in the specified directory.  Never fails.

Uses `strip --strip-unneeded` on Linux and FreeBSD, `strip -u -r` on OS X, and does nothing on other platforms.  Also uses `find`, passing any additional arguments to the tool.


Version control module
----------------------

> ---------------------|---
> Source:              | [`git.sh`](https://github.com/mietek/bashmenot/blob/master/src/git.sh)
> Dependencies:        | [`expect.sh`](https://github.com/mietek/bashmenot/blob/master/src/expect.sh), [_git_](http://git-scm.com/)


### `validate_git_url`

> ---------------------|---
> Arguments:           | _`url`_

Checks whether the specified URL starts with a URL scheme supported by _git_.

```
$ validate_git_url https://github.com/mietek/bashmenot ; echo $?
0
```
```
$ validate_git_url foo ; echo $?
1
```


### `git_do`

> ---------------------|---
> Arguments:           | _`work_dir cmd any*`_

Wrapper for _git_.

Used by the following functions in this module.  Passes any additional arguments to the tool.


### `quiet_git_do`

> ---------------------|---
> Arguments:           | _`work_dir cmd any*`_

Wrapper for _git_, ignoring all output.

Passes any additional arguments to the tool.


### `hash_newest_git_commit`

> ---------------------|---
> Arguments:           | _`dir`_

Outputs a SHA1 digest of the specified repository `HEAD`, when the repository is not empty; nothing otherwise.  Never fails, unless _`dir`_ does not exist.

```
$ hash_newest_git_commit .
d0ed0f48014efba06069abe3e1776a379612a0fa
```


### `git_clone_over`

> ---------------------|---
> Arguments:           | _`url dir`_

Clones the specified repository over the destination directory, along with any submodules, and outputs the hash of the newest commit.

Removes the destination directory.  Creates the destination directory if needed.

Defaults to the `master` branch.  Other branches can be specified with a `#`_`branch`_ suffix.

```
$ git_clone_over https://github.com/mietek/bashmenot foo
df22d6d7b0d7ca83195088206e689f6d13ac2be0
```


### `git_update_into`

> ---------------------|---
> Arguments:           | _`url dir`_

Ensures the destination directory contains an up-to-date checkout of the specified repository, along with any submodules, and outputs the hash of the newest commit.

Defaults to the `master` branch.  Other branches can be specified with a `#`_`branch`_ suffix.

```
$ git_update_into https://github.com/mietek/bashmenot foo
df22d6d7b0d7ca83195088206e689f6d13ac2be0
```


### `git_acquire`

> ---------------------|---
> Arguments:           | _`src_dir thing dst_dir`_

_TODO_


### `git_acquire_all`

> ---------------------|---
> Arguments:           | _`src_dir things dst_dir`_

_TODO_


Package installation module
---------------------------

> ---------------------|---
> Source:              | [`package.sh`](https://github.com/mietek/bashmenot/blob/master/src/package.sh)
> Dependencies:        | [`date.sh`](https://github.com/mietek/bashmenot/blob/master/src/date.sh), [`sort.sh`](https://github.com/mietek/bashmenot/blob/master/src/sort.sh), [`log.sh`](https://github.com/mietek/bashmenot/blob/master/src/log.sh), [`expect.sh`](https://github.com/mietek/bashmenot/blob/master/src/expect.sh), [`platform.sh`](https://github.com/mietek/bashmenot/blob/master/src/platform.sh), [`line.sh`](https://github.com/mietek/bashmenot/blob/master/src/line.sh), [`file.sh`](https://github.com/mietek/bashmenot/blob/master/src/file.sh)


### `fix_broken_links`

> ---------------------|---
> Arguments:           | _`dst_dir`_

_TODO_


### `install_deb_package`

> ---------------------|---
> Arguments:           | _`package_file dst_dir`_

_TODO_


### `install_rpm_package`

> ---------------------|---
> Arguments:           | _`package_file dst_dir`_

_TODO_


### `install_debian_packages`

> ---------------------|---
> Arguments:           | _`names dst_dir`_

_TODO_


### `install_redhat_packages`

> ---------------------|---
> Arguments:           | _`names dst_dir`_

_TODO_


### `install_platform_packages`

> ---------------------|---
> Arguments:           | _`specs dst_dir`_

_TODO_


Remote storage module
---------------------

> ---------------------|---
> Source:              | [`curl.sh`](https://github.com/mietek/bashmenot/blob/master/src/curl.sh)
> Dependencies:        | [`log.sh`](https://github.com/mietek/bashmenot/blob/master/src/log.sh), [`expect.sh`](https://github.com/mietek/bashmenot/blob/master/src/expect.sh), [_curl_](http://curl.haxx.se/)


### `format_http_code_description`

> ---------------------|---
> Arguments:           | _`code`_

Outputs a user-friendly description of the specified HTTP code.  Never fails.

```
$ format_http_code_description 418
418 I'm a teapot
```


### `curl_do`

> ---------------------|---
> Arguments:           | _`url any*`_

Wrapper for _curl_.

Used by every function in this module.   Passes any additional arguments to the tool.


### `curl_download`

> ---------------------|---
> Arguments:           | _`src_file_url dst_file`_

Downloads the specified resource with HTTP `GET`.

Overwrites existing files.  Creates the destination directory if needed.

```
$ curl_download httpbin.org/get foo
       Downloading httpbin.org/get... done
```


### `curl_check`

> ---------------------|---
> Arguments:           | _`src_url`_

Accesses the specified resource with HTTP `HEAD`.

```
$ curl_check httpbin.org/status/404
       Checking httpbin.org/status/404... 404 (not found)
```


### `curl_upload`

> ---------------------|---
> Arguments:           | _`src_file dst_file_url`_

Uploads the specified file with HTTP `PUT`.

Overwrites existing resources.

```
$ curl_upload foo httpbin.org/put
       Uploading httpbin.org/put... done
```


### `curl_delete`

> ---------------------|---
> Arguments:           | _`dst_url`_

Deletes the specified resource with HTTP `DELETE`.

```
$ curl_delete httpbin.org/delete
       Deleting httpbin.org/delete... done
```


Amazon S3 storage module
------------------------

> ---------------------|---
> Source:              | [`s3.sh`](https://github.com/mietek/bashmenot/blob/master/src/s3.sh)
> Dependencies:        | [`log.sh`](https://github.com/mietek/bashmenot/blob/master/src/log.sh), [`expect.sh`](https://github.com/mietek/bashmenot/blob/master/src/expect.sh), [`line.sh`](https://github.com/mietek/bashmenot/blob/master/src/line.sh), [`date.sh`](https://github.com/mietek/bashmenot/blob/master/src/date.sh), [`curl.sh`](https://github.com/mietek/bashmenot/blob/master/src/curl.sh), [GNU _date_](https://gnu.org/software/coreutils/manual/html_node/date-invocation.html), [_curl_](http://curl.haxx.se/), [OpenSSL](https://openssl.org/)


### `format_s3_url`

> ---------------------|---
> Arguments:           | _`resource`_

Outputs the S3 URL of the specified resource.

References [`BASHMENOT_S3_ENDPOINT`](#bashmenot_s3_endpoint).

```
$ format_s3_url /foo/bar
https://s3.amazonaws.com/foo/bar
```


### `read_s3_listing_xml`

> ---------------------|---
> Arguments:           | _none_

Parses an S3 bucket listing in XML format into a file of objects.


### `s3_do`

> ---------------------|---
> Arguments:           | _`url any*`_

S3-specific wrapper for [`curl_do`](#curl_do), supporting [S3 REST authentication](https://docs.aws.amazon.com/AmazonS3/latest/dev/RESTAuthentication.html).

Used by most functions in this module.  References [`BASHMENOT_AWS_ACCESS_KEY_ID`](#bashmenot_aws_access_key_id) and [`BASHMENOT_AWS_SECRET_ACCESS_KEY`](#bashmenot_aws_secret_access_key), unless [`BASHMENOT_NO_S3_AUTH`](#bashmenot_no_s3_auth) is set to `1`.  Uses `curl`, passing any additional arguments to the tool.


### `s3_download`

> ---------------------|---
> Arguments:           | _`src_bucket src_object dst_file`_

Downloads the specified resource from S3 with HTTP `GET`.

Overwrites existing files.  Creates the destination directory if needed.

```
$ s3_download foo.example.com foo/bar bar
       Downloading s3://foo.example.com/foo/bar... done
```


### `s3_check`

> ---------------------|---
> Arguments:           | _`src_bucket src_object`_

Accesses the specified S3 resource with HTTP `HEAD`.

An empty source object can be specified to access the bucket itself.

```
$ s3_check foo.example.com no-foo
       Checking s3://foo.example.com/no-foo... 404 (not found)
```


### `s3_upload`

> ---------------------|---
> Arguments:           | _`src_file dst_bucket dst_object dst_acl`_

Uploads the specified file to S3 with HTTP `PUT`.

Overwrites existing resources.  The destination resource is assigned the specified [S3 ACL](https://docs.aws.amazon.com/AmazonS3/latest/dev/S3_ACLs_UsingACLs.html).

Commonly used values are `private` and `public-read`.

```
$ s3_upload foo foo.example.com bar/foo private
       Uploading s3://foo.example.com/bar/foo... done
```


### `s3_create`

> ---------------------|---
> Arguments:           | _`dst_bucket dst_acl`_

Creates an S3 bucket with HTTP `PUT`.

The destination is assigned the specified [S3 ACL](https://docs.aws.amazon.com/AmazonS3/latest/dev/S3_ACLs_UsingACLs.html).

```
$ s3_create foo.example.com private
       Creating s3://foo.example.com/... done
```


### `s3_copy`

> ---------------------|---
> Arguments:           | _`src_bucket src_object dst_bucket dst_object dst_acl`_

Copies the specified resource on S3 with HTTP `PUT`, without downloading or uploading the resource data.

The source and destination can be the same bucket or separate buckets.  The destination is assigned the specified [S3 ACL](https://docs.aws.amazon.com/AmazonS3/latest/dev/S3_ACLs_UsingACLs.html).

```
$ s3_copy foo.example.com foo bar.example.com bar private
       Copying s3://foo.example.com/foo to s3://bar.example.com/bar... done
```


### `s3_delete`

> ---------------------|---
> Arguments:           | _`dst_bucket dst_object`_

Deletes the specified resource from S3 with HTTP `DELETE`.

An empty destination object can be specified to delete the bucket itself.

```
$ s3_delete foo.example.com foo/bar
       Deleting s3://foo.example.com/foo/bar... 204 (no content)
```
```
$ s3_delete foo.example.com ''
       Deleting s3://foo.example.com/... 204 (no content)
```


### `curl_list_s3`

> ---------------------|---
> Arguments:           | _`url`_

Outputs the contents of a publicly-accessible S3 bucket referenced by the specified URL.

```
$ curl_list_s3 https://s3.amazonaws.com/foo.example.com/
       Listing https://s3.amazonaws.com/foo.example.com/... done
foo/bar
bar/baz/foo
baz
```


### `s3_list`

> ---------------------|---
> Arguments:           | _`src_bucket src_prefix`_

Outputs the contents of the specified S3 bucket, downloaded with HTTP `GET`, listing the resources which start with the specified prefix.

An empty prefix can be specified to list the contents of the entire bucket.

```
$ s3_list foo.example.com foo
       Listing s3://foo.example.com/?prefix=foo... done
foo/bar
```
```
$ s3_list foo.example.com ''
       Listing s3://foo.example.com/... done
foo/bar
bar/baz/foo
baz
```
