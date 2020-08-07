
# How to turn Wii Games from Wii U eShop into ISOs on Linux
This may not work on all Wii games, I have only tested "Super Mario Galaxy 2"
This is currently more of a "How to get .nfs files from Wii U Wii VC"

1. You will need a Wii U console with a way of launching homebrew.
1. For this you will also need an SD Card, other SDs work as well eg. *SDHC* (I will be referring to it as an SD Card)
1. Download both [OTP2SD](https://github.com/dimok789/otp2sd_dumper/releases/download/v1.0/otp2sd.zip) and [SEEPROM2SD](https://github.com/dimok789/seeprom2sd/releases/download/v1.0/seeprom2sd.zip) (source code for OTP2SD [here](https://github.com/dimok789/otp2sd_dumper) and SEEPROM2SD [here](https://github.com/dimok789/seeprom2sd))
1. Create a folder called wiiu on the root of your SD Card, Inside of the wiiu folder create another folder called apps inside the wiiu folder.
1. Inside the folder called apps that you just created, Create one folder called OTP2SD and another called SEEPROM2SD.
1. Unzip OTP2SD and SEEPROM2SD, Then copy/move over the .elf from OTP2SD to the folder in apps called OTP2SD and do the same for SEEPROM2SD but copy/move it to the SEEPROM2SD folder.
1. Then unmount your SD Card and put it in your Wii U.
1. Plug a storage device into your Wii U's USB slot and format it if you haven't already. 
1. Then go to System Settings.
1. Go to Data Management and copy the Wii Game of choice to your storage device.
1. Once it has finished run OTP2SD and SEEPROM2SD.
1. Turn off your Wii U then take out the SD card and put it in your computer.
1. Copy otp.bin and seeprom.bin to your computer
1. Take out the storage device that you put in earlier.
1. Put it in your computer
1. Open a terminal and run `git clone https://github.com/koolkdev/wfslib.git` then compile it (see below)
1. To install the dependencies run the following command.
```
sudo apt install git g++ make pkg-config libfuse-dev libboost-dev libboost-system-dev libboost-filesystem-dev libboost-program-options-dev libcrypto++-dev
```
18. Then run `cd wfslib`.
1. Run  `make`  and then `cd wfs-fuse`
1. And also run `mkdir /tmp/wiivc/`
1. Copy over otp.bin and seeprom.bin to wfs-fuse.
1. Open Disks and determine your storage device's device file eg. */dev/sdb*
1. Then run the following command whilst replacing "PUT_YOUR_DEVICE_HERE" with the name you just determined. 
  * `sudo ./wfs-fuse/wfs-fuse /dev/PUT_YOUR_DEVICE_HERE /tmp/wiivc --otp ./wfs-fuse/otp.bin --seeprom ./wfs-fuse/seeprom.bin`
24. Also run `cd /tmp/wiivc`
1. Run `cp -r usr/ ~/` to copy over your game. 
1. The .nfs files will be stored in a "content" folder in the "user" directory.
1. This is currently incomplete, but if you want to continue you can use [nfs2iso2nfs](https://github.com/sabykos/nfs2iso2nfs) (written in C#).
