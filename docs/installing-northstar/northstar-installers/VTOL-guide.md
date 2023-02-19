# VTOL Information
VTOL is a mod manager for installing and managing mods for the Northstar client made for Titanfall 2. You can find links to install it on the [Northstar Website](https://northstar.tf), or on [VTOL's GitHub page](https://github.com/R2NorthstarTools/VTOL).

# Main Menu
![vtol-main-window](https://user-images.githubusercontent.com/70904206/219880640-b50e8ff4-4db1-4bb9-8bd2-929582783083.png)
**The Main Menu of VTOL is where you'll probably spend most of your time.**

This menu has a lot of useful information, such as the version of VTOL you have, the version of Northstar you have, if the Master Server is online, whether EA App/Origin are currently open, and a place to set your game path. 

## Version Numbers
You can see what version of VTOL/Northstar you have in the top left corner of the VTOL window.
![version-numbers](https://user-images.githubusercontent.com/70904206/219880616-eed5a09a-0b6f-482b-9274-f64b4191a6e4.png)

## Master Server/EA or Origin online
These small tabs near the middle of the VTOL window show you whether the Master Server for Northstar is currently online, and if EA or Origin is running properly on your computer. If the EA/Origin tab is red, solving that will be covered later (See: Settings section later on).\
If you are unsure if you have EA or Origin, you have EA.
![server-status](https://user-images.githubusercontent.com/70904206/219880687-1a2eaa8f-4f81-4d55-8af4-286b85f803b1.png)

## Northstar Installation/Locate Titanfall 2 Install
The final parts of the Main Menu are at the bottom, showing your game's directory with a button to Locate Titanfall 2 Install, a small button next to this, and a button reading "Update +Northstar"
![northstar-installation-info](https://user-images.githubusercontent.com/70904206/219880707-ed92e770-5784-4ff2-9414-36b4de3f2dbc.png)

# Installation Via VTOL
VTOL handles most things automatically, but it still may require minimal setup for some users.\
![northstar-installation-info-locate](https://user-images.githubusercontent.com/70904206/219880765-0fce4934-33e0-4aef-900b-c18edfb9bc1e.jpg)
Something you might have to do manually is locate your Titanfall 2 Install. You can do this by pressing the button of the same name on VTOL, and navigating to your Titanfall 2 directory (If you're unsure of what your game path is, check out the Northstar wiki's [Default Directories](https://r2northstar.gitbook.io/r2northstar-wiki/installing-northstar/troubleshooting#game-location) section)

After doing this, Northsar should automatically install. If not, the button at the bottom will read "Install Northstar". Let VTOL install Northstar, and you should be good to go. Once installed, this button will turn into the "Update +Northstar" shown in the screenshot earlier, which you can use to update without having to reinstall.

# Launching Northstar via VTOL
![launch-northstar](https://user-images.githubusercontent.com/70904206/219882248-0997abb1-4cf6-4f46-b88a-88de4f65dac2.png)\
Assuming you've followed everything up to this point, you should be set to hit "Launch Titanfall 2 Northstar" and play on Northstar's servers. If you encounter an error like a crash, Northstar will create a log file in the "titanfall2/r2northstar/logs" directory. You can look at this log yourself, or send it on the [Northstar Discord server](https://discord.com/invite/northstar) and someone can try to look at it and help you.

# Additional Mods/Settings

## Tab List
![vtol-settings](https://user-images.githubusercontent.com/70904206/219880914-f537fa8e-2596-4bd8-8689-5786f21d189e.png)\
The furthermost left side of VTOL has a list of tabs you can use for several different functions.\
To expand the smaller version of the tab list, press the button with 3 bars as shown below\
![vtol-settings-expand](https://user-images.githubusercontent.com/70904206/219881049-be071e8e-9182-4cd5-93ff-7cf811de15b5.jpg)\
**NOTE: This guide will not be including the "Home" button as a tab when describing this list. When it says the first tab, it means the first tab underneath the home button**
## Installed Mods List
![vtol-mods](https://user-images.githubusercontent.com/70904206/219881144-c8e83838-e59c-4214-b261-b25b72abf9f1.png)

The first tab of VTOL is the "Mods" tab. This is a list of your currently installed mods, with the ability to disable any of them quickly.

You can also right click on a specific mod to get the option to either delete it, or look at the mod's information (Mod Name, Author Name, Description, etc.)\
![right-click-vtol-mods](https://user-images.githubusercontent.com/70904206/219881212-a13f29e5-6d6b-48ae-a1d1-6c422b3c908e.png)


## Installing Mods Via VTOL
![vtol-mods-browser](https://user-images.githubusercontent.com/70904206/219881459-14f69243-9813-4b1e-814b-2925f5ee72dc.png)

VTOL has a built in browser for searching [Northstar's Thunderstore page](https://northstar.thunderstore.io/) (the website where most Northstar mods get uploaded to), located at the second tab "Browse" on the tab list. You will see the newest uploaded mods here by default, which you can change by applying filters (Note: The sorting is by default Low-High for filters. You can change this by pressing the button with an arrow next to the filters button, making it High-Low)

VTOL also has support where all you need to do is drag and drop a mod downloaded from the Thunderstore page onto the Mods tab (the second tab on the left side) to automatically install the mod

## Settings
![vtol-settings-tab](https://user-images.githubusercontent.com/70904206/219881503-cf1ec853-4589-454d-ab6e-0c1eb00e9c0a.png)

On the way bottom of the tab list, there is a button to open settings for the VTOL manager. You will want to keep most of these on default, but change them as you wish. It is normal for the "Restart_As_Admin" button to appear untoggled. This is also where you can tick "Enable_EA_APP_Usage" to make the client work better with the EA app, assuming you have it and not Origin

## Skins
![vtol-skins](https://user-images.githubusercontent.com/70904206/219881515-e68c156e-a2cf-45ff-ba15-fdd0b321cc85.png)

The third settings tab on VTOL is the "Skins" tab. VTOL has support for skins formatted for an older version of Northstar, normally requiring an extra tool. All you need to do is drag the folder of one of these old style skins onto the Skins screen to install it automatically.

## Server
![vtol-server](https://user-images.githubusercontent.com/70904206/219881530-baa4c77d-8f04-4ffc-bada-9fbb7c478847.png)

The fourth tab on VTOL is the "Server" tab. This section allows you to add Launch Arguments to your client or dedicated server. Note that this adds Launch Arguments to change what Northstar does when it launches, not to launch Northstar itself. A way you can do this is by adding [launch arguments](https://r2northstar.gitbook.io/r2northstar-wiki/installing-northstar/troubleshooting#launch-opts) via the store you own the game on and launching through there.

For the dedicated server option, you can scroll through this tab to set many different options for a server which can be found on the Northstar Wiki's [Server Hosting Guide](https://r2northstar.gitbook.io/r2northstar-wiki/hosting-a-server-with-northstar/basic-listen-server)

# Tools
![vtol-tools](https://user-images.githubusercontent.com/70904206/219882500-79bb66bb-1de1-4f91-ac0c-a5ed40d63ab3.png)
The fifth tab called "Tools" is meant to help those trying to create mods for Northsar. 

## ThunderStore Packer
![vtol-thunderstore-packer](https://user-images.githubusercontent.com/70904206/219881604-81f00c75-a000-4a01-bdb5-1683f70249c4.png)
The first screen is an area where you can locate your mod folder, and easily set up things such as the Name, Description, and Icon to be shown on the Thunderstore page when you go to upload your mod.

## Skin Tool
![vtol-skintool](https://user-images.githubusercontent.com/70904206/219881620-ce45b403-0f24-4ce4-a5f7-0548705dd513.png)
The second screen is an area where you can drag and drop images to the different maps of a skin to make your own skin. This is an implementaion of the [skin tool](https://github.com/zxcPandora/Titanfall2-SkinTool).

## Advocate
![vtol-advocate](https://user-images.githubusercontent.com/70904206/219881630-79ed35b9-1590-4bf6-a093-67049fd48d89.png)
The third screen is an implementation of Spoon's [Adovate Tool](https://github.com/ASpoonPlaysGames/Advocate), where you can convert an old style skin mod to a mod that can be installed by everyone like a normal mod. Please give credit to the original skin owner while doing this. (If confused, following the earlier link to Github describes how to set up Advocate)

## External Tools
![vtol-external-tools](https://user-images.githubusercontent.com/70904206/219881655-f6a44137-6daf-49b1-9daf-aebbc3e44da4.png)
The fourth screen lists a lot of commonly used tools by modders to help create mods easier. You can get more info about each tool by clicking the information icon in the top right of the image for each respective tool.

## About
![vtol-about](https://user-images.githubusercontent.com/70904206/219881669-3c957167-8ac7-46f2-8ad8-3dd71960c1d3.png)

The last section of the VTOL client is the 6th tab of VTOL, the "About" section. This screen shows you what VTOL can do, as well as a button to configure updates, and a button to check for updates for the VTOL client.

# Credits 
[Juicy](https://github.com/BigSpice) for creating and upkeeping the VTOL Manager, as well as helping explain some things that I hadn't seen before
