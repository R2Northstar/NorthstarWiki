# x64dbg

{% hint style="warning" %}
if you are not experienced with x64dbg it its recommended to use [Visual Studio](visualstudio.md)
{% endhint %}


## Windows

* Download [x64dbg](https://sourceforge.net/projects/x64dbg/files/latest/download)
* Extract the `release` folder somewhere on your PC
* Download the latest relase of [SycllaHide](https://github.com/x64dbg/ScyllaHide/releases/tag/v1.4)
* Merge the contents of the `x64dbg` folder into the previously extracted `release` folder
* Run `x96dbg.exe` and select `x64dbg` or run `x64/x64dbg.exe`

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