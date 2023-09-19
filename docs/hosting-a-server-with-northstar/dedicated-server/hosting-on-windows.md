# Hosting on Windows

## Hardware

{% hint style="info" %}
TODO: If you have experience in hosting Northstar servers and want to share your knowledge, please open a [pull request](https://github.com/R2Northstar/NorthstarWiki/pulls).
{% endhint %}

## Minimum requirements

The current minimum requirements are as follows:

**Requirements per server:**

- 8GB free disk space (5GB of the game and 3 for Origin/EA app)
- 3+ cores (2 might work, though)
- 3GB+ total memory (RAM or swap will do)
- Windows 8.1 

**Per instance:**

- 2GB RAM (this is what's actually used; it does drop to ~1.2GB after a bit)
- 15 Mbps network upload, but 10 is workable, 25 if you want to avoid players getting disconnected when going back to the lobby after a match

**Note:** It is recommended to surpass the listed requirements. Currently the number of available servers covers the daily playerbase more than enough. If you're planning to host public servers for the community it is therefore recommended to either fill a niche (like a gamemode that is so popular that all existing servers are full) or provide a better service than existing hosts (less lag, more stable, etc.).


## Setup

Dedicated servers allow you to host a Northstar server without having to use a full client, making them more lightweight and easier to host for longer periods of time. Dedicated servers are still in development for Northstar, so while they do work, expect some bugs and general jank.\
To start a dedicated server on Northstar, launch NorthstarLauncher.exe with the argument `-dedicated`, this can be done manually, but releases also provide the batch file `r2ds.bat`, which will also do this.\
When using a dedicated server, arguments are read from `ns_startup_args_dedi.txt`, rather than `ns_startup_args.txt`.

#### Useful configuration files

* `ns_startup_args_dedi.txt`\
  contains the [startup arguments](../server-settings/README.md/#startup-arguments)
* `R2Northstar\mods\Northstar.CustomServers\mod.json`\
  contains [ConVars](../server-settings/convars.md) default values
* `R2Northstar\mods\Northstar.CustomServers\mod\cfg\autoexec_ns_server.cfg`\
  contains [ConVars](../server-settings/convars.md) and [overrides](../server-settings/playlistvars.md)

### Dedicated Server Caveats

At the moment, dedicated servers still require DirectX 11 to work, which typically requires a physical GPU, though they use almost no GPU processing power while in use, this can be an issue especially on GPU-less setups, so the launch argument `-softwared3d11` can be used to force DirectX to run in software mode.\
While this is absolutely not ideal, it's the best solution for truly headless dedicated servers at the moment, and surprisingly hardly uses any CPU time, though it can use roughly up to 1GB of RAM.\
Regarding RAM usage, dedicated servers also use significant amounts of RAM at the moment, often requiring 1.5-2GB, though I expect this to lower as development continues.


