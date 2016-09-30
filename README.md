# EK-7688AMx.OW1505


## How to build the firmware for EK-7688AMx?

0. [Build the firmware](http://labs.mediatek.com/fileMedia/download/87c801b5-d1e6-4227-9a29-b5421f2955ac#page=97&zoom=auto,70,239)

## How to setup wireless mode from AP to AP-Client? 

0. Replace your target's lib/netifd/wireless/ralink.sh with ralink.sh

0. Rewrite /etc/config/wireless -- `vi /etc/config/wireless`
   
   ```
   ---option ssid UplinkAp
   +++option ssid 'RootAP_SSID'
   ---option key SecretKey
   +++option key 'RootAP_password'
   ---option encryption 'psk'
   +++option encryption 'psk2' (ps: RootAP's encryption)
   ---option disabled '1'
   +++option disabled '0' (ps: enabled station mode)
   +++option apcli '1' (ps: enabled ap-client mode)
   ```
   or 
   ```
   uci set wireless.sta.ssid="RootAP_SSID"
   uci set wireless.sta.key="RootAP_password"
   uci set wireless.sta.encryption="psk2"
   uci set wireless.sta.disabled="0"
   uci set wireless.sta.apcli="1"
   uci commit
   ```


0. Restart network -- `/etc/init.d/network restart` or `wifi`

## How to setup wireless mode to AP?

0. Replace your target's lib/netifd/wireless/ralink.sh with ralink.sh

0. Rewrite /etc/config/wireless --
   `uci set wireless.sta.disabled="1"`
   `uci commit`

0. Restart network -- `wifi`

## How to setup wireless mode to STA?

0. Replace your target's lib/netifd/wireless/ralink.sh with ralink.sh

0. Rewrite /etc/config/wireless --
   `uci set wireless.sta.disabled="0"`
   `uci set wireless.sta.apcli="0"`
   `uci commit`

0. Restart network -- `wifi`

## How to use elian(MTK smart connection)?

0. Install elian apk

0. Download wifi driver with elian in [linkit-smart-EK-7688AMx-feed](https://github.com/NuxNuxLi/linkit-smart-EK-7688AMx-feed)

0. Start elian `iwpriv apcli0 elian start`

0. Run elain apk, input your password and press Send V4

0. Get elian result `iwpriv apcli0 elian result`

0. Stop elian `iwpriv apcli0 elian stop`

