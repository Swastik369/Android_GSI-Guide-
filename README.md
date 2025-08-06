# 🚀 GSI Noob Guide: Installing GSI & Checking Treble Support 

> **For: Android Enthusiasts Who Want to Install a GSI**  
> _This guide assumes your device bootloader is already unlocked, you have a PC, USB cable, and basic knowledge of ADB & Fastboot._

---

## 1. Check Treble & GSI Support

### 1.a Using Treble Info App  
- Download **Treble Info** app from Play Store.  
- Open it and confirm:  
  - **Is your device Treble compatible?** → Should say _Yes_.  
  - **Partition type:** → Should be _A/B_ or _A-only_.

### 1.b Manual Method  
Connect your device and run:

adb shell getprop ro.treble.enabled

- If it returns **true** → Device supports Treble & GSIs.  
- If **false** → GSI installation is NOT supported.

---

## 2. Download a Suitable GSI

- Download a GSI image of your choice (e.g., Phh-Treble, LineageOS GSI).  
- Match the GSI architecture (`arm`, `arm64`, `aonly`, `ab`) with your device’s partition type.

---

## 3.  Prepare & Flash the GSI

### 3.a Boot to Fastboot Mode

adb reboot bootloader


### 3.b Wipe for Clean Install (Recommended)

fastboot erase system
fastboot erase userdata


### 3.c Flash the GSI Image

- If your GSI is zipped, unzip it first to get the `.img` file.  
- Flash the system image:

fastboot flash system <gsi-image-name>.img



- For A/B devices, flash vbmeta with verity and verification disabled (if required):

fastboot --disable-verity --disable-verification flash vbmeta vbmeta.img 


### 3.d Reboot Device

fastboot reboot

--

## 4.  First Boot & Troubleshooting

- The first boot after flashing a GSI can take several minutes — be patient!  
- If you encounter bootloops:  
  - Verify you are flashing the correct GSI for your device’s architecture and slot configuration.  
  - Consider reflashing your stock ROM and trying again.

---

## 📚 Resources & Credit

- Treble Info app  
- [Phh’s GSI Wiki](https://github.com/phhusson/treble_experimentations/wiki)  
- XDA Developers Treble Forums  

> _Feel free to contribute improvements or open issues if you find bugs!_
