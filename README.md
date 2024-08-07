# Disable Camera Shutter Noise
How to disable camera shutter noise on Android with no root even for Korean and Japanese phones. 
Tested on Samsung Galaxy S20 FE 5G and Samsung Galaxy Tab S6 (both Korean version) with Android 11.

Update (2024.08.14): this is still working with the newest Samsung phones, such as the Samsung Galaxy S24 Ultra with Android 14. 

## Guide

  1. Activate developer options: *Settings→ About phone → Software information —>* Click on "Build number" until the options are unlocked
  2. Activate usb debugging: *Settings → Developer options →USB debugging*
  3. Download and run ADB (Android Debug Bridge):
  
  - Windows: [https://developer.android.com/studio/releases/platform-tools](https://developer.android.com/studio/releases/platform-tools)

  - Mac:
  ```sh
  ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
  brew cask install android-platform-tools
  ```
  
  - Linux (Ubuntu / Debian-based):
  ```sh
  sudo apt-get install android-tools-adb android-tools-fastboot
  ```
    
4. Connect the phone: click on "allow USB debugging" (for Windows, go to the ADB installation folder folder, keep Shift pressed and right-clik, then open Powershell)
5. Run the following command in a terminal:
  - Windows:
  ```powershell
  .\adb shell settings put system csc_pref_camera_forced_shuttersound_key 0
  ```
  - Mac / Linux:
  ```bash
  adb shell settings put system csc_pref_camera_forced_shuttersound_key 0
  ```
6. Stop the ADB server and remove the phone safely
7. Now the shutter sound will only depend on the phones volume! Thus, we can create a _routine_ which turns the volume temporarily off if the camera app is opened. For example, in Bixby Routines (Samsung) it will look like this:

<p align="center">
  <img src="https://github.com/Juju-botu/disable-camera-shutter-noise/blob/main/Screenshot_20210624-110856_Bixby%20Routines.jpg" width=350 alt="Bixby Routines">
</p>

8. If all the steps were done correctly, no nasty camera noise will be emitted by you phone. Enjoy 😎

### Note on software updates
In certain phones, software updates may reset the adb settings. Just re-apply the fix after the software updates by running
```bash
adb shell settings put system csc_pref_camera_forced_shuttersound_key 0
```
or create a script / app for automatically doing so, and you will be ready to go!

### Credits
Special thanks to https://zaezin.tistory.com/496
