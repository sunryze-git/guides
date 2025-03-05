# Windows 7 Survival Guide
*Last updated 2/17/2025*

This guide is not for the inexperienced. You should know a thing or two about how Windows works, how to install it, and how to fix your PC if something goes wrong.

## Hardware Support
Windows 7 supports hardware officially until 2016. Hardware until 2021 is unofficially supported. Past that point is entirely up to your own research.

The following table shows the latest hardware support for Windows 7.

| **Category**     | **Intel**           | **AMD**                   | **NVIDIA**             |
| ------------     | ---------           | -------                   | ----------             |
| **Processor**    | Intel Core 11th Gen | AMD Ryzen 5000 Series     | *N/A*                  |
| **Graphics Card**| Intel UHD 600 Series| AMD Radeon RX 6000 Series*| NVIDIA RTX 3000 Series |

> *Radeon RX 5000 series and newer have issues regarding Aero performance.

## Finding Installation Media
The easiest place to find Windows 7 installation media is through [archive.org](archive.org). Be aware that some of these downloads may be modified. 

## Creating installation media
Modern computers, especially ones made after 2017, need some extra drivers for Windows 7 to run correctly. There are numerous ways to add drivers, ranging from integration software such as [NTLite](https://www.ntlite.com/), and [MSMG Toolkit](https://msmgtoolkit.in/). However, the easiest way is to add drivers using the built-in [DISM](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/what-is-dism?view=windows-11) included with Windows.

### What drivers do I need?
Typically, you will need an updated xHCI (USB 3) stack. This allows Windows 7 to be able to access USB 3 devices. It did include some by default at the time in 2009, however chipsets have been updated since then, and these drivers are not included. The Windows 8 USB stack was backported to Windows 7, and is downloadable [here](https://www.mediafire.com/file/h8zjqo8mxmppm5n). The password for the file is **MDL2024**. This may change over time.

**You will need to install [KB2864202](https://www.catalog.update.microsoft.com/Search.aspx?q=KB2864202) (KMDF Security Update) and [KB4474419](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4474419) (SHA-2 code signing support) before installing or integrating this driver.**

### Creating a working installer
Windows uses two different "systems" to install Windows. It includes the boot preinstallation environment, and the actual system itself. These can be distinguished as boot.wim and install.wim. It may be easier to integrate your drivers and updates in the install.wim as you would, and then swap that into a modern Windows 10 or 11 ISO. This saves you an extra step of having to integrate your drivers in the Windows 7 boot.wim as well.

## Updating the system
If you haven't integrated all the updates with one of the tools mentioned earlier, it is **extremely recommended** that you update the system. Not only for security reasons, but that the system may not even function correctly, since unupdated Windows 7 is missing numerous quality of life patches. 

Updating Windows 7 from official Microsoft servers without the SHA-2 update is impossible. Even with that, the updates are extremely slow, so I recommend setting up [Legacy Update](https://legacyupdate.net/), which will make installing all the updates as easy as possible.

Windows 7 did recieve ESU (Extended Security Updates) until January 2023, however many of you may not know that they actually are still continuing now for certain customers, most notably those who have Windows 7 VMs in Azure. I cannot provide any method to enabling them since that is piracy, however methods do exist, and Windows 7 will be recieving "extended" ESU until January 2026.

### "Spyware Updates"
There were some updates released shortly before Windows 10 came out, and throughout the rest of the Windows 7 support length, that add certain services to Windows 7 that one may call spyware. They do collect telemetry and send it to Microsoft. Below is a list of updates to avoid if you are interested.

*GWX Preparation Updates*
- KB2952664
- KB2976978
- KB2977759
- KB2990214
- KB3021917
- KB3044374
- KB3035583
- KB3139929
- KB3150513

*Telemetry*
- KB3021917
- KB3022345
- KB3068708
- KB3075249
- KB3080149
- KB3081954

## Staying Secure
It is extremely recommended you install antivirus on your system if it is connected to the internet, and set the firewall to the Public setting. Microsoft Security Essentials is not downloadable anymore, however it still will recieve definition updates as long as Microsoft keeps the current virus definition format the same. 

## What works?
A decent amount of software has dropped Windows 7 support over the last few years. To name a few:
- NVIDIA and AMD are no longer producing drivers.
- Steam has dropped support as of January 2024.
- Chrome has dropped support as of version 109.
- Firefox has dropped support, however they still maintain 115 ESR.
- Wallpaper Engine has dropped support for Windows 7.

### Games
As drivers age, so does compatibility with more modern titles. Windows 7 does support fairly recent graphics drivers, but as time passes they will slowly become less compatible. DX12 is supported in some titles, but many titles do not support 7 at all. 

You can utilize the WineD3D DLLs to translate DirectX to OpenGL if you want to play around, and there also is DXVK to translate DirectX to Vulkan if your GPU supports it.
