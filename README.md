## OrangeFox Recovery repo manifest

Read build instruction [here](https://wiki.orangefox.tech/en/dev/building)

## Syncing repo ##
---------------

To get started with AOSP sources to build OFRP, you'll need to get familiar
with [Git and Repo](https://source.android.com/source/using-repo.html).

To initialize your local repository using the AOSP trees to build OFRP, use a command like this:

    repo init -u https://github.com/Ctapchuk/platform_manifest_ofrp_aosp.git -b ofrp-11

To initialize a shallow clone, which will save even more space, use a command like this:

    repo init --depth=1 -u https://github.com/Ctapchuk/platform_manifest_ofrp_aosp.git -b ofrp-11

Then to sync up:

    repo sync --fetch-submodules

NOTE: Device makefile in the device tree and dependencies file should use the "twrp" prefix.

You can enable ccache for faster building:

     export USE_CCACHE=1; export CCACHE_EXEC=/usr/bin/ccache; ccache -M 20G

Then to build for a device with recovery partition:

     cd <source-dir>; export ALLOW_MISSING_DEPENDENCIES=true; . build/envsetup.sh; lunch twrp_<device>-eng; mka recoveryimage

Then to build for a device without recovery partition:

     cd <source-dir>; export ALLOW_MISSING_DEPENDENCIES=true; . build/envsetup.sh; lunch twrp_<device>-eng; mka bootimage
