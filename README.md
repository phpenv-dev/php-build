# php-build

php-build is an [phpenv](https://github.com/phpenv-dev/phpenv) plugin
that provides an `phpenv install` command to compile and install
different versions of PHP on UNIX-like systems.

You can also use php-build without phpenv in environments where you
need precise control over PHP version installation.

_This project was forked from [ruby-build](https://github.com/rbenv/ruby-build),
and modified for PHP._

## Installation

### Installing as an phpenv plugin (recommended)

Installing php-build as an phpenv plugin will give you access to the
`phpenv install` command.

    $ mkdir -p ~/.phpenv/plugins
    $ cd ~/.phpenv/plugins
    $ git clone git://github.com/phpenv-dev/php-build.git

This will install the latest development version of php-build into
the `~/.phpenv/plugins/php-build` directory. From that directory, you
can check out a specific release tag. To update php-build, run `git
pull` to download the latest changes.

### Installing as a standalone program (advanced)

Installing php-build as a standalone program will give you access to
the `php-build` command for precise control over PHP version
installation. If you have phpenv installed, you will also be able to
use the `phpenv install` command.

    $ git clone git://github.com/phpenv-dev/php-build.git
    $ cd php-build
    $ ./install.sh

This will install php-build into `/usr/local`. If you do not have
write permission to `/usr/local`, you will need to run `sudo
./install.sh` instead. You can install to a different prefix by
setting the `PREFIX` environment variable.

To update php-build after it has been installed, run `git pull` in
your cloned copy of the repository, then re-run the install script.

## Usage

### Using `phpenv install` with phpenv

To install a PHP version for use with phpenv, run `phpenv install` with
the exact name of the version you want to install. For example,

    $ phpenv install 7.2.11

PHP versions will be installed into a directory of the same name
under `~/.phpenv/versions`.

To see a list of all available PHP versions, run `phpenv install`
without any arguments. You may also tab-complete available PHP
versions if your phpenv installation is properly configured.

### Using `php-build` standalone

If you have installed php-build as a standalone program, you can use
the `php-build` command to compile and install PHP versions into
specific locations.
Run the `php-build` command with the exact name of the version you
want to install and the full path where you want to install it. For
example,

    $ php-build 7.2.11 ~/local/php-7.2.11

To see a list of all available PHP versions, run `php-build
--definitions`.

Pass the `-v` or `--verbose` flag to `php-build` as the first
argument to see what's happening under the hood.

### Custom definitions

Both `phpenv install` and `php-build` accept a path to a custom
definition file in place of a version name. Custom definitions let you
develop and install versions of PHP that are not yet supported by
php-build.

See the [php-build built-in
definitions](https://github.com/phpenv-dev/php-build/tree/share/php-build)
as a starting point for custom definition files.

### Special environment variables

You can set certain environment variables to control the build
process.

* `TMPDIR` sets the location where php-build stores temporary files.
* `PHP_BUILD_BUILD_PATH` sets the location in which sources are
  downloaded and built. By default, this is a subdirectory of
  `TMPDIR`.
* `CC` sets the path to the C compiler.
* `CONFIGURE_OPTS` lets you pass additional options to `./configure`.
* `MAKE_OPTS` (or `MAKEOPTS`) lets you pass additional options to
  `make`.

### Keeping the build directory after installation

Both `php-build` and `phpenv install` accept the `-k` or `--keep`
flag, which tells php-build to keep the downloaded source after
installation. This can be useful if you need to use many extensions
with PHP.

Source code will be kept in a parallel directory tree
`~/.phpenv/sources` when using `--keep` with the `phpenv install`
command. You should specify the location of the source code with the
`PHP_BUILD_BUILD_PATH` environment variable when using `--keep` with
`php-build`.

## Getting Help

Please see the [php-build
wiki](https://github.com/phpenv-dev/php-build/wiki) for solutions to
common problems.

If you can't find an answer on the wiki, open an issue on the [issue
tracker](https://github.com/phpenv-dev/php-build/issues). Be sure to
include the full build log for build failures.

### License

(The MIT License)

Copyright (c) 2017 Septian Dwic.\
Copyright (c) 2011 Sam Stephenson

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
