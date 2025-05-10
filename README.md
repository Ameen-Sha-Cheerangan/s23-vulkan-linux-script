# S23/S23+/S23U Vulkan Rendering Tool (Linux)

A simple menu-driven Bash script to force Vulkan rendering on any Samsung Galaxy S23 variant via ADB from Linux.  
Tested by the author on S23U, and based on community recommendations, this tool may improve performance, reduce device heat, and extend battery life.  
**All changes are temporary and revert on device reboot.**

---

## Features

- Easy menu-driven interface with safety warnings and notices
- Forces Vulkan rendering via ADB
- Offers two modes for applying Vulkan:
      Normal mode: Only restarts key system apps (recommended for most users; avoids most issues)
      Aggressive mode: Stops all apps and relaunches previously running apps and widgets (may cause side effects; see Known Issues)
- Optionally: Launch all apps (not at all recommended; see warnings)
- Blacklist apps from Game Driver (based on [Reddit recommendation](https://www.reddit.com/r/GalaxyS23Ultra/comments/1kgnzru/comment/mr0qdd4/))
- Clear instructions and user prompts

---
## Vulkan Modes
When you select "Switch to Vulkan", you will be prompted to choose how aggressive the script should be when stopping apps:

- Normal Mode (Recommended):
      Only restarts key system apps (SystemUI, Settings, Launcher, AOD, Keyboard).
      This mode avoids the issues listed below and is suitable for nearly all users.

- Aggressive Mode (Read the issues(section : System-Wide App Restart Issues), I didn't face it because I don't use them, so I use Aggressive mode):
      Force-stops all apps and relaunches previously running apps and widgets.
      This mode may cause the side effects described in Known Issues.      
      Recommended only if you need Vulkan applied to every app immediately.

---
## Requirements

- Linux PC
- [ADB](https://developer.android.com/tools/adb) installed (usually pre-installed on most Linux distros)
      Ubuntu - (`sudo apt-get update && sudo apt-get install android-sdk-platform-tools gawk grep coreutils`)
      Fedora/RHEL/CentOS - (`sudo dnf install android-tools gawk grep coreutils`)
- Samsung Galaxy S23/S23+/S23U
- USB Debugging enabled on your phone (`Settings > Developer Options > USB Debugging`)
- A suitable USB cable for connection

---

## Installation / How to switch to Vulkan
Clone the repository (do this once):
`git clone https://github.com/Ameen-Sha-Cheerangan/s23-vulkan-linux-script.git`

`cd s23-vulkan-linux-script`

**Running (repeat after every device restart):**

`sh opengl-to-vulkan.sh`

Follow the on-screen menu instructions.

---



## ⚠️ Known Issues

This tool is community-driven and experimental. Below are known issues reported by users or observed during testing. This list may expand as more feedback is received.


### 🔸 Vulkan Rendering Issues

- **Visual Artifacts**  
  Some users may experience visual glitches or artifacting when Vulkan is enabled. While Adreno GPUs in the S23 series usually handle Vulkan well, your experience may vary.

- **App Compatibility**  
  Not all apps will run properly under Vulkan. The majority do, but exceptions exist due to incomplete support from Samsung and app developers. There is no workaround—Samsung must adopt Vulkan across models, and developers must support it fully.

### 🔸 System-Wide App Restart Issues

- **Default App Resets**  
  After a system-wide app stop, default apps such as your browser or keyboard may be reset to Samsung defaults.

- **Loss of WiFi Calling / VoLTE**  
  Some users reported losing WiFi-Calling or VoLTE after restarting all apps.  
  **Fix**: Go to **Settings > Connections > SIM manager**, then toggle SIM 1/2 **off and back on**.  
  *Credit: Reddit users [Fun-Flight4427](https://www.reddit.com/user/Fun-Flight4427) and [ActualMountain7899](https://www.reddit.com/user/ActualMountain7899)*

- **Aggressiveness Profile Note**  
  Using the "Aggressive" profile when stopping apps increases the chance of the above issues.  
  For fewer side effects, use the "Normal" profile when prompted by the script.

### 🔸 Additional Notes

- These issues are **not bugs in the script** itself but rather limitations of system behavior when Vulkan is forced and apps are restarted.
- All changes made by the script are **temporary** and will **reset on device reboot**.
---

## Uninstall / Switch Back to OpenGL

To revert your device back to OpenGL rendering, **simply restart your phone**.  
No files or settings need to be removed-rebooting the device will reset the GPU renderer to its default (OpenGL).


---

## Warnings

- **All changes are temporary!** Vulkan rendering will reset after a device reboot.
- **Launching all apps is NOT recommended!**  
- If you do **not** relaunch all apps, some notifications from important apps may be delayed until you open them manually.
- The blacklist feature is based on a Reddit user's recommendation and may not work for everyone.


---
## Standard Disclaimer (Just in Case!)

This script is provided for your convenience.  
I've tested it extensively on my own device and haven't seen any issues,  
but just to be safe (for both of us!), I'm including this notice:

- It makes changes to system settings. Please use responsibly.
- If you have any concerns, consider backing up your data first.
- Please do not use this tool for any harmful or inappropriate purposes.
- By using this tool, you accept responsibility for your actions.

While issues are very unlikely, always proceed with care.  
The author is not responsible for any unexpected issues, data loss, or device instability that may arise from use of this tool.  
This is not an official Samsung or Google product.

---

## Credits

- Original Windows script and concept: https://github.com/popovicialinc/gama
- Game Driver blacklist workaround suggested by [Swimming_Minimum6147](https://www.reddit.com/r/GalaxyS23Ultra/comments/1kgnzru/comment/mr0qdd4/) on Reddit
---

## How to Check if Vulkan is Active

To verify that Vulkan rendering is enabled:

1. **Open Developer Options** on your device.
2. **Enable GPUWatch.**
3. **Open any app** (for example, the Dialer).
4. GPUWatch will display an overlay-look for the renderer information.
   - If Vulkan is active, it will show something like: **Vulkan Renderer (skiavk)**

This is the easiest way to confirm that Vulkan is running on your Galaxy S23/S23+/S23U device.

---
## FAQ

### What is Vulkan, why should I switch to it?

Vulkan is a modern graphics API that offers more efficient, low-overhead access to your device’s GPU compared to OpenGL. Switching to Vulkan can improve performance, reduce device heat, and extend battery life as reported by reddit users in S23 Ultra reddit community.

### Why is there a "Launch All Apps" option?

This option is included because it is a common practice in other Vulkan-enabling scripts for Samsung devices. In practice, you rarely need to launch all apps after forcing Vulkan. Most users will not benefit from this step, and it may cause unnecessary battery drain or device warmth. It is included for completeness and for advanced troubleshooting only.

### I see error related to "user 150" in the output. Is this a problem?

No, this is expected and harmless. This message appears because some apps-such as those inside Samsung Secure Folder or other secondary user profiles-cannot be controlled by ADB shell commands unless the device is rooted. The shell user (used by ADB) only has permission to control apps for the main device user (user 0), not for additional users like user 150 (which is typically Secure Folder). Your main device user (user 0) is still fully handled by the script, and this message can be safely ignored

---
## Issues

If you find any issues or have suggestions, please [open an issue](https://github.com/Ameen-Sha-Cheerangan/s23-vulkan-linux-script/issues).

If you found this tool helpful, please consider giving it a ⭐ on [GitHub](https://github.com/Ameen-Sha-Cheerangan/s23-vulkan-linux-script)!


---
## License

MIT License. See [LICENSE](LICENSE) for details.
