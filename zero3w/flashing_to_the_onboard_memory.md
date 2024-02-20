<h1>How to flash the image to the onboard memory</h1>


Setup

Currently there is no bootloader file available from Radxa to use their flashrom feature. However it is still possible to flash the image to the onboard emmc. We do this by booting from the SD card and flashing the onboard memory with the `dd` command.

Download an image of your choice for the Zero 3W. [I recommend this one.](https://github.com/Joshua-Riek/ubuntu-rockchip/releases/download/v1.33/ubuntu-22.04.3-preinstalled-server-arm64-radxa-zero3.img.xz)

Flash that image to an SD card, then transfer the openipc image to a directory inside that image.

Example

		(after flashing the image to the SD card)
  		sudo mount /dev/mmcblk0p2 /mnt
		sudo cp zero3w-openipc.img /mnt/media
  		sudo umount /mnt


Boot the system from the SD card and the img we want to flash to the emmc is found in `/media`.

***

Flashing

Prepare the emmc for flashing with fdisk. Type `sudo fdisk /dev/mmcblk0` then delete any partitions that may be present.

Go to the directory you put the img file and enter the following command:

`sudo dd bs=1M if=zero3w-openipc.img of=/dev/mmcblk0 status=progress`

When that's done, power down and remove the SD card. The system should now boot from onboard emmc.
