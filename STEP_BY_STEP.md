# Step By Step Installation Guide for Catalina >=10.15.2

## BIOS Settings

BIOS version: `F11`

- Load Optimized Defaults
- Settings -> Internal Graphics -> Enabled
- Settings -> DVMT Pre-Allocated -> 32M
- Settings -> Wi-Fi -> Disabled
- Settings -> Above 4G Decoding -> Enabled
- Settings -> Wake on LAN Enable -> Disabled
- Settings -> USB Configuration -> Legacy USB Support -> Disabled
- Settings -> USB Configuration -> XHCI Hand-off -> Enabled
- Settings -> Software Guard Extensions(SGX) -> Disabled
- Settings -> Trusted Computing -> Security Device Support -> Disabled
- Boot -> CSM Support -> Disabled


## USB

- Format: Mac OS Extended.
- Schema: GUID Partition Map       

Follow Apple's instruction on how to use "createinstallmedia" command [https://support.apple.com/en-us/HT201372](https://support.apple.com/en-us/HT201372)

### Clover for USB Installer

Download Clover installter from [here](https://github.com/Dids/clover-builder/releases). Open it and choose USB as install location. Customize as following;

```
- Clover for UEFI booting only
- Install Clover in the ESP
- UEFI Drivers
	- Recommended drivers
		- ApfsDriverLoader
		- AptioMemoryFix
		- FSInject
		- HFSPlus
	- Additional drivers
		- EmuVariableUefi
```

### Additional Driver
- VirtualSMC.efi

### Kext
- AppleALC.kext
- IntelMausiEthernet.kext
- Lilu.kext
- SMCProcessor.kext
- SMCSuperIO.kext
- VirtualSMC.kext
- WhateverGreen.kext
- USBInjectAll.kext

### config.plist

Use `config_usb.plist`

Boot from USB and install macOS. 

## Post Install

### Configure USB
Follow this guide: [https://www.tonymacx86.com/threads/the-new-beginners-guide-to-usb-port-configuration.286553/](https://www.tonymacx86.com/threads/the-new-beginners-guide-to-usb-port-configuration.286553/)
[USBMAP.md](USBMAP.md) 

### Clover

```
- Clover for UEFI booting only
- Install Clover in the ESP
- UEFI Drivers
	- Recommended drivers
		- ApfsDriverLoader
		- AptioMemoryFix
		- FSInject
		- HFSPlus
	- Additional drivers
		- EmuVariableUefi
- Install RC scripts on target volume
```

### Additional Driver
- VirtualSMC.efi

### Kext
- AppleALC.kext
- IntelMausiEthernet.kext
- Lilu.kext
- SMCProcessor.kext
- SMCSuperIO.kext
- VirtualSMC.kext
- WhateverGreen.kext
- USBMap.kext # created from the previous step

### config.plist

Use `config.plist`

### For sleep to work properly

```
sudo pmset hibernatemode 0
sudo pmset proximity 0
```
