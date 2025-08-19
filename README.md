# Crystal Bootstrap Automation

This script automates bootstrapping crystal from source code, compiling every
intermediate compiler version to reach the latest version.

## Dependencies

- Essential build tools i.e. `build-essential`/`base-devel`
- curl
- git
- patch
- which
- tar
- xz
- autoconf
- libtool
- cmake
- pcre dev package
- zlib dev package
- libyaml dev package
- libunwind dev package
- libgc (bdwgc) dev package

Additionally, the script compiles some dependencies that are unlikely to be available in a modern system.
- Ruby 1.9.3
- Python 2.7
- LLVM 3.x
- pcl
- libevent 2.1.10
- openssl 1.0.2q

Some dependencies do not compile with the most recent versions of GCC.
Alternative executables for the C and C++ compiler for the affected older dependencies can be defined in the environment variables `BOOTSTRAP_OLD_CC` and `BOOTSTRAP_OLD_CXX`, respectively.
They will overwrite the environment variables `CC` and `CXX`.
Compilation using GCC 7 or 10 has been confirmed to succeed.
