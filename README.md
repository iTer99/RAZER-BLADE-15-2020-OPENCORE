# RAZER BLADE 15 (LATE 2020) | RZ09-03519 Running MacOS Monterey - OpenCore bootloader
Bios modding or unlocking doesn't need required (Thank LuxuryWasTaken)

<img src="/Images/monterey.png"  width="1000">
<img src="/Images/monterey2.png"  width="1000">
<img src="/Images/monterey3.png"  width="1000">

<summary><strong>My Hardware 💻</strong></summary>
</br>

| Category                | Specification                                                                                                        |
|:------------------------|:---------------------------------------------------------------------------------------------------------------------|
| Model                   | [RZ09-03519](https://mysupport.razer.com/app/answers/detail/a_id/3919)                                               |
| Processor               | 10th Gen Intel® Core™ i7-10750H processor, 6 Cores / 12 Threads, 2.6 GHz / 5.0 GHz (Base / Max Turbo), 12 MB Cache   |
| Graphics (Integrated)   | Intel® UHD Graphics                                                                                                  |
| Chipset                 | Mobile Intel® HM470 Chipset                                                                                          |
| Graphics (Discrete)     | NVIDIA® GeForce® GTX 1660 Ti (6 GB GDDR6 VRAM, Optimus™ Technology)                                                  |
| 15.6" Display           | 120 Hz Full HD, 16:9 aspect ratio, matte screen with 4.9 mm bezel                                                    |
| Storage                 | 1 TB SSD M.2 NVMe PCIe 3.0 x4 (512 GB x 2)                                                                           |
| Memory                  | 32 GB Samsung dual-channel DDR4-2933 MHz (16 GB x 2)                                                                 |                     
| WLAN + Bluetooth        | Intel® Wireless-AC 9560                                                                                              |
| Webcam                  | Built-in webcam (1MP/720P)                                                                                           |
| Audio support           | HD Audio, Realtek ALC256 codec, dual array microphone, combo audio/microphone jack                                   |
| Battery                 | Built-in 60.8 WHr rechargeable lithium-ion polymer battery                                                           |

<summary><strong>How to install macOS</strong></summary>
</br>

1. [Create an installation media](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/#making-the-installer)
1. Download the this EFI and copy it into the ESP partiton
1. Boot from the USB installer (press `F12` to choose boot volume) and [start the installation process](https://dortania.github.io/OpenCore-Install-Guide/installation/installation-process.html#booting-the-opencore-usb)

<summary><strong>Enable Apple Services</strong></summary>
</br>

1. Run the following script in Terminal

```bash
git clone https://github.com/corpnewt/GenSMBIOS && cd GenSMBIOS && chmod +x GenSMBIOS.command && ./GenSMBIOS.command
```

2. Type `3` to Generate SMBIOS, then press ENTER
3. Type `MacBookPro16,1 5`, then press ENTER. Leave this Terminal window open.
4. Open `/EFI/OC/Config.plist` with any editor and navigate to `PlatformInfo -> Generic`
5. Add the script's last result to `MLB, SystemSerialNumber and SystemUUID`

```diff

<key>Generic</key>
<array>
  </dict>
    <key>AdviseFeatures</key>
    <false/>
    <key>MLB</key>
    <string>*****************</string>
    <key>MaxBIOSVersion</key>
    <false/>
    <key>ProcessorType</key>
    <integer>0</integer>
    <key>ROM</key>
    <data>lVhEd021</data>
    <key>SpoofVendor</key>
    <true/>
    <key>SystemMemoryStatus</key>
    <string>Auto</string>
    <key>SystemProductName</key>
    <string>MacBookPro16,1</string>
    <key>SystemSerialNumber</key>
    <string>*************</string>
    <key>SystemUUID</key>
    <string>*******-****-****-****-************</string>
  </dict>
</array>

```

<summary><strong>What's not working ⚠️</strong></summary>
</br>

- [ ] NVIDIA® GeForce® GTX 1660 Ti doesn't support for MacOS
- [ ] Broken when dualboot with windows if using EFI Opencore
- [ ] HDMI slot cann't use because it work on nVIDIA card so can be replace to USB slot
- [ ] If trackpad have problem, just disabled Force Click and haptic feedback in Settings - Trackpad
- [ ] You talk to me
