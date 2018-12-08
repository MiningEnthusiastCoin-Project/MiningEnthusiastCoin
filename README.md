MiningEnthusiastCoin Core integration/staging tree
=====================================

[![Build Status](https://travis-ci.org/MiningEnthusiastCoin-Project/MiningEnthusiastCoin.svg?branch=develop)](https://travis-ci.org/MiningEnthusiastCoin-Project/MiningEnthusiastCoin)

(Japanese HP)https://miningenthusiastcoin.com/
(English HP)https://miningenthusiastcoin.com/en/

What is MiningEnthusiastCoin?
----------------

MiningEnthusiastCoin is an experimental digital currency that enables instant payments to
anyone, anywhere in the world. MiningEnthusiastCoin uses peer-to-peer technology to operate
with no central authority: managing transactions and issuing money are carried
out collectively by the network. Litecoin Core is the name of open source
software which enables the use of this currency.

For more information, as well as an immediately useable, binary version of
the MiningEnthusiastCoin Core software, see [https://miningenthusiastcoin.com](https://miningenthusiastcoin.com).

License
-------

MiningEnthusiastCoin Core is released under the terms of the MIT license. See [COPYING](COPYING) for more
information or see https://opensource.org/licenses/MIT.

Quickstart
----------
### Build on Ubuntu

    This is a quick start script for compiling MiningEnthusiastCoin on Ubuntu

    sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils git cmake libboost-all-dev
    sudo apt-get install software-properties-common
    sudo add-apt-repository ppa:bitcoin/bitcoin
    sudo apt-get update
    sudo apt-get install libdb4.8-dev libdb4.8++-dev

    # If you want to build the Qt GUI:
    sudo apt-get install libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libprotobuf-dev protobuf-compiler

    git clone https://github.com/MiningEnthusiastCoin-Project/MiningEnthusiastCoin
    cd MiningEnthusiastCoin

    # Note autogen will prompt to install some more dependencies if needed
    ./autogen.sh
    ./configure 
    make -j2

### Build on OSX

The commands in this guide should be executed in a Terminal application.
The built-in one is located in `/Applications/Utilities/Terminal.app`.

#### Preparation

Install the OS X command line tools:

`xcode-select --install`

When the popup appears, click `Install`.

Then install [Homebrew](https://brew.sh).

#### Dependencies

    brew install cmake automake berkeley-db4 libtool boost --c++11 --without-single --without-static miniupnpc openssl pkg-config protobuf qt5 libevent imagemagick --with-librsvg

NOTE: Building with Qt4 is still supported, however, could result in a broken UI. Building with Qt5 is recommended.

#### Build MiningEnthusiastCoin Core

1. Clone the MiningEnthusiastCoin source code and cd into `MiningEnthusiastCoin`

        git clone --recursive https://github.com/MiningEnthusiastCoin-Project/MiningEnthusiastCoin
        cd MiningEnthusiastCoin

2.  Build MiningEnthusiastCoin Core:

    Configure and build the MiningEnthusiastCoin binaries as well as the GUI (if Qt is found).

    You can disable the GUI build by passing `--without-gui` to configure.

        ./autogen.sh
        ./configure
        make

3.  It is recommended to build and run the unit tests:

        make check

### Run

Then you can either run the command-line daemon using `src/miningenthusiastcoind` and `src/miningenthusiastcoin-cli`, or you can run the Qt GUI using `src/qt/miningenthusiastcoin-qt`

Development Process
-------------------

The `master-0.x` branch is regularly built and tested, but is not guaranteed to be
completely stable. [Tags](https://github.com/MiningEnthusiastCoin-Project/MiningEnthusiastCoin/tags) are created
regularly to indicate new official, stable release versions of Litecoin Core.

The contribution workflow is described in [CONTRIBUTING.md](CONTRIBUTING.md).

Testing
-------

Testing and code review is the bottleneck for development; we get more pull
requests than we can review and test on short notice. Please be patient and help out by testing
other people's pull requests, and remember this is a security-critical project where any mistake might cost people
lots of money.

### Automated Testing

Developers are strongly encouraged to write [unit tests](src/test/README.md) for new code, and to
submit new unit tests for old code. Unit tests can be compiled and run
(assuming they weren't disabled in configure) with: `make check`. Further details on running
and extending unit tests can be found in [/src/test/README.md](/src/test/README.md).

There are also [regression and integration tests](/test), written
in Python, that are run automatically on the build server.
These tests can be run (if the [test dependencies](/test) are installed) with: `test/functional/test_runner.py`

The Travis CI system makes sure that every pull request is built for Windows, Linux, and OS X, and that unit/sanity tests are run automatically.

### Manual Quality Assurance (QA) Testing

Changes should be tested by somebody other than the developer who wrote the
code. This is especially important for large or high-risk changes. It is useful
to add a test plan to the pull request description if testing the changes is
not straightforward.

Translations
------------

We only accept translation fixes that are submitted through [Bitcoin Core's Transifex page](https://www.transifex.com/projects/p/bitcoin/).
Translations are converted to Litecoin periodically.

Translations are periodically pulled from Transifex and merged into the git repository. See the
[translation process](doc/translation_process.md) for details on how this works.

**Important**: We do not accept translation changes as GitHub pull requests because the next
pull from Transifex would automatically overwrite them again.
