Adblock Minus for Chrome - Blocking Disabled!  AJW 5/2016
=========================================

Preface
---------
This README.md (and indeed this entire project) is a lightly modified 
version of that found in the Adblock Plus for Chrome repo here:

https://hg.adblockplus.org/adblockpluschrome

=========================================

This repository contains the Adblock Minus source code for
Chrome, as well as some residual Adblock Plus files for Opera and Safari. 
It can be used to build Adblock Minus for Chrome.  Generic Adblock Plus/Minus 
code will be extracted from other repositories
automatically (see _dependencies_ file).

Building
---------

### Requirements

- [Python 2.7](https://www.python.org)
- [The Jinja2 module](http://jinja.pocoo.org/docs)
- [The PIL module](http://www.pythonware.com/products/pil/)
- For signed Chrome builds: [M2Crypto module](https://github.com/martinpaljak/M2Crypto)
- For signed Safari builds: A [patched version of the xar command line tool](https://github.com/mackyle/xar/)

### Building the extension

Run the following command in the project directory:

    ./build.py -t chrome build -k adblockpluschrome-noblock.pem

This will create a build with a name in the form
_adblockpluschrome-noblock-1.2.3.nnnn.crx_.
Note that you don't need an existing signing key for Chrome, a new key
will be created automatically if the file doesn't exist.

### Development environment

To simplify the process of testing your changes you can create an unpacked
development environment. For that run one of the following commands:

    ./build.py -t chrome devenv

This will create a _devenv.platform_ directory in the repository. In Chrome you
should load _devenv.chrome_ as an unpacked extension directory. After making
changes to the source code re-run the command to update the development
environment, the extension should reload automatically after a few seconds.

Running the unit tests
----------------------

To verify your changes you can use the unit test suite located in the _qunit_
directory of the repository. In order to run the unit tests go to the
extension's Options page, open the JavaScript Console and type in:

    location.href = "qunit/index.html";

The unit tests will run automatically once the page loads.
NOTE: Several of the unit tests are failing.  This is true even 
for the unmodified code for Adblock Plus.
