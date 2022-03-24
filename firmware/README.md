# Hacked Firmware Files

# NOTE:  Uses at your own risk

# New Procedure:  https://youtu.be/yZ9Bxln1qOU


#### x6100_ui_v100.TXOpen - TX on every frequency this radio is able to
#### x6100_ui_v100.TXOpen10w_Bat - Open TX with 10w output from the internal battery

# Install Instructions

* Format a micro SD card in (FAT32 format).
* Put the desired file named "x6100_ui_v100" on the SD card.
* Boot the X6100 without the SD card.
* Connect the raspberry pi to the X6100 with the USB-C cable connected to the "DEV" port.
* Boot up the Raspberry Pi and open a terminal screen.
* Type the following commands:

  ```
  sudo apt install screen (confirm with yes and it will install)
  stty -F /dev/ttyACM0 cs8 -parenb
  screen /dev/ttyACM0 115200
  ```

* Now you will be presented with the terminal screen of the X6100 (this may take a
  while, press a key if needed to initiate the connection).
* Log in with username "root" and password "123".
* Insert the SD card into the X6100.

  When you insert the card into the SD slot, the screen will indicate that a card is inserted.

  It also gives some information about the card being read-only.

* Type the following commands:
```
  CD
  mkdir test
  mount /dev/mmcblk0p1 test
  cd /usr/app_qt
  ## make a backup
  cp x6100_ui_v100 x6100_ui_v100.original
  killall x6100_ui_v100
  cp /root/test/x6100_ui_v100 /usr/app_qt
  chmod 775 x6100_ui_v100
  /etc/init.d/S99userappstart start
```
* Power Off the radio
* Remove the SD card and disconnect the USB-C cable.
* Turn the X6100 back on and have fun... (legally)
