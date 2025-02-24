# Steam on Windows XP
This is a quick guide on how to get the latest version of Steam operating under Windows XP.

## OS Information
I have used this setup when creating this guide:
- VMware Workstation 17
- Windows XP Pro x64 SP2 (fully updated)
- .NET and MSVC++ installed

## Install Steam
**DO NOT** use the Steam installer from the main webpage. I have found the default installer to be unreliable. It is best to install the latest compatible version for Windows 7 accessible [here](https://archive.org/details/steam_12-31-2023).

## ProxHTTPSProxy
After Steam is installed, you need to install [ProxHTTPSProxy](https://storage.levelleap.com/nina/clients/msnp/tools/ProxHTTPSProxy_Setup.exe). It is needed to fix issues with Steam network connectivity.

### Installing ProxHTTPSProxy
ProxHTTPSProxy has some important steps you need to take after downloading and installing it:
1. Navigate to the ``C:\Program Files (x86)\ProxHTTPSProxy`` directory.
2. Run ``ProxHTTPS Cert Install.exe`` and wait a few seconds.
3. Open a Command Prompt in the current directory.
4. Run ``proxyswitch.bat A`` exactly as stated.
5. Run ``ProxHTTPSProxy_PSwitch.exe``. This will start the proxy immediately.

You will not need to do this on every startup, this sets up the system to use the proxy. The proxy app will automatically start upon login from this point forward.

**IMPORTANT**:
Chromium based browsers will from now on complain that websites are using HSTS and will refuse to let you access them. I have not encountered this issue with Firefox based browsers. I recommend Firefox ESR 128.
> *If you use 128 ESR, you should enable system title bar in customization settings.*
> *There is also a bug where Firefox will hang after you close it, requiring it to be terminated in Task Manager.*

## Running Steam
Set the Steam executable compatibility to Windows 7, or else it will try to update itself to a version that is incompatible and/or complain that it is not supported on Windows XP anymore.

### Launch Options
I recommend using these launch options, which improve performance of the Steam client:

- ``-cef-disable-d3d11`` - Disables DirectX 11
- ``-cef-disable-gpu-compositing`` - Disables GPU Compositing
- ``-cef-disable-gpu`` - Disables GPU acceleration
- ``-cef-disable-sandbox`` - Disables Chromium Sandbox
- ``-cef-disable-occlusion`` - Disables Chromium Occlusion
- ``-cef-ignore-certificate-errors`` - Ignores Chromium certificate errors
- ``-disable-winh264`` - Disables H264
- ``-enable-desktop-gl-fallback`` - Enables OpenGL fallback
- ``-forceservice`` - Forces Steam service on Admin accounts
- ``-no-cef-sandbox`` - Disables Chromium Sandbox (2)
- ``-no-dwrite`` - Uses GDI for font rendering instead of DWrite
- ``-nofriendsui`` - Disables FriendUI from showing automatically
- ``-opengl`` - Enables OpenGL rendering
- ``-tcp`` - Forces TCP connectivity (this is deprecated and probably won't work in the future)

### My Two Cents
I have noticed a lot of weird networking issues in OCA. I suspect that the networking stack has some broken procedures under the latest OCA version.

## Steam Configuration
After you get Steam running, you should go into the settings of Steam and change these settings. This should help significantly with performance:

- Low Performance Mode
- Low Bandwidth Mode
- Disable GPU Acceleration
- Disable Smooth Scrolling
- Disable HW Accelerated Video Decoding
- Disable Community Content
- Turn off Open on Startup


> Guide made with ❤️ by sunryze
