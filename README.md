Full hotpatch configuration.

## Specs
|||
|--|--|
| CPU | i7-8650u |
| NVME 2280 | Adata XPG8200 (1tb) - Windows|
| NVME 2242 (WWAN) | WD SN520 (512gb) - OSX|
| RAM | 16gb |
| Display | WQHD |
| Wifi | Fenvi BCM94352Z DW1560 |

## Working
 - Webcam 
 - Trackpoint/touchpad 
	 - middle scroll is extremely fast and triggers clicking action (ACPI or VoodooPS2 I think)
	 - All gestures working natively
 - HiDPI scaling
 - Microphone
 - Speakers 
 - USB
 - Airdrop, Handoff, Sidecar wireless and wired
 - Wifi
 - Ethernet
 - Keyboard backlight
 - Volume keys
 - Power management is good, especially with undervolting
	 - ~6hr+ of battery life, idle drain <3w
 - Got sleep working with a custom hotpatch
 	 - Custom USB SSDT patch -> this may need to be changed depending on setup, use Hackintool it's easy
  	 - Completely disabled wake on USB (doesn't matter anyways as its a laptop)
	 - Rename GPRW to XPRW and create an XPRW SSDT to override the original method
 - iMessage, Facetime, App Store
 - CS major street cred++++++++

## Not working
 - Power button LED flashes after waking from sleep
 - Brightness keys (ACPI problem)
 	 - this is very weird because I have the correct SSDT hotpatch for fn keys...

## Untested
 - Headphone jack
 - SD card
 - USB C output
 - Thunderbolt

## Repos I used

[https://github.com/mohamedspicer/hackintosh-T480s](https://github.com/mohamedspicer/hackintosh-T480s)

[https://github.com/kk1987/T480s-hackintosh/](https://github.com/kk1987/T480s-hackintosh/)

[https://github.com/lisovskiy01/T480s-hackintosh](https://github.com/lisovskiy01/T480s-hackintosh)

[https://github.com/beele/thinkpad-t480-hackintosh](https://github.com/beele/thinkpad-t480-hackintosh)

[https://github.com/tienhuynh5312/ThinkPad-T480-Hackintosh](https://github.com/tienhuynh5312/ThinkPad-T480-Hackintosh)
