# Steam on Windows XP
This is a quick guide on how to get the latest version of Steam operating under Windows XP.

## OS Information
I have used this setup when creating this guide:
- VMware Workstation 17
- Windows XP Pro x64 SP2 (fully updated)
- .NET and MSVC++ installed

## Install Steam
**DO NOT** use the Steam installer from the main webpage. I have found this installer to be unreliable. It is best to install the latest compatible version for Windows 7 accessible [here](https://archive.org/details/steam_12-31-2023).

## ProxHTTPSProxy
After Steam is installed, you need to install [this](https://storage.levelleap.com/nina/clients/msnp/tools/ProxHTTPSProxy_Setup.exe). I really am not sure why it is needed but it allows Steam to be able to access the internet correctly. Without this you will have issues signing in and won't be able to download games.

After downloading and installing it, you will need to open its Program Files x86 directory. In there, run ``ProxHTTPS Cert Install.exe``. Wait a few seconds. Then open a Command Prompt in that directory, and run ``ProxySwitch.BAT`` and give it argument A. It would look as such in CMD:
``ProxySwitch.BAT A``

After that, run ``ProxHTTPSProxy_PSwitch.exe``. This will start the proxy. It will launch on startup.

**IMPORTANT**:
Chromium based browsers will from now on complain that websites are using HSTS and will refuse to let you access them. I have not encountered this issue with Firefox based browsers. I have tested both Firefox 115 ESR and Firefox 128 ESR, I have found 128 ESR to work better in some cases.
> *If you use 128 ESR, you should enable system title bar in customization settings.*

## Running Steam
Set the Steam executable compatibility to Windows 7. After this, run the executable.

### Launch Options
I recommend using these launch options, which improve performance of the Steam client:

``-cef-disable-d3d11`` - Disables DirectX 11
``-cef-disable-gpu-compositing`` - Disables GPU Compositing
``-cef-disable-gpu`` - Disables GPU acceleration
``-cef-disable-sandbox`` - Disables Chromium Sandbox
``-cef-disable-occlusion`` - Disables Chromium Occlusion
``-cef-ignore-certificate-errors`` - Ignores Chromium certificate errors
``-disable-winh264`` - Disables H264
``-enable-desktop-gl-fallback`` - Enables OpenGL fallback
``-forceservice`` - Forces Steam service on Admin accounts
``-no-cef-sandbox`` - Disables Chromium Sandbox (2)
``-no-dwrite`` - Uses GDI for font rendering instead of DWrite
``-nofriendsui`` - Disables FriendUI from showing automatically
``-opengl`` - Enables OpenGL rendering

### My Two Cents
I have noticed a lot of weird networking issues in OCA. I suspect that the networking stack has some broken procedures under the latest OCA version. I suspect that it is possible UDP networking is a little messed up under OCA.

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
