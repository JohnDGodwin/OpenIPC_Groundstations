<h1>First Boot Instructions</h1>

* 1 -- Flash the img file -- I highly recommend using internal memory, either emmc or nvme. SD cards are slow.
* 2 -- On first boot you'll be dropped to the homescreen. Press `CTRL-ALT-F1` to enter into a terminal.
* 3 -- Run the `./wfb_keygen` and transfer transfer the keys. Run `sudo cp gs.key /etc` to transfer your gs.key to the groundstation's /etc directory. To transfer the drone.key file, connect your camera to your home network, then run `scp drone.key root@x.x.x.x:/etc` and replace x.x.x.x with your camera's local ip address.

<h1>Notes</h1>

* Currently playback start/stop is controlled via a push button installed to the gpio header. On the Orange Pi 5 Plus it is connected to pin 5 and ground. On the Radxa Zero 3W it is connected to pins 15 and 3.3v. In both cases, the pins are right next to each other.
* The stock system will force your display to 1920x1080 mode. If you wish to change this behavior, i.e. display 1280x720, you can do so in the dvr.sh script found at `/home/ubuntu/scripts/setdisplay.sh`
* DVR can be accessed at `/home/ubuntu/Videos` on the Orange Pi 5 Plus and at `/media/SD` on the Radxa Zero 3W. You can also access DVR via a media server if your system is on your home network at `x.x.x.x:8080` in a browser. (replace x.x.x.x with the groundstation's local ip address.)

<h1>Special for the Orange Pi 5 Plus</h1>

* On the Orange Pi 5 Plus, there are two DVR scripts. The default will simply increment the file name. The second script uses a timestamp naming scheme and is for use if you install a RTC. Just change the name of the dvr.sh script to something like dvr.sh.old, then rename the dvr_rtc.sh to dvr.sh.

<h1>Special for the Radxa Zero 3W</h1>

* DVR is recorded to the SD card on the Zero 3W. Insert a partitioned SD card and it should auto-mount and save DVR video to it. (Because of this, the image cannot be run from an SD card.)
* The internal wifi can be used and is recommended for SSH. Instructions on connecting to your network are located at [zero3w_wifi_connection_instructions.](https://github.com/JohnDGodwin/OpenIPC_Groundstations/blob/main/zero3w_wifi_connection_instructions.md)
