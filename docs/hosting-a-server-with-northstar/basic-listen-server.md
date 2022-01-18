# Hosting a Basic Listen Server

A listen server only runs while the user is in the match, and acts like a 'public' private match/lobby\
The only difference between a listen and dedicated server is that a listen can only run while the host is in the match, while a dedi will run without the user or TF|2 open.

## Instructions

To host a listen server on Northstar, go to the lobby and press the `Private Match` button to begin a private match. While this does allow you to host a server, other people won't be able to join it, so you'll need to port forward 2 ports to allow other people to join.\
The ports you'll need to forward are `37015` UDP, and `8081` TCP by default, if this works as it should, this should result in your server being displayed on the server browser, and other clients being able to connect to it.\
![screenshot select private match](https://raw.githubusercontent.com/R2Northstar/NorthstarWiki/main/wiki/lobbyprivatematch.png)

## Server Configuration

Whether you're running a listen or dedicated server, you'll generally want to mess with the configuration at least a bit. While I do think the default configuration settings are pretty ok, being able to change your server's name or password, or increasing your server's tickrate is often something you'll want to do. Server configuration can be modified in the file `R2Northstar/mods/Northstar.CustomServers/mod/cfg/autoexec_ns_server.cfg`, which will be executed on server startup.\

Additionally most dedicated server settings and configs can be used on a listen server.\
Dedicated server startup arguments can't seem to be used, as the private match lobby overrides them. However most these settings can all be changed in the lobby prior to game start, rendering it a moot point. \
The only arg that is not able to be replicated (I think) via the lobby screen is `max_players` You'd need a dedicated server if you want to change that.\
Dedicated convars can be placed into `R2Northstar/mods/Northstar.CustomServers/mod/cfg/autoexec_ns_server.cfg`\



Below are a series of variables and commands you can use for server configuration:

| Name                                   | Description                                                                                                                                                                                 | Default Value                  |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------ |
| `ns_server_name`                       | Your server's name on the server browser                                                                                                                                                    | `"Unnamed Northstar Server"`   |
| `ns_server_desc`                       | Your server's description on the server browser                                                                                                                                             | `"Default server description"` |
| `ns_server_password`                   | The password required to join your server, can be bypassed if clients directly connect and you are using insecure auth                                                                      | `""`                           |
| `ns_report_server_to_masterserver`     | Whether your server should report itself to the masterserver, for use in auth and the serverbrowser                                                                                         | `1`                            |
| `ns_report_sp_server_to_masterserver`  | Whether your server should report itself to the masterserver if started on a singleplayer map, for use in auth and the serverbrowser                                                        | `0`                            |
| `ns_auth_allow_insecure`               | Allows clients to join your server without authenticating with the masterserver, currently required to allow clients to connect directly to your IP, rather than through the server browser | `0`                            |
| `ns_erase_auth_info`                   | Whether your server should erase authentication information after it is used, this is useful for development but should normally be kept at 1                                               | `1`                            |
| `ns_player_auth_port`                  | The port used for the server's local authentication server, this is the TCP port we forwarded earlier                                                                                       | `8081`                         |
| `everything_unlocked`                  | Whether all items, weapons, etc should be unlocked on the server                                                                                                                            | `1`                            |
| `ns_should_return_to_lobby`            | Whether the server should return to private match lobby after completing a game, if 0, this will go to the next map/mode in the playlist                                                    | `1`                            |
| `ns_should_log_unknown_clientcommands` | Whether unknown clientcommands should be printed in the console, worth disabling if they get on your nerves                                                                                 | `1`                            |
| `net_chan_limit_mode`                  | If 0, don't limit the netchannel processing time individual clients are allowed. If 1, kick clients that go over the limit. If 2, log clients that go over the limit in console             | `2`                            |
| `net_chan_limit_msec_per_sec`          | The number of milliseconds of server netchan processing time clients can use per second before triggering the response set in net\_chan\_limit\_mode                                        | `30`                           |
| `base_tickinterval_mp`                 | The delay between each tick ran on the server, your tickrate will be 1 divided by this value                                                                                                | `0.016666667`                  |
| `sv_updaterate_mp`                     | The maximum number of times per second your server will send information to connected players, if a player's cl\_updaterate\_mp value is lower than this, their rate will be limited to it  | `20`                           |
| `sv_max_snapshots_multiplayer`         | The number of snapshots stored locally for use in replays, this should be set to sv\_updaterate\_mp \* 15                                                                                   | `300`                          |
| `host_skip_client_dll_crc`             | Whether the server should allow clients with modified client.dll files to connect, these are used for visor colour edit mods                                                                | `1`                            |

## Tips and tricks:

To change gamemode and map, run:

```
sv_cheats 1; script GameRules_ChangeMap( "mp_forwardbase_kodai", "ctf" ); sv_cheats 0
```

replace `mp_forwardbase_kodai` and `ctf` with your desired map and gamemode.\
The list of maps can be found [here](dedicated-server/#maps).\
The list of gamemodes [here](dedicated-server/#gamemodes).

If someone keeps messing with the settings, set `ns_private_match_only_host_can_change_settings` to `2`, so that only you can change them.

Set `ns_private_match_countdown_length` to `1` if you don't want to wait for the countdown timer when you start a match. \
Additionally, set `ns_private_match_only_host_can_start` to `1` so that only you can actually press the _start match_ button.
