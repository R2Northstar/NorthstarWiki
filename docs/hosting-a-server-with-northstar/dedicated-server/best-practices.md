# Best practices

---
description: Tweaks and tricks to improve both your experience in hosting and others' in playing on your server
---

## Monitoring

You can set the Convar `ns_should_log_all_clientcommands` to `1` to log all client commands. This includes both benign things like the command a client sends to server to respawn after death but also nefarious, like a malicious client calling `emit`, a command that before being patched out allowed clients to spam voice lines to other clients.

Due to the increased verbosity `ns_should_log_all_clientcommands` is set to `0` (disabled) by default but should be enabled in cases where you want to investigate suspicious activity on your server.

## Optimization Commands (Optional)

| Command                          | Description                                                                                                                    |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| `net_compresspackets 1`          | Enable compress packets                                                                                                        |
| `net_compresspackets_minsize 64` | Decrease usage from ~12-16 mbps to ~6-8 mbps on 20 player PVP server and ~9-12mbps to ~5-7 mbps on 12 player gun game server   |
| `sv_maxrate 127000`              | Sets the maximum bandwidth rate allowed (both incoming/outcoming) per second (in bytes)                                        |

**Note:** The effect is dependent on your network, system, etc. Therefore, you should really add the command one by one and test it to see if there is any benefit for your server.
