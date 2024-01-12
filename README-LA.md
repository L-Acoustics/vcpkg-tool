L-Acoustics vcpkg fork
======================


Key differences
---------------

This version of VCPKG is patched to:
  * Always download tools (like cmake) from the internet, instead of relying on local tools
  * Use our custom L-Acoustics triplet files by default


Build
-----

Update VERSION.txt
Use Ninja, same on all platforms :)

```
mkdir _build && cd _build
cmake .. -G Ninja -D CMAKE_BUILD_TYPE=Release <platform specific options>
cmake --build
```

Note: on macOS, add `-D CMAKE_OSX_ARCHITECTURES="x86_64;arm64"` to generate a universal binary

Codesign/notarize accordingly


Release
-------

 * Push tag on github
 * Deploy `vcpkg.exe`, `vcpkg-macos`, `vcpkg-glibc` to GitHub
 * Update our private `vcpkg` repo fork to download those prebuilt versions

 