# Build Notes

---

## Toolset
This was painful to figure out. The ArchWSL and ArchWSL-Appx projects require different compilers/SDK's but Visual Studio (or my lack of ability to use it) didn't give useful error messages and I got to a point where one said "Platform Toolset: Visual Studio 2022 (v143)" and the other said ""Platform Toolset: Visual Studio 2022 (v143) not installed".

### Visual Studio Installer

The installer must be run as admin. If not run as admin, it runs but installs appear to proceed but fail silently.

###	Visual Studio Community 2022
* ArchWSL
	* workload: "Desktop development with C++"
        * MSVC v143 - VS 2022 C++ x64/x86 build tools
        * Windows 11 SDK

      (I'm not sure that needed both but by the time it worked, I didn't care to figure it out. I think one of these came with MSBuild)

*	ArchWSL-Appx
    * workload: "Universal Windows Platform development"
        * C++ (v143) Universal Windows Platform tools
        * Windows 11 SDK

### Visual Studio Build Tools 2022

* workload: "Desktop development with C++"
    * MSVC v143 - VS 2022 C++ x64/x86 build tools
    * Windows 11 SDK

  (same notes as above)

* workload: "Universal Windows Platform development"
    * C++ (v143) Universal Windows Platform tools
    * Windows 11 SDK (10.0.22000.0)
    * Windows 11 SDK (10.0.22621.0)
  
  (I doubt I needed both versionds of SDK, probably an accident that one isn't uninstalled)

* workload: ".NET desktop build tools"
    * .NET Framework 4.8 development tools
    * .NET SDK

  I'm _pretty sure_ I needed both the UWP and .NET tools but not 100% if it was really just one or the other.

---

## Building

* build.bat

    * modify path/version of MSBuild in the binary locator logic
    
    * I think I got build.bat to work for the launcher, but not the -Appx app (or vice versa). I'm sure I could have figured out how to get it to work. Debug|Release and x64|ARM

* Visual Studio
    
    * I think I used VS to build the -Appx (and thus the final package)

* build.py (from https://github.com/vineelsai26/Arch-WSL) could be investigated
