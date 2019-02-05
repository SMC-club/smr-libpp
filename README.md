# smr-libpp

SMR-compatible serialization and transaction signing sample/demo

## Introduction

Demo application that uses the 
([smrd](https://github.com/Muvon/smrd)).
C++ library to create, sign, and serialize
[SMR](https://smr.one) transactions before
submission to the SMR Consensus Ledger
([smrd](https://github.com/Muvon/smrd)).
This demonstrates much of the functionality of the
[`sign`](https://ripple.com/build/rippled-apis/#sign)
RPC function without the overhead of a JSON library,
network delays, needing to trust a 3rd party's smrd,
nor needing to run your own smrd.

## Table of contents

* [Dependencies](#dependencies)
  * [SMRD submodule](#smrd-submodule)
  * [Other dependencies](#other-dependencies)
* [Demo](#demo)
  * [Additional dependencies](#additional-dependencies)
  * [Build and run](#build-and-run)

## Dependencies

### SMRD submodule

smr-libpp includes a git submodule to include the smrd
source code, which is not cloned by default. To get the
smrd source, either clone this repository using
```
$ git clone --recursive <location>
```
or after cloning, run the following commands
```
$ git submodule init
$ git submodule update
```

Note: even though the entire smrd source tree is included
in the submodule, only a subset of it is used by the library.

### Other dependencies

* C++14 or greater
* [Boost](http://www.boost.org/)
* [OpenSSL](https://www.openssl.org/)

## Demo

Code examples are provided in `src/test/smr-libpp_demo.cpp`
to demonstrate how to create, sign, and verify the signature of a
transaction. Building and running this demo is an optional step to
verify that dependencies are installed and available as expected.

### Additional dependencies

In addition to the Usage [dependencies](#dependencies), building
the demo requires

* [cmake](https://cmake.org)

### Build and run

For linux and other unix-like OSes, run the following commands:

```
$ cd ${YOUR_SMR_LIBPP_DIRECTORY}
$ mkdir -p build/debug
$ cd build/debug
$ cmake ../.. -DCMAKE_BUILD_TYPE=Debug
$ cmake --build .
$ ./smrlibppdemo
```

For 64-bit Windows, open a MSBuild Command Prompt for Visual Studio
and run the following commands:

```
> cd %YOUR_SMR_LIBPP_DIRECTORY%
> mkdir build
> cd build
> cmake -G"Visual Studio 15 2017 Win64" ..
> cmake --build .
> .\Debug\smrlibppdemo.exe
```

32-bit Windows builds are not supported.
