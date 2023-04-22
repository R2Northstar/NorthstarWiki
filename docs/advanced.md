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

## Setting levels using console commands <a href="#set-level" id="set-level"></a>

With everything unlocked, there is no need to set your level to a higher level, but some users may stil want to do so. In order to this, you'll need to open the console and type in the relevant commands. Both of these require `sv_cheats 1` to be enabled on the server you're playing on, easily done by using `sv_cheats 1` in the console in a private match. Avoid setting your xp number to higher than 472, as doing so may cause a crash or mess up your Northstar save data.

`script GetPlayerArray()[0].SetPersistentVar("gen", insertGenCount)` this command sets the Generation level of the player. You want to replace `insertGenCount` with the number you want.

`script GetPlayerArray()[0].SetPersistentVar("xp", insertXpCount)` this command sets the xp count of the player (change this wording pls). You want to replace `insertXpCount` with the number you want.

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

Method 1:

Method 1 saves ~14.5GB, and allows you to verify your game files.

Open up Powershell and run it as administrator, then copy and paste the following command. When using this command, you need to edit the `Install Dir` to match the path to your [titanfall2 directoy](installing-northstar/troubleshooting.md#game-location). You want to keep the quotation marks around it in place.\
```
#Requires -RunAsAdministrator
$tf2 = (Get-ItemProperty -Path "HKLM:\SOFTWARE\Respawn\Titanfall2")."Install Dir"
Get-ChildItem $tf2 -Filter "*.starpak" -Recurse |
    Where-Object Length -GT 1mb |
    ForEach-Object FullName |
    ForEach-Object { & compact /EXE:XPRESS16K /C /F "$_" | Select-String -SimpleMatch "[OK]" }
```

Method 2:

Method 2 saves ~(bruh i gotta test this on my own machine with 2mb/s download fml)GB, however _does____not___ allow you to verify the games files. 

To use this method, you need to go do [this GitHub repo](https://github.com/pg9182/tf2vpk#examples), go to the `Releases` section on the side, download the click on and download the `zip` option, then extract the `zip` folder to your preffered place, downloads will work just fine.

From here, open up a terminal and follow the directions on the GitHub page as to what you should enter to reduce the storage space. The first option is what most users will want to use, while the second option is only for server hosters so they only have to use the required files for a Northstar server, further reducing space.

For this, you want to replace `/path/to/Titanfall2/vpk` with the path to your titanfall2 directory, targeting the vpk directory (just type in your titanfall2 folder, then add `/vpk` after it)
