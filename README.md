# autorun-ccminer-termux
Autorun ccminer (mining verus coin) on termux app!
1. Download termux app from Fdroid
copy link below to your browser
  ```cpp
  https://f-droid.org/repo/com.termux_1000.apk
  ```
2. Download termux boot from Fdroid
copy link below to your browser
  ```cpp
  https://f-droid.org/repo/com.termux.boot_1000.apk
  ```
3. Install termux:app & termux:boot on your smartphone!
4. Update, upgrade and install packages.
  ```cpp
  pkg update && pkg upgrade -y
  pkg install libjansson wget nano -y
  ```
5. Create boot directory & setting termux properties
  ```cpp
  mkdir ~/.termux/boot
  nano ~/.termux/termux.properties
  ```
  remove ```#``` on ``` allow-external-apps 'true' ```
  ctrl+x y
  [Enter]

6. Download ccminer, config, verus bash
  ```cpp
  mkdir ~/ccminer
  wget https://raw.githubusercontent.com/Burhan7610/autorun-ccminer-termux/generic/ccminer
  wget https://raw.githubusercontent.com/Burhan7610/autorun-ccminer-termux/generic/config.json
  wget https://raw.githubusercontent.com/Burhan7610/autorun-ccminer-termux/generic/verus
  cd ~/ccminer && chmod +x ccminer verus
  cp ./verus ../../usr/bin/verus
  ```

7. Create script auto start termux and running verus mining.
  ```cpp
  nano ~/.termux/boot/start-verus
  ```
  copas code script here
  ```cpp
  am startservice --user 0 -n com.termux/com.termux.app.RunCommandService \
  -a com.termux.RUN_COMMAND \
  --es com.termux.RUN_COMMAND_PATH '/data/data/com.termux/files/usr/bin/verus' \
  --esa com.termux.RUN_COMMAND_ARGUMENTS '-n,5' \
  --es com.termux.RUN_COMMAND_WORKDIR '/data/data/com.termux/files/home' \
  --ez com.termux.RUN_COMMAND_BACKGROUND 'false' \
  --es com.termux.RUN_COMMAND_SESSION_ACTION '1'
  ```
  ctrl+x y
  [Enter]
  
8. Start the Termux:Boot app once by clicking on its launcher icon.
9. reboot your smartphone
DONE!
