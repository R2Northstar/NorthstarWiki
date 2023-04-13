# Advanced Options

{% hint style="warning" %}
This is a section detailing the more advanced parts of using Northstar, with some of them having a chance to potentially break your install if done improperly. 
{% endhint %}

## Setting up Mod profiles <a href="#profiles" id="profiles"></a>

Profiles are a way to launch a version of Northstar with specific mods enabled, differing per profile. This is especially useful if you want to [play vanilla using Northstar](advanced.md#vanilla-on-northstar).

A simple "vanilla" profile can be created using a `.bat` file, without needing to fully make an additional mods folder. You can do this simply by creating a `.bat` file inside of your titanfall2 directory (you can name it however you want), and putting in `NorthstarLauncher.exe -norestrictservercommands -profile=R2Vanilla`. This tells the NorthstarLauncher to not restrict server commands, which is what normally disables the Vanilla multiplayer servers on Northstar to lower confusion, and tells it to use the `R2Vanilla` profile, which, as it doesn't normally exist, will launch Northstar with no core mods enabled, allowing you to easily play on Vanilla using Northstar's security fixes.

Double clicking the `.bat` or right clicking on it and hitting `open` will launch the vanilla profile.



Setting up a profile with a second set of mods has a similar process with the `.bat` creation, but requires more setup.

The first thing you want to do while creating a new profile is have a Northstar release version downloaded and ready to be used. You will only need the `R2Northstar` folder from this second version, as the rest of the `NorthstarRelease.zip` doesn't matter to creating additional profiles

You'll want to rename the `R2Northstar` folder to whatever you prefer it to be called, such as `R2NorthstarNoMods` if you'd like to have a normal Northstar installation without using additional mods. These profiles act entirely independently from the other folders, meaning you can use a mod in a folder without it affecting any others. The only downside to this, however, is that they must all be updated independetly when a Northstar update is released. You can install any mods that you would like to `YourProfileName/mods`, and they will load when launching it, though, just like core mods, these will all need to be updated independently. 

In order to create the `.bat` to launch this profile, you'll need to first create a `.bat` file inside of your titanfall2 direcotry, and name it whatever you would like. Inside of this `.bat` file, you'll want to put in `NorthstarLauncher.exe -profile=PROFILE FOLDER NAME HERE`, replacing all of `PROFILE FOLDER NAME HERE` with the name that you gave the folder you installed your mods to. Double clicking or right clicking on the `.bat` file then hitting `open` will launch Northstar with the assigned profile.

You can set up profiles even more advanced by setting up a way to use Steam to launch multiple different profiles from their newer launch menu that appears when you can launch a game in more ways than one. This is also covered [here](installing-northstar/basic-setup.mdbasic-setup#adding-alternate-launch-option-for-steam), and can be set up for profiles by simply adding the `-profile=PROFILE FOLDER NAME HERE` to the arguments of the new option for NorthstarLauncher, as seen below

![SteamEdit using Northstar Profiles](images/steamedit-profiles.png)

## Playing Vanilla via NorthstarLauncher <a href="#vanilla-on-northstar" id="vanilla-on-northstar"></a>

It is recommended that you [set up a vanilla profile](advanced.md#profiles) instead of disabling all of your mods and using `-norestrictservercommands` as a launch option, however if you wish to only play vanilla using this method and would rather not set up a profile, you can do the following.

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
2. Open your `R2Northstar` folder
3. Delete `enabledmods.json`
4. Launch Northstar

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
