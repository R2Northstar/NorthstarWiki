# x64dbg

{% hint style="warning" %}
If you are not experienced with x64dbg it its recommended to use [Visual Studio](visualstudio.md).
{% endhint %}


## Windows

* Download [x64dbg](https://x64dbg.com/)
* Extract the `release` folder somewhere on your PC
* Download the latest relase of [SycllaHide](https://github.com/x64dbg/ScyllaHide/releases/latest)
* Merge the contents of the `x64dbg` folder into the previously extracted `release` folder
* Run `x96dbg.exe`
  * You may receive a Windows SmartScreen prompt, x64dbg snapshots are not signed and will always cause these prompts
  * When running for the first time it will ask you some questions. After this is complete rerun the executable.
* Select `x64dbg` in the Launcher    
![](../../images/debugger-x64dbg-launcher.png)

* Do make debugging easier it is suggested to change your settings to the following:
  * Keeping System Breakpoint enabled is optional but useful    
![](../../images/debugger-x64dbg-events.png)

  * Skipping INT3 stepping is recommended to prevent generic breakpoints from stopping the program    
![](../../images/debugger-x64dbg-engine.png)

  * Make sure to select the exception before disabling breaking. If you are debugging a C++ Exception you need to ignore common exceptions that occur during runtime    
![](../../images/debugger-x64dbg-exceptions.png)

* Open `NorthstarLauncher.exe` in x64dbg
* You are now free to debug Northstar

## Linux

{% hint style="warning" %}
Debugging Northstar under Linux is not trivial due to the direct dependency on
{% endhint %}

Debugging Northstar under Linux is not trivial due to the direct dependency on Origin.

To simplify the use of x64dbg and automate running Origin a community member has created a script.

* clone `https://git.jandroegehoff.de/sentry/ns-gdb`
* run `./nsdbg x64dbg`
  * by default it looks for the steam install for Titanfall 2, you can override that by setting the `TF2_GAME_DIR` environment variabel to the game path
  * Due to compatibility issues with most wine builds, it attempts to run it in proton. If this is undesired append `--compat=wine`