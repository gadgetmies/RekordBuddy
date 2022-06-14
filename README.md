# RekordBuddy
The future-proof music collection manager, built by DJs for DJs.

This initial code dump will most likely not build easily or at all. That's normal. Still working on converting everything over and fixing things so that it does.

# Build

**NOTICE: This is a work in progress and here just for notes**

## Using cmake
```
cd ~/Documents
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

make # Use `make VERBOSE=1` to see the compile commands

# Run the application
open ./UI/Rekord\ Buddy.app

```

### Issues:

* The app will build ok, but will not run on macOS versions later than 11.

### Using bin/build.py

You need to have XCode installed in order to build the application with the script.

```
cd ~/Documents
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

python bin/build.py --taglibpath `realpath ../../taglib/build/taglib` --qtpath /usr/local/Cellar/qt@5/5.15.3
make # Use `make VERBOSE=1` to see the compile commands

# Run the application
open ./UI/Rekord\ Buddy.app

```

### Issues:
* Unused variable breaks the build as -Werror is set. To get past this, build with `make VERBOSE=1`, copy the compiler command, remove `-Werror` argument, run the compiler command and continue the build by running `make`.
```
RekordBuddy/TrackFiles/Objects/Internal/MPEGTrackFileInternal.hpp:55:9: warning: variable 'id3_version' set but not used [-Wunused-but-set-variable]
    int id3_version;
        ^

RekordBuddy/Collections/Common/Objects/Markers/MarkerValidation.cpp:566:13: error: variable 'gridMarkersHaveBeenRemoved' set but not used [-Werror,-Wunused-but-set-variable]
    boolean gridMarkersHaveBeenRemoved = false;
            ^

RekordBuddy/Collections/Common/Objects/Markers/MarkerOffset.cpp:170:9: error: variable 'vbr_quality' set but not used [-Werror,-Wunused-but-set-variable]
    int vbr_quality = -1;
        ^

RekordBuddy/Collections/PCDJ/Include/PCDJCollection/Collection.hpp:100:19: error: variable 'lastTrackID' set but not used [-Werror,-Wunused-but-set-variable]
            count lastTrackID = 0;
                  ^
```

