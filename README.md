macOS Sierra EFI for the Dell OptiPlex 780 MT using OpenCore. I will try to keep this EFI up to date with the latest OpenCore and kexts

<img width="1280" height="1024" alt="image" src="https://github.com/user-attachments/assets/fbe5aa59-ad1d-4bb9-85d1-97d46564a9d4" />

# WARNING! SMBIOS DETAILS ARE NOT INCLUDED IN THE CONFIG.PLIST.
You will have to use [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) to generate an **iMac10,1** SMBIOS for your system, and add them to the config.plist.

Make sure you're on BIOS A15 before continuing. You can get it from Dell's website. Older versions may cause issues. I do not, and will never support Libreboot.

## Other macOS versions?
Likely not. If someone gets the 5450 working on High Sierra, I will update this EFI with High Sierra support. Earlier versions do not have plans to be supported, and as High Sierra is the last version supported by iMac10,1, nothing after High Sierra will be supported. If you want a different version, feel free to fork this repo to modify it for whatever version you want. Do note newer versions will likely require OCLP.

## System specs
Do note if your hardware differs, while unlikely, you may have issues.
- CPU: Intel Core 2 Duo E7500
- GPU: ATi Radeon HD 5450 512MB
- Chipset: Intel Q45
- Audio: Analogue Devices AD1985A
- Ethernet: Intel 82567LM
- Disk: Seagate Barracuda 160GB 7200RPM 3.5"

## Issues
- NVRAM does not work. On Legacy BIOS with OpenCore, NVRAM never works.
- After waking from sleep, Ethernet does not work. You will have to reboot to get Ethernet to work again.
- If using a VGA output, you'll get an "OUT OF RANGE!"/"Unsupported resolution"/"Input not supported" error on your display. You'll have to manually specify your resolution in UEFI -> Output -> Resolution in the config.plist.

If you notice any other problems, please open an issue (or pull request if you have a fix)

### BIOS settings
If you do not set these BIOS settings, macOS will **not** boot.

- Drivers -> SATA Operation -> RAID Autodetect / AHCI
- System Configuration -> Parallel Port -> Disable
- System Configuration -> Serial Port #1 -> Disable
- Virtualization Support -> Virtualization -> Enable "Enable Intel® Virtualization Technology"
- Virtualization Support -> VT for Direct I/O -> Disable "Enable Intel® VT for Direct I/O"
- Security -> CPU XD Support -> Enable "Enable CPU XD Support"
- Post Behaviour -> Fast Boot -> Disable "Enable Fast Boot"
