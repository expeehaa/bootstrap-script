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
- python2
- pcre dev package
- zlib dev package
- libyaml dev package
- libunwind dev package
- libgc (bdwgc) dev package

Additionally, the script compiles some dependencies that are unlikely to be available in a modern system.
- Ruby 1.9.3
- LLVM 3.x
- pcl
- libevent 2.1.10
- openssl 1.0.2q
