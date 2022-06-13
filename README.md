# RekordBuddy
The future-proof music collection manager, built by DJs for DJs.

This initial code dump will most likely not build easily or at all. That's normal. Still working on converting everything over and fixing things so that it does.

# Build

**NOTICE: This is a work in progress and here just for notes**

```
git clone git@github.com:gadgetmies/RekordBuddy.git

brew install qt@5
brew install taglib

mkdir build
cd build
cmake ..
make
```

## Issues:

* Build does not find headers for taglib i.e.:
`...RekordBuddy/TrackFiles/Objects/Internal/TrackFileInternal.hpp:37:10: fatal error: 'tag/tfile.h' file not found`
