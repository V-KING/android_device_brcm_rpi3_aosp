#This is AOSP tree for Raspberry Pi 3
*I'm planning to add emulated storage, automated img creation for easy install, more useful apps, optimized kernel (prebuilt)
and other stuff to make the Android experience as smooth as possible!*

Thanks to:
- peyo-hd
- ikalkov
- kconger
- udK
and everyone else who have been working on the original tree!
(https://github.com/Android-RPi3/android_device_brcm_rpi3)


Read it first : https://github.com/peyo-hd/local_manifests/tree/npv

# Building the kernel
 $ apt-get install gcc-arm-linux-gnueabihf python-mako
 $ cd kernel/rpi
 $ ARCH=arm scripts/kconfig/merge_config.sh arch/arm/configs/bcm2709_defconfig android/configs/android-base.cfg android/configs/android-recommended.cfg
 $ ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- make zImage
 $ ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- make dtbs

# Patch
  Run: patch -p1 < device/brcm/rpi3/Patch.diff
  OR
  https://github.com/peyo-hd/device_brcm_rpi2/wiki#avoid-logcat-flood
 
# Building the Android
 $ source build/envsetup.sh
 $ lunch rpi3-eng
 $ make

# Preparing the sdcard
  The image script is coming soon!

Further steps coming soon!

Community forum : https://groups.google.com/forum/#!forum/android-rpi
