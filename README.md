# OpenCore for macOS Monterey on ThinkPad X1 Yoga 3 (2018)
A complete OpenCore folder for hackintoshing the Lenovo ThinkPad X1 Yoga Gen 3 (2018) with Monterey (specifically Model 20LF). Based on OpenCore 0.8.5
![](https://i.imgur.com/Zjjm45P.png)

**I am by no means a hackintosh expert, and this is only a snapshot of what I got to work with my system. I can only provide limited support.**

Most things work great such as:
  - Keyboard w/ Special Functions
  - TrackPad incl. full multi-touch gestures
  - TrackPoint (see notes)
  - USB-C data & charging
  - Battery monitoring
  - Webcam / Mic
  - WiFi (see notes) & Bluetooth
  - SD Card Reader
  - iServices (see installation)

What doesn't work / cannot test / haven't tested:
  - Touch Screen / Pen
  - Fingerprint Reader
  - WWAN
  - HiDPI (I have a 1080p model so it's not needed)
  - Thunderbolt 3
  
## Notes on making things work / Disclaimers
  - Sleep mode kinda sucks. The OS doesn't tell your CPU to quiet down when the lid is closed, which leads to excess heat and power draw. This can probably be fixed with some tweaking to the ``config.plist``that I just haven't figured out yet.
  - WiFi works great, except after you wake from sleep. It will randomly disconnect whenever it feels like. It's not too annoying, because you can just go to the WiFi menu and reconnect. On multi access-point networks, such as a school, you may have to renew your DHCP lease as you move between the APs as well.
  - Out of the box, the TrackPoint works great minus scrolling. The middle button is middle click without an app like [Smart Scroll](https://www.marcmoini.com/sx_en.html) to disable that.

## Installation
  1. Follow Dortania's OpenCore guide [here](https://dortania.github.io/OpenCore-Install-Guide/) up until "Adding base OpenCore files"
  2. Drag the folders from this repo into the ``EFI/OC`` folder. Select replace, NOT merge.
  3. Go into the BIOS and configure these settings: ![bios settings](https://i.imgur.com/ScfQBMF.png)
  4. Boot into the installer and configure your SSD. APFS is supported and recommended, although I have not tested the full disk encryption version.
  5. Install, go through the onboarding, and download [MountEFI.](https://github.com/corpnewt/MountEFI) Copy your EFI folder from your USB to your SSD.
  6. Follow the [Fixing iServices section of Dortania's OpenCore Post-Install Guide](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#using-gensmbios). Apply the changes to ``config.plist > PlatformInfo > Generic``. Ignore the ``DataHub``, ``PlatformNVRAM``, and ``SMBIOS`` dictionaries within ``PlatformInfo``; only ``Generic`` matters.

## Credit to:
  - [Mapomme on Olarila](https://www.olarila.com/topic/23224-monterey-on-lenovo-x1-yoga-3rd-gen/) for making the base of this folder.
  - [Tyler Nguyen](https://tylernguyen.github.io/x1c6-hackintosh/) for making the X1 Carbon 6 folder (very similar to this one) and the BIOS settings graphic.
