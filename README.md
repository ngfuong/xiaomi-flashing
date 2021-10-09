# xiaomi-flashing
A basic flashing guide that one needs to read before trifling with ROOTING/flashing Xiaomi's ROMs.

## Official Stock ROM
* Stock recovery ROMs of every models are available on <a href="https://c.mi.com/global/miuidownload/index">Miui Official ROM Site</a>. I repeat. EVERY.
* <a href="https://mifirm.net/">Mifirm</a> is a reliable source (both recovery ROM and fastboot firmware) but AdBlock is not welcomed.

## (1) Unlock bootloader
* The bootloader of recent Xiaomi phones is locked by default.
* In order to establish ADB (Android Debugging Bridge) and start tampering, the bootloader has to be unlocked first.
> **Warning**
> 
> * Unlocking bootloader (and further installing other ROMs) will __erase all data on your phone so PLEASE MAKE A BACKUP__.
> * A SIM with internet connection is needed.
> * In each and every steps of this tutorial, remember to __connect your phone via a USB cable and a USB port or hub__. Do not use other cables or ports (like Thunderbolt) because it might affect compatibility. In some scenarios, you have to use USB Type-A 2.0 ports instead of 3.0.

### Unlock Xiaomi
1. Create a Mi account directly in __Settings -> Account__ menu in your phone or you can create by using <a href="https://account.xiaomi.com/pass/register/">this website</a>.
1. Enter Developer Mode in __Settings -> About Phone__ by tapping the MIUI version repeatedly until you are a developer.
1. Link your phone to the Mi account in __Settings -> Additional settings -> Developer options -> Mi Unlock status__.
1. Download the Mi Unlock App (only works with Windows) from <a href="https://en.miui.com/unlock/download_en.html">this website</a>.
1. Shutdown your Xiaomi and enter Fastboot mode (by simultaneously holding __Volume Down__ and __Power__ until the Mi logo appears, if the Mi rabbit appears you are in).
1. Connect your phone to PC using a USB cable and click __Unlock__. Wait until it completes and the phone will reboot.
> **Note**: 
> If you have just bought your Xiaomi, you might need to wait for several days until you can request an unlock.
  
### Enable USB debugging
1. Enter Developer Mode again.
1. Enable USB debugging via __Settings -> Additional Settings -> Developer Options__.
1. (optional) Enable **File Transfer** in USB debugging mode when connected to computer 

## (2) Flashing
### Install a custom recovery
1. Download the latest version of <a href="https://twrp.me/Devices/Xiaomi/">TWRP</a>.
1. Connect your phone to the computer.
1. Open a terminal (as root) where you store your recovery and type:
`adb reboot bootloader`
This command puts your phone into bootloader mode. Alternatively, you can just enter fastboot by holding the key combination.
1. Verify that your device is recognized:
`fastboot devices`
1. Flash the recovery into your device:
`fastboot flash recovery *recovery_file*.img`
1. Because Xiaomi default recovery may override the custom recovery, you have to reboot into recovery by hold __Volume Up__ and __Power__ until the Mi logo appears and the phone vibrates (or else you have to do all the steps all over again).
> **Note**: 
> There are many custom recovery but I mainly use TWRP. Not every TWRP here works. One time or another you have to use a specifically moded version of TWRP for your phone or you have to use another recovery (E.g. Xiaomi Mi 9 SE).
### Flasing firmware (optional)
If your current MIUI is not up to date, download an official firmware stock ROM and flash it first then reboot to fastboot and flash your custom ROM after. Remember to back up your data before flashing or wiping anything.
### Flasing custom ROM
In recovery:
1. __BACK UP YOUR DATA__.
1. Download your custom ROM (__.zip__) to your computer and copy it into the __/sdcard__ of your phone.
Wipe __Dalik/David Cache__, __Cache__ and __Data__.
1. __Format Data__ (in __Advanced Wipe__) or __Factory Reset__, which will decrypt data, format your partition and delete all files.
1. In the __Install__ menu, choose your copied ROM and flash it.
1. Alternatively, enter the __Advanced Settings -> Apply from ADB__ (or something like that) and type on your terminal:
`adb sideload *ROM_file*.zip` (This is not needed if you copy and install the ROM directly the phone)
1. (optional) Install GApps if your custom ROM requires
1. Once the ROM has been flashed successfully, reboot into system and your phone is running on a new ROM!
> **Warning**: 
> __DELETE/WIPE SYSTEM__ poses a high chance that your phone will get stuck in a fastboot loop.
## Boot Loop Recovery
If you are in a fastboot loop, you need:
  ### Qualcomm USB Driver (optional)
  * If you are using Windows, it will be automatically installed when you plug the USB in.
  * If there is some error, install it manually <a href="https://gsmusbdrivers.com/download/android-qualcomm-usb-driver/">here</a>.
  * Often, different USB ports/hub will work differently. So try every combination of hub/ports before reporting issues.
  ### A flash tool (choose one)
  1. <a href="https://www.xiaomiflash.com/download/">Official Xiaomi Flash Tool</a>
    * This only works in Windows and before using it will invoke specific drivers to be installed.
    * If there is an error while installing drivers, try creating a log folder (to store log) in the same folder as the .exe file and run the tool again.
  1. <a href="https://www.xiaomitool.com/V2/">Xiaomi Tool V2</a>
    * This is a custom tool that helps moding ROM in every Xiaomi phones.
    * Only runs on Windows.
  1. <a href="https://github.com/Szaki/XiaomiADBFastbootTools">Xiaomi ADB/Fastboot Tools</a>
    * This is a custom tool that runs on Windows, MacOS, Linux.
    * If you keep getting random errors using Xiaomi Flash, use this. It requires Oracle Java and OpenJDK >=11.
  ### An official fastboot ROM
  * Download an official fastboot ROM (or your fastboot old ROM for safety measures). Refer to the [Official Stock ROM section](#official-stock-rom) for downloads.
  * Remember, it has to be a FASTBOOT ROM (__.tgz__ or __.gz__ and you have to rename it into __.tgz__) or else you cannot flash in fastboot.
  ## Flashing official stock ROM
  If you use Xiaomi ADB/Fastboot Tools, the process is:
  1. Boot phone into bootloader
  1. In the Fastboot Menu, select ROM folder (unzip the __.tgz__ or __.gz__ file)
  1. Select the Clean Install option
  1. Begin flashing

