# Hosting a Dedicated Server

{% hint style="warning" %}
The GitBook based NorthstarWiki has been replaced in favour of the [NorthstarDocs](https://docs.northstar.tf/) where this wiki has been integrated.

Check it out here: [https://docs.northstar.tf/Wiki/](https://docs.northstar.tf/Wiki/)

The same page on the new wiki should be located here: [https://docs.northstar.tf/Wiki/hosting-a-server-with-northstar/dedicated-server/](https://docs.northstar.tf/Wiki/hosting-a-server-with-northstar/dedicated-server/)

{% endhint %}

## Hosting a Dedicated Server

### Setup

Dedicated servers allow you to host a Northstar server without having to use a full client, making them more lightweight and easier to host for longer periods of time. Dedicated servers are still in development for Northstar, so while they do work, expect some bugs and general jank.\
To start a dedicated server on Northstar, launch NorthstarLauncher.exe with the argument `-dedicated`, this can be done manually, but releases also provide the batch file `r2ds.bat`, which will also do this.\
When using a dedicated server, arguments are read from `ns_startup_args_dedi.txt`, rather than `ns_startup_args.txt`.

### Dedicated Server Caveats

At the moment, dedicated servers still require DirectX 11 to work, which typically requires a physical GPU, though they use almost no GPU processing power while in use, this can be an issue especially on GPU-less setups, so the launch argument `-softwared3d11` can be used to force DirectX to run in software mode.\
While this is absolutely not ideal, it's the best solution for truly headless dedicated servers at the moment, and surprisingly hardly uses any CPU time, though it can use roughly up to 1GB of RAM.\
Regarding RAM usage, dedicated servers also use significant amounts of RAM at the moment, often requiring 1.5-2GB, though I expect this to lower as development continues.

### Troubleshoot

See [troubleshoot](../troubleshooting.md)

For all settings see [Server settings](../server-settings/README.md)
