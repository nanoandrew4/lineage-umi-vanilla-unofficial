# lineage-umi-vanilla

This repository hosts vanilla builds of Lineage OS for umi devices. You can run Lineage by itself, or flash GApps if you wish, following the instructions in the appropriate section.

## Vanilla installation

To install vanilla Lineage, with no GApps, simply grab the [latest release](https://github.com/nanoandrew4/lineage-umi-vanilla/releases) zip on this repository alongisde the appropriate recovery file, and flash it to your phone. You'll need the ADB and fastboot command line tools installed to do this, see [this](https://www.xda-developers.com/install-adb-windows-macos-linux/) guide if you don't have them set up, and your phone plugged in to your computer. These are the steps to flash the ROM onto your phone:

1. Reboot your phone into fastboot mode (hold power and volume down until the device vibrates, then let go of the power button but hold the volume button until you see the fastboot screen)
2. From your computer run the following command `fastboot flash recovery <recovery.img>` where `recovery.img` is the recovery image file you downloaded alongisde the zip file.
3. Reboot into recovery mode with the command `fastboot reboot recovery` or holding down the power button and volume up button, and releasing the power button but holding the volume button when the phone vibrates until you enter recovery mode.
4. Once in recovery mode, tap on `Factory reset`, tap `Format data/factory reset` and confirm. Once that is done, tap on `Format system partition` and confirm. Once both these steps have been performed, tap the back arrow on the top left corner and tap `Apply update`, and subsequently tap `Apply from ADB`. From your computer run the following command: `adb sideload <downloaded-rom.zip>` where `downloaded-rom` is the zip file you downloaded from this repository. It will get stuck at 47%, at which point you should see some information on your phone screen as the ROM is flashed on to your phone, this process may take several minutes.
5. Reboot and enjoy! (unless you want GApps)

## GApps installation

To install Lineage with GApps, you first have to follow the vanilla installation steps, excluding the last reboot. For GApps to be properly installed, they have to be flashed right after the ROM is flashed, and without booting up the phone in between. There are many GApps providers, such as [OpenGapps](https://opengapps.org/), [NikGApps](https://nikgapps.com/) and MindTheGapps, which the official LineageOS website [links](https://wiki.lineageos.org/gapps) to. 

Currently, most of the flavors of GApps will run into issues due to being too big, and not enough space being allocated to system partitions on the vanilla image (otherwise you'd have less space for all your stuff). However, the smallest package available from any of these providers, which usually only includes the core services and Play Store, is small enough to be installed, so I recommend you go with that package. Any of the other Google Apps you want from the other flavors of GApps can be downloaded through the Play Store anyways, and you can pick and choose what you want, so you are not missing anything by going with the smallest possible package.

Once you have completed the vanilla installation and the ROM has just been flashed, tap `Apply update` and `Apply from ADB` once again. Run the command `adb sideload <gapps.zip>` where `gapps.zip` is the zip file you downloaded from one of the aforementioned GApps providers. You will likely get a signature verification error, as they have not signed their package with my keys (because its their package, not mine), but you can just tap yes and the GApps will be flashed to the device. If everything finishes without an error, you can reboot and enjoy, if you ran into any errors with the gapps zip file you chose, you can always try another one after repeating step 4 in the vanilla installation section.

