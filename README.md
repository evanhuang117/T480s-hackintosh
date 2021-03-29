Full hotpatch configuration. Sleep is working but I completely disabled hibernate in my attempts to fix sleep issues. Not messing with hibernation right now, sleep is good enough. Undervolt works really well with voltageshift, running -80mv on CPU/Cache, -30mv on GPU, 20w/25w short/long PL. Took a longgggg time to get to this point... safe to say I'm not excited for Big Sur - I might switch to Opencore

## Specs
|||
|--|--|
| CPU | i7-8650u |
| NVME 2280 | Adata XPG8200 (1tb) - Windows|
| NVME 2242 (WWAN) | WD SN520 (512gb) - OSX|
| RAM | 16gb |
| Display | WQHD |
| Wifi | Fenvi BCM94352Z DW1560 |
| Repasted with Thermal Grizzly Kryonaut| I don't think this helped all that much with temps, still idles around 40c|

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
 - Brightness keys
 - Volume keys
 - Power management is good, especially with undervolting
	 - ~6hr+ of battery life, idle drain <3w
 - Got sleep working with a custom hotpatch
 	 - Custom USB SSDT patch -> this may need to be changed depending on setup, use Hackintool it's easy
  	 - Completely disabled wake on USB (doesn't matter anyways as its a laptop)
	 - Rename GPRW to XPRW and create an XPRW SSDT to override the original method
	 - I think the renames and stuff broke Hackintool as I can no longer export USB configs anymore, use USBMap as an alternative
 - iMessage, Facetime, App Store
 - USB-C Hotplug and unplug
 - Thunderbolt 3 Hotplug, hot unplug instantly kernel panics
 - Clamshell mode with HDMI output
 - CS major street cred++++++++

## Not working
 - Power button LED flashes after waking from sleep
 - Thunderbolt 3 hotplug - instant kernel panic, have to do another ACPI patch unfortunately
 	- I haven't tested plugging it in before boot (no hotplug) which I think will work

## Untested
 - Headphone jack
 - SD card
 - USB C output

## Sleep Settings

pmset settings are important for sleep (I think), this is what is working for me right now on battery. I've also disabled Find My Mac, enhanced notifications, wake for network, power nap, automatic updates... basically anything that could possibly do anything during sleep.

|```pmset -g```||
 |--|--|
| standbydelaylow  |    3600 |
| standby          |    0|
| halfdim          |    1|
| hibernatefile    |    /var/vm/sleepimage|
 |proximitywake    |    0|
 |gpuswitch        |    2|
| powernap         |    0|
| disksleep        |    1|
| standbydelayhigh |    7200|
| sleep            |    5|
| autopoweroffdelay |   28800|
| hibernatemode    |    3|
| autopoweroff     |    1|
| ttyskeepawake    |    1|
| displaysleep     |    3|
| tcpkeepalive     |    0|
| highstandbythreshold | 50|
| lidwake            | 1|

### Here are some code snippets that are useful for debugging sleep problems

- Run ```sleepless``` after this to find current idle sleep preventers

```alias sleepless="pmset -g assertions | egrep '(PreventUserIdleSystemSleep|PreventUserIdleDisplaySleep)'"```

- Get the wake/sleep commands and their reasons

```pmset -g log|grep -e " Sleep  " -e " Wake  "```

- This one is also useful to get more info on the cause of sleep/wake requests, it's very messy and hard to read though

```pmset -g log|grep -e " Assertions " ```


## Repos I used

[https://github.com/mohamedspicer/hackintosh-T480s](https://github.com/mohamedspicer/hackintosh-T480s)

[https://github.com/kk1987/T480s-hackintosh/](https://github.com/kk1987/T480s-hackintosh/)

[https://github.com/lisovskiy01/T480s-hackintosh](https://github.com/lisovskiy01/T480s-hackintosh)

[https://github.com/beele/thinkpad-t480-hackintosh](https://github.com/beele/thinkpad-t480-hackintosh)

[https://github.com/tienhuynh5312/ThinkPad-T480-Hackintosh](https://github.com/tienhuynh5312/ThinkPad-T480-Hackintosh)
