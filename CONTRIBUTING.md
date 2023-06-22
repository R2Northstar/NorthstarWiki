# Contributing

In case you feel like something is out of place, not accurate, biased, or if you just want to contribute, please [open a new issue](https://github.com/R2Northstar/NorthstarWiki/issues/) or [make a pull request](https://github.com/R2Northstar/NorthstarWiki/pulls) to our wiki:\
[https://github.com/R2Northstar/NorthstarWiki](https://github.com/R2Northstar/NorthstarWiki)

# Helping

This section is meant mostly for those that will be actively helping others in the Northstar Discord server or otherwise. If you've somehow stumbled upon this page trying to fix an issue first, you should try checking the [troubleshooting page](docs/installing-northstar/troubleshooting.md).

As of {ENTER DATE HERE WHEN SPECTRE GETS ADDED}, Cyn(cooldudepugs)'s Discord bot [Spectre](https://github.com/CooldudePUGS/Spectre) was added to Northstar's Discord. This bot tries to automatically redirect users to opening a ticket in the `#help` channel, and automatically replies to some messages regarding issues with the game, however it cannot and will not catch all cases, even of basic help. When helping a user, please try to move them to the `#help` channel as well to keep public channels less cluttered.

Arguably the most important things to know as a helper are the ability to read logs and deal with users that don't read the wiki (90% of tickets are solutions solvable by checking the wiki. There is a pretty high chance that even if the user says yes, they read the wiki, that they didn't or didn't find their issue on there)

Reading logs is a little tougher however, but once you get the basics down you can easily diagnose issues in a few seconds after opening a log. You can use `/tag id:logs` to inform users how to properly send a log in a Discord channel. Generally, when reading a log there are a list of things you want to look for. 

This section will first go over extremely common issues and their tags, then the basics of using the help bot for ticket commands, and then some overview and specific examples for reading logs.

## Common issues and their tags

In the Northstar Discord server, a massively used device to help end users is the help bot. A lot of the common issues and questions that come up have tags for them on the Discord. To use a tag from the help bot, you want to use the slash command `/tag`. You can either type `/tag id:{TAG ID HERE}` or let the bot autofill the tag for you after typing `/tag` and selecting the tag id from the list then sending the command. Note, you can't reply to a user while using a slash command, so try to reply to the bot while pinging the person and informing them that they should follow the provided section.

Here, this guide will go over common issues and their tag id's, mostly trying to have the more used tags near the top.

"Couldn't find player account/Invalid Masterserver Token (when the Mastserver isn't down)": `/tag id:playernotfound` (It's named this as the error used to simply say `Player Not Found`. The linked wiki section contains all known fixes)

"Failed creating log file!/Mod manager not installing mods properly": `/tag id:ea-app` (It's named this as this almost always is the fault of EA App's default install path not being writable. Note that antivirus programs APART from Windows Defender can also cause Mod managers to not properly install Northstar/mods)

"My controller isn't working": `/tag id:controller` (This links to the specific section on adding launch options/Northstar's `.exe` file to Steam to use it's controller support, as well as mentioning DS4Windows as a backup)

"How do I play with friends?": `/tag id:host-listen` (This goes over hosting a listen server, which is what hitting `Private Match` in Northstar does. Try to inform the user that they can't invite friends normally and have to do this. If they ask about port forwarding, ask them to Google how to do it for their specific router as it tends to differ, sometimes heavily, from router to router)

"How to play co-op?": `/tag id: coop` (This gives a detailed mini explanation on how to install the co-op mod, and host a server to run it. Try to inform the user that it's still heavily WIP and has some issues. Listen servers don't allow for joining mid game; to do this, they must host a dedicated server with the "coop patches" mod provided with this tag)

"How to play Frontier Defnse?": `/tag id:fd` (This is called fd as it's the abbreviation for **F**rontier **D**efense. This also goes over how to install and set up Frontier Defense, like co-op's tag)

"How do I use x Mod manager?": The 3 "main" mod managers all have guides. `/tag id:{INSTALLER NAME HERE}-guide` links to the specified installer's guide

"How do I (manually) install Northstar?": `/tag idd:manual-install` (This goes over installing, extracting, and replacing the files as well as giving a video guide)

"How do I manually install mods?": `/tag id:install-mods` (Try to inform the user that they should also make sure to check for mod dependencies when manually installing mods)

"How do I verify files?": `/tag id:verify-files` (This links to a section detailing verifying for all 3 platforms)

These are most of the most common and most used tags for helping people. More exist, however these are the "main" ones helpers should know

## Ticket channel commands

The tickets have a fairly straightforward way of operating. When a user clicks on a button to open a ticket, they're greeted with the following screen:\
![image](https://github.com/CooldudePUGS/NorthstarWiki/assets/70904206/7f03abf5-4dff-4855-8190-028ba08258e8)

They will fill this out with information which will later be shared in their ticket as a message sent as an embed by the help bot. This will be the first message in the channel and will look something similar to this:\
![image](https://github.com/CooldudePUGS/NorthstarWiki/assets/70904206/90dd1df6-d2fb-4c93-bdbb-7b295f36406a)

Note the buttons below the embed. Hitting `Close` will close the ticket without a reason for closing it. `Close with reason` will let you give a reason as to why you closed the ticket. `Claim` allows you to "claim" a ticket and lets other helpers know that you'll be solving the ticket. This doesn't usually get used for Northstar, however people can still message in the channel even after it's claimed so don't worry if you accidentally claim a ticket/end up not being able to solve it.

These buttons, however, are not always easy to scroll back up to, especially if the ticket has been open for a while. This is where slash commands come in.

There are 3 major slash commands for tickets. These are `/close`, `/closerequest`, and `/add`.

`/close` by itself will close the ticket immediately, without a reason. Using a slash command however, you can give a reason for closing using the `reason` option for the slash command. 

`/add` will add a normal (non ticket-viewing) user to a ticket. This is useful if, for example, someone who created a mod and can't see the tickets has one of their mods create an error for a user and you can't diagnose it. This is also useful for cases where someone opens a ticket for someone else.

You may have noticed that `/closerequest` has been skipped. That's because there's sort of a "etiqutte" surrounding it.

### General log reading
1. Looking for the error
   
    When reading a log, the errors are generally easy to find. You can usually scroll to the bottom of the log, then look for an error message for script compilation errors, or a crash dump. Note that the crash dump isn't usually all to helpful in itself, however for both crash dumps and script compilations, generally you can look at the areas surrounding it to see what mod is loaded before the error and start from there. Read the specifics for more in depth explanations of each.
   
2. Time and date
 
   If a log doesn't display the time, date, or version of Northstar, tell the user to update their Northstar. If none of these exist, the Northstar install is ancient :)

### Specifics of log reading
1. Script compilation error

     This error generally arises due to a mod installed breaking, not having a valid dependency, or conflicting with another installed mod (sometimes, even core mods!). For these issues, there are two ways you can go about them. If they're issues with mod dependencies, the log will state something like the following

   (Note: These log examples ARE out of date. The error messages, however, have stayed the same or relatively similar.)
   
   This is a specific example of the user not having [Mod Settings](https://northstar.thunderstore.io/package/EladNLG/ModSettings/) installed.\
   ![image](https://github.com/CooldudePUGS/NorthstarWiki/assets/70904206/19e31f35-0289-400f-a7e3-ddeeddcb01e9)
   
   This is a specific example of the user not having [ClientKillCallback](https://northstar.thunderstore.io/package/S2Mods/ClientKillCallback/) installed.\
   ![image](https://github.com/CooldudePUGS/NorthstarWiki/assets/70904206/e36f6922-adbf-4dce-8525-aa8e2091b388)

   For these, have the user install the respective missing dependency if you can tell what it is.

  
   Otherwise, you can have them simply remove/disable the mod causing issues (especially important if the mod is out of date or installing a dependency didn't cause it to work). You can piece together what mod it is by looking at the file name that causes the error (for example, the first screenshot earlier says `ui/hud_revamp_settings.nut` meaning HUD Revamp is causing the issue, and the second screenshot says `s2_wg_overhaul.nut` which means WarGames Overhaul). The file names will not always line up with the exact mod name, and some are named different things entirely. For cases like these, try to check the last loaded folder before the error occurs, such as the following:
   
      Here, we see that a folder named `s2.WarGamesOverhaul` is causing issues. This makes it quite easy to debug what it is. You should also try to search for these on [Thunderstore](https://northstar.thunderstore.io/package/) to see if you can find any abbreviations/shortened names for mods, and what the mod's actual name is.
   
   ![image](https://github.com/CooldudePUGS/NorthstarWiki/assets/70904206/454aa343-ac09-4ed4-ab0d-9465d04551d2)

   Sometimes, the issue isn't a dependency and instead says something completely random. Here we can see that [Mastiff Reactive Skin](https://northstar.thunderstore.io/package/S2Mods/MastiffKillReactiveSkin/) causes a weird error not described so far in the guide. For these, the user should first try to update the mod that's causing the issue. If that doesn't work, follow the part about enabling mods to see what causes the issue if this doesn't fix it.\
   ![image](https://github.com/CooldudePUGS/NorthstarWiki/assets/70904206/746af297-fcaf-436c-8870-d7cefc056765)

   Note that a decent amount of the time, even after solving one of these, more can arise that previously didn't! This doesn't mean that the last thing you/the user tried caused more errors, but it's important to note that more can come up after solving one. This is _especially_ prevalent with manual installers that don't update their mods, then try to install new mods that use newer dependency versions.

3. Crash dumps

     Crash dumps are snippets of information given in logs when Northstar "hard crashes". These dumps aren't generally all too useful for giving you an exact error, however can still hold vital information. Crash dumps tend to look like this:
   
   This part importantly gives a list of loaded mods and their versions.\
   ![image](https://github.com/CooldudePUGS/NorthstarWiki/assets/70904206/d42e9589-72c9-43bc-a7a2-ff42a2bcbaf2)
   
   This part is normally much easier to spot and more recognizable for quickly looking at a log.\
   ![image](https://github.com/CooldudePUGS/NorthstarWiki/assets/70904206/064f3ed8-eca9-4657-ba85-0216eef9a8b5)

   When seeing a crash dump, many things can cause it. However, once again, this is almost always due to one or more installed mods. A lot of the times, however, these are harder to diagnose than a simple compilation error. Generally, if the user disables all but core mods their game works (if not, they should manually delete their core mods and reinstall Northstar, either via a mod manager or manually. Be prepared to explain every step of manually reinstalling if you ask them to do so), and it's then recommended that they enable dependency mods first (e.g. Mod Settings and ClientKillCallback as shown previously) then enable mods in batches of anywhere from 2-4 (depends how many mods they have, use your judgement and recommend a number). This is mostly a safe way to debug absolutely any error with the game as well.
   
4. Multiple crash dumps in one log/Multiple crash messages when launching Northstar

   This is almost always due to the user having multiple sound mods that replace the same sound installed. This is especially prevalent with mods such as [Goofy Ahh Soundpack](https://northstar.thunderstore.io/package/theNon/Goofy_Ahh_Soundpack/) where a _ton_ of sounds get replaced, however it's never stated which ones are. When debugging this, simply ask the user if they have multiple sound mods that replace the same sound installed. If they say no, ask if they have the before mentioned `Goofy Ahh Soundpack` installed. If they do, tell them to disable ALL other sound mods when using it.

   An example of multiple crash messages when launching Northstar:\
   ![multiple crashes](https://github.com/CooldudePUGS/NorthstarWiki/assets/70904206/5c364d61-4bf9-44bf-8b29-e51934bee4ae)

   Multiple crash dumps in one log are either very easy to find, or very easy to skip over. It's especially given away when this is the cause because the log tends to show a crash dump, then continues to load for a while longer (if it's one crash dump near the end of the file and it continues for a couple lines, that's negligible and you should probably focus on normal crash dumps instead)

   An extreme example of multiple crash dumps in a Northstar log:\
   {FINISH THIS LATER, I'LL HAVE TO MAKE A LOG OF THIS MYSELF}

## Contacting us

You are welcome to create an issue at:\
[https://github.com/R2Northstar/NorthstarWiki/issues](https://github.com/R2Northstar/NorthstarWiki/issues)

Alternatively feel free to reach out via Discord:\
[https://northstar.tf/discord](https://northstar.tf/discord)
