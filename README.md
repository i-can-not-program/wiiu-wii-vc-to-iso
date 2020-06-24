
# How to turn Wii Games from Wii U eShop into ISOs
1. Plug a storage device into your Wii U's usb slot and format it if you haven't already. 
1. Then go to System Settings.
1. Go to Data Management and copy the Wii Game of choice to your storage device.
1. Go to the Homebrew Launcher and get OTP2SD and SEEPROM2SD in your preferred way.
1. You will need an SD Card, other SDs work as well.
1. Run OTP2SD and SEEPROM2SD.
1. Turn off your Wii U then take out the SD card and put it in your computer.
1. Copy otp.bin and seeprom.bin to your computer
1. Take out the storage device that you put in earlier.
1. Put it in your computer
1. Run `git clone https://github.com/koolkdev/wfslib.git` then compile it (see below)
1. Open a terminal and go into it.
1. Run `make` then `cd wfs-fuse`
1. Copy over otp.bin and seeprom.bin to wfs-fuse.
1. Please open Disks and determine your storage device's device file eg. */dev/sdb*
1. Then run the following command whilst replacing "PUT_YOUR_DEVICE_HERE" with the name you just determined. 
  * `sudo ./wfs-fuse/wfs-fuse /dev/PUT_YOUR_DEVICE_HERE /tmp/wii --otp ./wfs-fuse/otp.bin --seeprom ./wfs-fuse/seeprom.bin`
  
