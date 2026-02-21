Automatically patch system.img for use with Bigme B1051C Pro, adding eink features support

# I never did get this working 100%, so take these changes with a grain of salt.

# NOTE: MAKE SURE YOU BACKUP YOUR SYSTEM IMAGE WITH MTK_CLIENT
- SEE: https://vbh.ai/unlocking-the-bootloader-and-rooting-the-hibreak-pro/
    - As steps are identical for the B1051C

To run the script on linux and patch your own treble based system.img you simply have to:

- Download a treble-droid based system.img you want to use
- Download and extract a9_system_patcher.zip from https://github.com/damianmqr/a9_accessibility_service/releases/latest
- Go in terminal to the folder containing unzipped files
- Run `sudo bash patch_system_img.sh /path/to/system.img`
- system_patched.img will be saved in the same directory, ready to be flashed

Flashing the resulting file is done the same as any other system.img
**(make sure your bootloader is unlocked! and you have disabled vbmeta verification by reflashing with `fastboot flash vbmeta --disable-verity --disable-verification vbmeta.img`)**

- reboot to fastbootd using `adb reboot fastboot` (or any other method)
- run `fastboot flash system system_patched.img`
- after that's done, run `fastboot -w`
- run `fastboot reboot` and give it a few minutes

## Licensing

### MIT License
Most of the project is licensed under the MIT License unless specified otherwise

The code and releases are provided “as is,” without any express or implied warranty of any kind including warranties of merchantability, non-infringement, title, or fitness for a particular purpose.

### Apache License 2.0
The file `HardwareGestureDetector.kt` includes code derived from AOSP. The original code is subject to the following license:

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.

Modifications and additions to the original code are licensed under the MIT License

# Further Notes on Hardware Locations and variables for this device:
### Modes

#### Default 
ro.vendor.xrz.default_anti_alias: 0
ro.vendor.xrz.default_anti_flicker: 0git 
ro.vendor.xrz.default_auto_clean: 1
ro.vendor.xrz.default_brightness_level: 0
ro.vendor.xrz.default_color_enhance: 80
ro.vendor.xrz.default_contrast_level: 0
ro.vendor.xrz.default_refresh_frequency: 0
ro.vendor.xrz.default_refresh_mode: 178

#### Magazine
sys.maga_anti_flicker: 0
sys.maga_auto_clean: 0
sys.maga_brightness: 0
sys.maga_color_enhance: 80
sys.maga_contrast: 0
sys.maga_refresh_mode: -2147483471

#### Comic
sys.comic_anti_flicker: 0
sys.comic_auto_clean: 0
sys.comic_brightness: 0
sys.comic_color_enhance: 90
sys.comic_contrast: 90
sys.comic_refresh_mode: 180`

#### Video
sys.video_anti_flicker: 1
sys.video_auto_clean: 1
sys.video_brightness: 0
sys.video_color_enhance: 80
sys.video_contrast: 0
sys.video_refresh_mode: 179

#### Force Global Refresh Mode
vendor.xrz.force_global_refresh_mode: -1

#### Refresh Frequency
ro.vendor.xrz.default_refresh_frequency: 0

#### Full Refresh Fequency
vendor.xrz.clean_frequency: 0 - 50

#### Lights
/sys/devices/platform/11d20000.i2c1/i2c-1/1-0036/lm3630a_warm_light 0-222
/sys/devices/platform/11d20000.i2c1/i2c-1/1-0036/lm3630a_cold_light 0-222

Clean
clean_a2=0

Antiflicker
anti_flicker=0 // not in eink settings

no white or black threshold path

no edb contrast

