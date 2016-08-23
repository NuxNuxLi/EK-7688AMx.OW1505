# EK-7688AMx.OW1505


## How to build the firmware for EK-7688AMx?

0. [Install prerequisite packages](http://labs.mediatek.com/fileMedia/download/87c801b5-d1e6-4227-9a29-b5421f2955ac#page=97&zoom=auto,70,239)

0. Update the feed information for all packages and install all packages
   ```
     ./scripts/feeds update -a
     ./scripts/feeds install -a
   ```	 

0. Choose default config -- `make defconfig`

0. Select options for EK-7688AMx -- `cp EK-7688AMx.OW1505 .config`

0. Make a new firmware -- `make V=s`

0. Get a new firmware under bin/ramips/xxx-sysupgrade.bin

