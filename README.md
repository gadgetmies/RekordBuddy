# RekordBuddy
The future-proof music collection manager, built by DJs for DJs.

This initial code dump will most likely not build easily or at all. That's normal. Still working on converting everything over and fixing things so that it does.

# Build

**NOTICE: This is a work in progress and here just for notes**

```
git clone git@github.com:gadgetmies/RekordBuddy.git

brew install qt@5
brew install taglib

# TODO: is this really necessary to get the headers included with #include <tag/...>?
ln -s /usr/lib/include/taglib /usr/lib/include/tag

mkdir build
cd build
cmake -D NXA_TAGLIB_DIR=/usr/local/Cellar/taglib/1.12/lib -D NXA_QT_DIR=/usr/local/Cellar/qt@5/5.15.3 ../
make
```

## Issues:

```
RekordBuddy/build/rkb_build_defines.cmake:4 (include):
  include could not find requested file:

    getversions
```
