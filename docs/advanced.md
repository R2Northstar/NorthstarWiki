# Advanced Options

## Setting up Mod profiles <a href="#profiles" id="profiles"></a>

Profiles are a way to launch a version of Northstar with specific mods enabled, differing per profile. This is especially useful if you want to [play vanilla using Northstar](advanced.md#vanilla-on-northstar).



## Playing Vanilla via NorthstarLauncher <a href="#vanilla-on-northstar" id="vanilla-on-northstar"></a>

Note that "via NorthstarLauncher" also applies to [launch options](installing-northstar/troubleshooting.md#launch-opts), as launch options just launch the NorthstarLauncher for you. This will not work for mod managers however, as they do not inherit launch options needed to launch Vanilla.

The reason behind doing this is that Northstar has several security fixes that Vanilla does not have, however these are not *neccesary*. The odds you get hacked playing vanilla are close to zero, and there are no reports of people being genuinely hacked by playing Vanilla, the worst reports being that they've been taken offline temporarily due to DDOS attacks.

This method assumes you're launching Northstar via Titanfall 2 on EA/Steam/Origin using launch options

1. Go to the main menu of Northstar 
2. Click `"Mods"` on the bottom of the menu
3. Disable **ALL** of your mods
4. Close Northstar
5. Add `-norestrictservercommands` as a [launch option](installing-northstar/troubleshooting.md#launch-opts)
6. Launch Titanfall 2 and you should be able to play on vanilla servers using Northstar's security fixes

**TO PLAY ON NORTHSTAR AGAIN**

1. Go to your [titanfall2 directory](installing-northstar/troubleshooting.md#game-location)
2. Go into your `R2Northstar` folder


Alternatively, if you don't want to disable your mods or delete `enabledmods.json` every time you want to switch between vanilla and Northstar, set up a [Vanilla profile](advanced.md#profiles) and launch through that

## Shrinking Titanfall 2's size

There are multiple methods which you can use to reduce Titanfall 2's size on your disk. The first method saves ~14.5 GB, and still allows you to verify your game files should something go wrong. The second method will not allow you to verify your game files.

Method 1:

In your operating system's terminal, you will need to copy and paste the following command:\
`#Requires -RunAsAdministrator
$tf2 = (Get-ItemProperty -Path "HKLM:\SOFTWARE\Respawn\Titanfall2")."Install Dir"
Get-ChildItem $tf2 -Filter "*.starpak" -Recurse |
    Where-Object Length -GT 1mb |
    ForEach-Object FullName |
    ForEach-Object { & compact /EXE:XPRESS16K /C /F "$_" | Select-String -SimpleMatch "[OK]" }`

When using this command, you need to edit the `-Path "HKLM:\SOFTWARE\Respawn\Titanfall2"` to match the path to your [titanfall2 directoy](installing-northstar/troubleshooting.md#game-location)
