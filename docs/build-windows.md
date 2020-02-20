WINDOWS BUILD NOTES
====================

Some notes on how to build Addmore Core for Windows.

Most developers use cross-compilation from Ubuntu to build executables for
Windows. This is also used to build the release binaries.

Building on Windows itself is possible (for example using msys / mingw-w64),
but no one documented the steps to do this. If you are doing this, please contribute them.

Cross-compilation
-------------------

These steps can be performed on, for example, an Ubuntu VM. The depends system
will also work on other Linux distributions, however the commands for
installing the toolchain will be different.

First install the toolchains:

    sudo apt-get install g++-mingw-w64-i686 mingw-w64-i686-dev g++-mingw-w64-x86-64 mingw-w64-x86-64-dev

To build executables for Windows 32-bit:

    cd depends
    make HOST=i686-w64-mingw32 -j4
    cd ..
    ./configure --prefix=`pwd`/depends/i686-w64-mingw32
    make

To build executables for Windows 64-bit:

    cd depends
    make HOST=x86_64-w64-mingw32 -j4
    cd ..
    ./configure --prefix=`pwd`/depends/x86_64-w64-mingw32
    make

On Ubuntu 15.10 and above, if your build fails because the cross-compiler does not seem to support C++11 threads (you get errors such as "httpserver.cpp:69:10: error: ‘mutex’ in namespace ‘std’ does not name a type) you may have to select the posix versions of gcc-mingw-w64 and g++-mingw-w64:

    sudo update-alternatives --config x86_64-w64-mingw32-gcc
    sudo update-alternatives --config x86_64-w64-mingw32-g++

And select the posix version of the compiler.

For further documentation on the depends system see [README.md](../depends/README.md) in the depends directory.

