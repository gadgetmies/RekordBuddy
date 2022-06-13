# RekordBuddy
The future-proof music collection manager, built by DJs for DJs.

This initial code dump will most likely not build easily or at all. That's normal. Still working on converting everything over and fixing things so that it does.

# Build

**NOTICE: This is a work in progress and here just for notes**

```
git clone git@github.com:taglib/taglib.git
cd taglib

# Build taglib as framework and install it as per: https://github.com/taglib/taglib/blob/master/INSTALL.md#mac-os-x i.e.:
# mkdir build; cd build
# cmake .. -DCMAKE_BUILD_TYPE=Release \
#  -DBUILD_TESTING=OFF \
#  -DBUILD_FRAMEWORK=ON \
#  -DCMAKE_OSX_DEPLOYMENT_TARGET=10.10 \
#  -DCMAKE_OSX_ARCHITECTURES="arm64;x86_64"
# make

# To install:
# sudo make install

cd ..
git clone git@github.com:gadgetmies/RekordBuddy.git

brew install qt@5
brew install coreutils

mkdir build
cd build
cmake -D NXA_TAGLIB_DIR=`realpath ../../taglib/build/taglib` -D NXA_QT_DIR=/usr/local/Cellar/qt@5/5.15.3 ..

# Patch the rkb_build_defines.cmake file in build folder by replacing '../../' in the include with '../'

make # `Use make VERBOSE=1` to see the compile commands

# Run the application
open ./UI/Rekord\ Buddy.app

```

## Issues:

* The app will build ok, but will not run on macOS versions later than 11.
