TWRP Device tree for the Samsung Galaxy SDM439 (android 10 , 11 and android 12)
=================================================

| Basic                   | Spec Sheet                                                                                                                     |
| -----------------------:|:------------------------------------------------------------------------------------------------------------------------------ |
| CPU                     | Octa-core                                                                   |
| Chipset                 | Qualcomm SDM439 Snapdragon 439                                                         |
| GPU                     | Adreno 505                                                                         |
| Memory                  | 2/3 GB RAM                                                           |
| Shipped Android Version | 10.0                                                         |
| Storage                 | 16/32 GB                                     |
| Battery                 | Non-removable Li-Po 4000 mAh battery                        |
| Display                 | 1080 x 2400 pixels, 20:9 ratio (~393 ppi density)                                    |
| Camera (Back)(Main)     | 13 MP, f/1.8, 26mm (wide), 1/1.73", 0.8µm, PDAF, 0.8µm, PDAF                              |
| Camera (Front)          | 5 MP, f/2.0, 26mm (wide), 1/2.8", 0.8µm                                                                                      |


| Feature |Working or Not |
|----|----|
|Correct screen/recovery size|yes|
|Working Touch, screen|yes|
|Backup to internal/microSD|yes|
|Restore from internal/microSD|yes|
|reboot to system|yes|
|ADB|yes|
|update.zip sideload|yes|
|UI colors (red/blue inversions)|yes correct colours|
|Screen goes off and on|yes|
|F2FS/EXT4 Support, exFAT/NTFS where supported|yes|
|all important partitions listed in mount/backup lists|yes|
|backup/restore to/from external (USB-OTG) storage|yes |
|backup/restore to/from adb|yes|
|decrypt /data|no|
|Correct date|yes|
|MTP export|yes|
|reboot to bootloader|not supported by samsung|
|reboot to recovery|yes|
|poweroff|yes|
|battery level|yes|
|temperature|yes|
|encrypted backups|no|
|input devices via USB (USB-OTG) |yes|
|USB mass storage export|yes|
|set brightness|yes|
|vibrate|yes|
|screenshot|yes|
|Partition SD card|yes|

## How-to compile it:
# Init repo
$ repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1

# Clone m01q repo
$ git clone https://github.com/SamsungSDM439/twrp_samsung_device_439 device/samsung/m01q

# Sync
$ repo sync --no-repo-verify -c --force-sync --no-clone-bundle --no-tags --optimized-fetch --prune -j`nproc`

# Build
$ source build/envsetup.sh; export ALLOW_MISSING_DEPENDENCIES=true; lunch twrp_m01q-eng; mka recoveryimage


# Remove Samsung Securities after installing TWRP.
$ Boot TWRP; start TWRP Terminal; type setup.
# Decrypt the data partition after installing TWRP This will automatically wipe data.
$ Boot TWRP; start TWRP Terminal; type decrypt.
# Encrypt the data partition after installing TWRP This will automatically wipe data.
$ Boot TWRP; start TWRP Terminal; type encrypt.
# If you stuck in twrp after flashing any rom with encryption,
$ Boot TWRP; start TWRP Terminal; type encrypt.

Blobs version:
> Kernel base: Prebuilt Kernel.
> Ramdisk, DTB, DTBO base: M015GXXU3BVB4

