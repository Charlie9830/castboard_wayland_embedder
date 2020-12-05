Castboard Flutter Wayland Embedder

Build Setup Instructions
------------------------

### Building the Embedder
* Set the Flutter Engine SHA code variable inside `CMakeLists.txt` to match the SHA of whichever revision of the Flutter SDK you are using. You can find this out by visiting the offical Flutter Github repository for the current version/commit you are using and navigating to `/bin/internal/engine.version`.
* Install the following packages (Tested on Ubuntu Server 20.04 Focal):
    - `weston`
    - `libwayland-dev`
    - `cmake`
    - `ninja-build`
    - `clang`
    - `pkg-config`
    - `libgles2-mesa-dev`
* From the source root `mkdir build` and move into the directory.
* `cmake -G Ninja ../`. This should check you development environment for required packages, download the Flutter engine artifacts and unpack the same in the build directory.
* `ninja` to build the embedder.

### Building the Castboard Player
* Run `sudo snap install flutter --classic`.
* Run `flutter channel master`
* Run `flutter upgrade`
* Clone the castboard player repo, cd into directory.
* Run `flutter config --enable-linux-desktop`
* Run `flutter build bundle` don't use --release flags. Doesn't seem to work currently.


### Running the Application
* Start Weston `weston`
* Once Weston is running use the Internal Weston Terminal to run `./flutter_wayland {CASTBOARD_PLAYER_PATH}/build/flutter_assets}`
