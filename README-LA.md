L-Acoustics vcpkg fork
======================


Key differences
---------------

This version of VCPKG is patched to:
  * Always download tools (like cmake) from the internet, instead of relying on local tools
  * Use our custom L-Acoustics triplet files by default


Compilers
---------

Currently tested with:

 * Visual studio 2022 (2019 proven not to work)
 * Xcode 15.1
 * GCC 8.3 from Debian 10 (Buster)


Build
-----

Use Ninja, same on all platforms :)

```
mkdir _build && cd _build
cmake .. -G Ninja -D CMAKE_BUILD_TYPE=Release -D VCPKG_BASE_VERSION=<versionString> <platform specific options>
cmake --build
```

Note: on macOS, add `-D CMAKE_OSX_ARCHITECTURES="x86_64;arm64"` to generate a universal binary, and `-D CMAKE_OSX_DEPLOYMENT_TARGET=10.13` (or equivalent to manage the target macOS version)

Note: on Windows, you need to do this from a "Developer Command Prompt for VS XXX" for environment variables
pointing to your VS install to be setup correctly. Otherwise cmake will not find the right compiler.

Codesign/notarize accordingly


Release
-------

 * Push tag on github
 * Deploy `vcpkg.exe`, `vcpkg-macos`, `vcpkg-glibc` to GitHub
 * Update our private `vcpkg` repo fork to download those prebuilt versions
