# Launch arguments

{% hint style="warning" %}
The GitBook based NorthstarWiki has been replaced in favour of the [NorthstarDocs](https://docs.northstar.tf/) where this wiki has been integrated.

Check it out here: [https://docs.northstar.tf/Wiki/](https://docs.northstar.tf/Wiki/)

The same page on the new wiki should be located here: [https://docs.northstar.tf/Wiki/using-northstar/launch-arguments](https://docs.northstar.tf/Wiki/using-northstar/launch-arguments)

{% endhint %}

Here's a list of new command line arguments that Northstar introduces, they should be included in `ns_startup_args.txt` or `ns_startup_args_dedi.txt`.

| Argument           | Description                                                                                        | Value                            |
| ------------------ | -------------------------------------------------------------------------------------------------- | -------------------------------- |
| `-disablelogs`     | Disable logging and creation of log files                                                          |                                  |
| `-nonorthstardll`  | Disables Northstar loading                                                                         |                                  |
| `-northstar`       | Enables Northstar loading                                                                          |                                  |
| `-vanilla`         | Enables vanilla compatibility                                                                      |                                  |
| `-dedicated`       | Starts a dedicated server without video output                                                     |                                  |
| `-waitfordebugger` | Waits for debugger to connect before launching game                                                |                                  |
| `-language`        | Forces loading of client localisation                                                              | language string ex: `portuguese` |
| `-profile=`        | Enabled specifying a different profile directory. Default: R2Northstar                             | Example: `-profile="dev mods"`   |
| `-enablechathooks` | Enables the use of chathooks for use by mods                                                       |                                  |
| `-noplugins`       | Disables the plugin system                                                                         |                                  |

Here's a list of command line arguments from the base game.

| Argument           | Description                                                                                        | Value                            |
| ------------------ | -------------------------------------------------------------------------------------------------- | -------------------------------- |
| `-novid`           | Disables startup videos                                                                            |                                  |
| `-nosound`         | Disables all game sounds                                                                           |                                  |

# Environment Variables
| Variable name      | Description                                                                                        | Value                            |
| ------------------ | -------------------------------------------------------------------------------------------------- | -------------------------------- |
| `LFX`              | Enables the use of [LatencyFleX](../steamdeck-and-linux/installing-on-steamdeck-and-linux.md#latencyflex) (Linux-only) | `0` or `1`                       |
