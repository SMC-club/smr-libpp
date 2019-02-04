# smc-libpp

SMC-compatible serialization and transaction signing sample/demo

## Introduction

Demo application that uses the 
([smcd](https://github.com/Muvon/smcd)).
C++ library to create, sign, and serialize
[SMC](https://smc.one) transactions before
submission to the SMC Consensus Ledger
([smcd](https://github.com/Muvon/smcd)).
This demonstrates much of the functionality of the
[`sign`](https://ripple.com/build/rippled-apis/#sign)
RPC function without the overhead of a JSON library,
network delays, needing to trust a 3rd party's smcd,
nor needing to run your own smcd.

## Table of contents

* [Dependencies](#dependencies)
  * [SMCD submodule](#smcd-submodule)
  * [Other dependencies](#other-dependencies)
* [Demo](#demo)
  * [Additional dependencies](#additional-dependencies)
  * [Build and run](#build-and-run)

## Dependencies

### SMCD submodule

smc-libpp includes a git submodule to include the smcd
source code, which is not cloned by default. To get the
smcd source, either clone this repository using
```
$ git clone --recursive <location>
```
or after cloning, run the following commands
```
$ git submodule init
$ git submodule update
```

Note: even though the entire smcd source tree is included
in the submodule, only a subset of it is used by the library.

### Other dependencies

* C++14 or greater
* [Boost](http://www.boost.org/)
* [OpenSSL](https://www.openssl.org/)

## Demo

Code examples are provided in `src/test/smc-libpp_demo.cpp`
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
$ cd ${YOUR_SMC_LIBPP_DIRECTORY}
$ mkdir -p build/debug
$ cd build/debug
$ cmake ../.. -DCMAKE_BUILD_TYPE=Debug
$ cmake --build .
$ ./smclibppdemo
```

For 64-bit Windows, open a MSBuild Command Prompt for Visual Studio
and run the following commands:

```
> cd %YOUR_SMC_LIBPP_DIRECTORY%
> mkdir build
> cd build
> cmake -G"Visual Studio 15 2017 Win64" ..
> cmake --build .
> .\Debug\smclibppdemo.exe
```

32-bit Windows builds are not supported.
