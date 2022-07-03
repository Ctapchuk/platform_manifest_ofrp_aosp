## OrangeFox Recovery repo manifest

## Maintaining Authorship ##
Maintaining authorship is a very important aspect of working with Open Source code. If you wish to submit a patch/fix
from anywhere else (another ROM, project, etc.), it is imperative that you maintain the ownership of the person whose
work you are seeking to include. Doing so will ensure that credit is given where it is deserved, and
the [principles of open source](http://opensource.org/docs/osd)
are upheld. Your contribution to the project will still be recognized as you will forever be listed as the committer.

Read build instruction [here](https://wiki.orangefox.tech/en/dev/building)

## Syncing repo ##
---------------

To get started with AOSP sources to build OFRP, you'll need to get familiar
with [Git and Repo](https://source.android.com/source/using-repo.html).

To initialize your local repository using the AOSP trees to build OFRP, use a command like this:

    repo init -u https://github.com/Ctapchuk/platform_manifest_ofrp_aosp.git -b ofrp-12.1_dev

To initialize a shallow clone, which will save even more space, use a command like this:

    repo init --depth=1 -u https://github.com/Ctapchuk/platform_manifest_ofrp_aosp.git -b ofrp-12.1_dev

Then to sync up:

    repo sync

Then to setup the build:

     cd <source-dir>; export ALLOW_MISSING_DEPENDENCIES=true; . build/envsetup.sh; lunch twrp_<device>-eng

The build target is dependent on the device, and should reflect the location of stock recovery on the device. Issue the build command that applies to your device:
- Recovery partition: `mka recoveryimage`
- Boot image ramdisk: `mka bootimage`
- Vendor_boot image ramdisk: `mka vendorbootimage`
