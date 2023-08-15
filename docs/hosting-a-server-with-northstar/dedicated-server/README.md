# Hosting a Dedicated Server

If you want to host a server long term you cant always run a game instance on your PC.

For this we have two ways to host
* [Docker image](./hosting-on-linux.md) for Linux (generally recomended for long term hosting)
* [Windows hosting](./hosting-on-windows.md) (good for short term hosting)

### Troubleshooting

#### Useful configuration files

* `ns_startup_args_dedi.txt`\
  contains the [startup arguments](./#startup-arguments)
* `R2Northstar\mods\Northstar.CustomServers\mod.json`\
  contains [ConVars](./#convars) default values
* `R2Northstar\mods\Northstar.CustomServers\mod\cfg\autoexec_ns_server.cfg`\
  contains [ConVars](./#convars) and overrides

### Dedicated Server Caveats

At the moment, dedicated servers still require DirectX 11 to work, which typically requires a physical GPU, though they use almost no GPU processing power while in use, this can be an issue especially on GPU-less setups, so the launch argument `-softwared3d11` can be used to force DirectX to run in software mode.\
While this is absolutely not ideal, it's the best solution for truly headless dedicated servers at the moment, and surprisingly hardly uses any CPU time, though it can use roughly up to 1GB of RAM.\
Regarding RAM usage, dedicated servers also use significant amounts of RAM at the moment, often requiring 1.5-2GB, though I expect this to lower as development continues.

