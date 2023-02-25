<div align="center">
    <img src="ArchWSL/images/icon.png?raw=true" alt="Logo" width="150" height="150">
</div>

# Arch Linux in WSL

Build a Windows Subsystem for Linux (WSL) distribution installer/launcher application.

---

## Install

1. The latest version of WSL is available from the [Microsoft Store](https://apps.microsoft.com/store/detail/windows-subsystem-for-linux/9P9TQF7MRM4R)

2. Download the .appx app and corresponding .cer cert from [releases/latest](releases/latest)

3. Import the self-signed .cer to `Trusted Publisher` and `Trusted Root Certificate Authority`

4. Install the .appx app package

---

## Build

1. Obtain root filesystem tarball and save as x86\install.tar.gz. I preferred the method from [badgumby/arch-wsl](https://github.com/badgumby/arch-wsl)

2. Setup and build:

	* Detailed notes: [build-notes](doc\build-notes.md) supplement the Microsoft [README](doc\readme_MS.md)

	* Visual Studio isn't strictly required, but it was practically so in order to get the build tools setup and .vcxproj files corrected.

---

## Notes

1. The command `netsh winsock reset` has been used to solve a number of strange WSL failures, for example:

	> The attempted operation is not supported for the type of object referenced. Error code: Wsl/Service/0x8007273d

---

## To-do

1. Any other [advanced settings](https://learn.microsoft.com/en-us/windows/wsl/wsl-config) and then add /etc/wsl to rootfs

2. Eliminate ARM build targets if not needed (or figure out necessary tools)

---

## Credits

This solution was pieced together from multiple sources:

* [microsoft/WSL-DistroLauncher](https://github.com/microsoft/WSL-DistroLauncher/tree/master/DistroLauncher) -  WSL Distro Launcher Reference Implementation

* [vineelsai26/Arch-WSL](https://github.com/vineelsai26/Arch-WSL) - mainly used for logos, etc. in ArchWSL-Appx/Assets and overall guidance

* [badgumby/arch-wsl](https://github.com/badgumby/arch-wsl) - good instructions for creating Arch based WSL rootfs (not packaged as .appx)