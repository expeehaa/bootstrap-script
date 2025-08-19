# Crystal Bootstrap Automation

This script automates bootstrapping crystal from source code, compiling every
intermediate compiler version to reach the latest version.

## Dependencies

- Essential build tools i.e. `build-essential`/`base-devel`
- curl
- git
- patch
- which
- awk
- find
- tar
- xz
- autoconf
- libtool
- cmake
- zlib dev package
- libyaml dev package
- libunwind dev package
- libgc (bdwgc) dev package

Additionally, the script compiles some dependencies that are unlikely to be available in a modern system.
- Ruby 1.9.3
- Python 2.7
- LLVM 3.x
- pcre
- pcl
- libevent 2.1.10
- openssl 1.0.2q

Some dependencies do not compile with the most recent versions of GCC.
Alternative executables for the C and C++ compiler for the affected older dependencies can be defined in the environment variables `BOOTSTRAP_OLD_CC` and `BOOTSTRAP_OLD_CXX`, respectively.
They will overwrite the environment variables `CC` and `CXX`.
Compilation using GCC 7 or 10 has been confirmed to succeed.

## openSUSE Tumbleweed

The required dependencies can be installed with the following command.
```
zypper install curl git patch which awk find tar xz autoconf cmake gcc gcc-c++ gcc7 gcc7-c++ libyaml-devel zlib-devel libunwind-devel gc-devel
```

Then clone this repository and change to its root directory.

(Early) Crystal attempts to load the library `librt.so`, but Tumbleweed provides it with so-version `1` (at the time of writing), leading to an error.
This can be fixed by creating the symlink
```
mkdir -p buildroot/lib
ln -s /usr/lib64/librt.so.1 buildroot/lib/librt.so
```

Download all required source files and run the `bootstrap` script with some environment variables to use GCC 7.
```
./download
BOOTSTRAP_OLD_CC=gcc-7 BOOTSTRAP_OLD_CXX=g++-7 ./bootstrap
```
