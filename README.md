# Windows 10 Setup

## Uninstall pre-installed apps

1. `Win` + `X` > Windows PowerShell (Admin)
2. Run one of the follows:
  * Remove All Apps except Store from Your (current) Account
    ```
    Get-AppXPackage | where-object {$_.name –notlike "*store*"} | Remove-AppxPackage
    ```
  * To Remove All Apps except Store from All Current Accounts on PC
    ```
    Get-AppxPackage -AllUsers | where-object {$_.name –notlike "*store*"} | Remove-AppxPackage
    ```
3. (Optional) Reinstall [
Windows Calculator](https://www.microsoft.com/en-us/p/windows-calculator/9wzdncrfhvn5) or [Snip & Sketch](https://www.microsoft.com/en-us/p/snip-sketch/9mz95kl8mr0l) or [uBlock Origin](https://www.microsoft.com/en-us/p/ublock-origin/9nblggh444l4)


## Remove OneDrive

* Run `RemoveOneDrive.bat`

### CMD or PowerShell Mono Font

* [msjhmono](https://storage.googleapis.com/google-code-archive-downloads/v2/code.google.com/cs-drag4ie9/msjhmono.zip) or 華康 OO 體
* Title Bar > Right click > Properties > Font
* (Untested) [Windows cmd Consolas](http://nkidtw-program.blogspot.com/2010/09/windows-cmd-consolas.html)

## *.reg

### Remove All user Folders in This **PC**

* Run `Remove_All_user_Folders_in_This_PC.reg` (64-bit) to remove all
* Run `Restore_All_user_Folders_in_This_PC.reg` (64-bit) to restore
    > Remove the `;` before lines you want to restore

### Restore Windows Photo Viewer

1. Run `Restore_Windows_Photo_Viewer_with_Sort_order_fix.reg`
2. Settings > Apps > Default apps > Photo viewer
3. (Optional) [Fix Windows Photo Viewer yellow tint background](https://optimwise.com/fix-windows-photo-viewer-yellow-tint-background/)

### Remove ModernSharing

* Run `Remove_ModernSharing.reg`


## Windows Update

### Disable (with Professional ↑ editions)

1. `Win` + `R` > `gpedit.msc`
2. Navigate to `Computer Configuration \ Administrative Templates \ Windows Components \ Windows Update`
3. Locate the `Configure Automatic Updates` > Enabled > `2 - Notify for download and auto install`

### Temporarily Hide

* Run `wushowhide.diagcab`

### Update Windows Defender

1. `Win` + `R` > `taskschd.msc`
2. Right panel > Create Basic Task
   1. Name: `Defender Update`, Description: `Update Windows Defender`
   2. Daily > Set the Time > Start a program
      1. Program/script: `C:\Program Files\Windows Defender\MpCmdRun.exe`
      2. arguments: `-SignatureUpdate`
3. Active Tasks > `Defender Update`
   1. `Defender Update` > Right click > Properties > Triggers > Edit...
   2. Advanced settings > Check `Repeat task every` > select a time intervel

## Apps

### O&O ShutUp10

1. [Download](https://dl5.oo-software.com/files/ooshutup10/OOSU10.exe) and Run `OOSU10.exe`
2. Actions > Apply only recommended settings > reboot

### Windows 7 calculator

* Files from the old Windows 7
  * `C:\Windows\SysWOW64\calc.exe`
  * `C:\Windows\SysWOW64\zh-TW\calc.exe.mui`
* Rename and Copy the files into the same path (`calc1.exe`, `calc1.exe.mui`)
  * Type `calc` to find `calc1.exe` in the `SysWOW64` folder and Run it (for 0101) !

### WSL Bash

#### Installation

1. `Win` + `R` > `optionalfeatures` > Check `Windows Subsystem for Linux` > reboot
2. (Optional) Setup your PC's name
   1. `Win` + `R` > `sysdm.cpl` > rename > reboot
3. Microsoft Store > Install `Ubuntu` > Launch and setup user/pass

#### wsl-terminal

* [Download](https://github.com/goreliu/wsl-terminal#usage)
* Add context menu
   1. cmd.exe > locate to `wsl-terminal\tools`
   2. Run `wscript 1-add-open-wsl-terminal-here-menu.js`
* Add shortcut key
   1. Right click on `wsl-terminal\open-wsl.exe` > `Pin to Start`
   2. Start > Right click on `wsl-terminal` > More > Open file location
   3. Right click on the shortcut > Proerties > `Shortcut key`
* Theme
  * Copy [`flat-dange0.minttyrc`](https://github.com/dange0) into `wsl-terminal\etc\themes`
  * Title Bar > Right click > Properties > Select 

### [Chocolatey](https://chocolatey.org/)

* [Installation](https://chocolatey.org/install#install-with-powershellexe)
* [Usage](https://github.com/chocolatey/choco/wiki/CommandsReference)
```
choco install python git iperf3 jre8 streamlink
choco uninstall [package]
choco list --local-only
```
* [Packages](https://chocolatey.org/packages)

### Other Apps

* Player
  * foobar2000
  * [VLC](https://www.videolan.org/vlc/download-windows.zh-TW.html)
  * [MPC-HC](https://mpc-hc.org/)
* Editor
  * [**Visual Studio Code**](https://code.visualstudio.com/)
  * [Notepad++](https://notepad-plus-plus.org/)
* SSH Client
  * [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
  * [Pietty](https://sites.google.com/view/pietty-project)
  * [Xshell](https://www.netsarang.com/products/xsh_overview.html)
  * [WinSCP](https://winscp.net/eng/docs/portable)
    * FTP, SCP, SFTP
* Tool
  * [**Bandizip**](https://www.bandisoft.com/bandizip/)
    * Compression, Decompression, Explorer shell menu
  * [**Greenshot**](http://getgreenshot.org/)
    * Screenshot
  * [HashTab](http://implbits.com/products/hashtab/)
    * MD5, SHA1... in Properties
  * [Geek Uninstaller](https://geekuninstaller.com/download)
  * [FreeFileSync](https://www.azofreeware.com/2009/09/freefilesync-22.html)
    * folder comparison and synchronization
  * [Rufus](https://rufus.ie)
    * Create bootable USB drives
  * [JDownloader](https://www.azofreeware.com/2009/06/jdownloader-06193.html)
  * [NewFileTime](https://www.azofreeware.com/2015/12/newfiletime.html)
    * manipulate timestamps
  * [NTPClock](http://www.stdtime.gov.tw/chinese/home.aspx)
  * [Caffeine](https://www.zhornsoftware.co.uk/caffeine/index.html#Versions)
    * keep awake
  * [**H**ttp **F**ile **S**erver](http://www.rejetto.com/hfs/?f=dl)
    * [working with upload](http://www.rejetto.com/wiki/index.php?title=HFS:_Working_with_uploads)
  * Disk
    * [CrystalDiskInfo](https://crystalmark.info/en/download/#CrystalDiskInfo)
    * [Defraggler](https://www.ccleaner.com/defraggler/download/portable)
    * [AS SSD Benchmark](https://www.azofreeware.com/2018/05/as-ssd-benchmark.html)
      * ahci, alignment
  * Info
    * [CPU-Z](https://www.cpuid.com/softwares/cpu-z.html)
    * [GPU-Z](https://www.techpowerup.com/download/techpowerup-gpu-z/)
    * [HWMonitor](https://www.cpuid.com/softwares/hwmonitor.html)
      * hardware sensor monitoring
    * [AIDA64](https://www.azofreeware.com/2014/05/aida64-4503000.html)
      * stress test
  * USB
    * [USBDeview](https://www.nirsoft.net/utils/usb_devices_view.html)
      * lists all devices, uninstall
    * [ChipGenius](https://www.filecroco.com/download-chipgenius/)
      * device details
  * Entertainment
    * [3D Youtube Downloader](https://yd.3dyd.com/)
    * [BeanfunLogin](https://kaihao.info/BeanfunLogin/)
    * [streamlink-twitch-gui](https://github.com/streamlink/streamlink-twitch-gui/releases)
      * require streamlink (choco or [installer](https://streamlink.github.io/install.html#windows-binaries))
    * [Discord portable](https://portapps.github.io/app/discord-portable/)



## Themes

### Background

* [Poro](https://wallpapertag.com/wallpaper/full/a/2/b/631216-poro-wallpapers-1920x1080-ipad.jpg)
* [BMO](http://i.imgur.com/GeZYrrO.png)

### Cursors

1. Download and Copy into **`C:\Windows\Cursors`**
   1. [MapleStory](http://www.rw-designer.com/cursor-downloadset.php?id=original-maplestory-white)
   2. [滑鼠1.ani > aero_link.ani](http://www.mediafire.com/?fx92ogov01j47wg)
2. Desktop > Right click > Personalize > Themes > Mouse cursor


## Others
* [Make Windows 10’s File Explorer start in any folder you want](https://www.digitalcitizen.life/how-make-windows-10s-file-explorer-start-any-location-you-want)
* [Switch between Static IP and DHCP](https://gist.github.com/happyincent/7318da7a88a3cfda0254d10b7d3a4dc8)
* [SimpleHTTPAuthServer](https://github.com/tianhuil/SimpleHTTPAuthServer) (Python2)

## References

* Remove All user Folders in This PC
  * https://www.tenforums.com/tutorials/6015-add-remove-folders-pc-windows-10-a.html
  * https://www.howtogeek.com/331361/how-to-remove-the-3d-objects-folder-from-this-pc-on-windows-10/
* Restore Windows Photo Viewer
  * https://www.tenforums.com/tutorials/14312-restore-windows-photo-viewer-windows-10-a.html
* Remove ModernSharing
  * https://www.ptt.cc/bbs/Windows/M.1508359307.A.100.html
* Uninstall pre-installed apps
  * https://www.thewindowsclub.com/uninstall-preinstalled-apps-games-windows-10-setting
* MapleStory Cursors
  * http://www.rw-designer.com/cursor-set/original-maplestory-white
  * https://forum.gamer.com.tw/Co.php?bsn=07650&sn=5275304
* Remove OneDrive
  * https://gist.github.com/shrayasr/d3a4987ebd5b508f6490
* Windows Update
  * https://kheresy.wordpress.com/2015/09/01/windows-update-of-windows-10/
  * https://www.thewindowsclub.com/update-windows-defender-automatic-windows-updates-disabled
* O&O ShutUp10
  * https://www.ptt.cc/bbs/EZsoft/M.1449856893.A.41E.html