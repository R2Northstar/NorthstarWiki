---
description: Tweaks and tricks to improve both your experience in hosting and others' in playing on your server
---

{% hint style="warning" %}
The GitBook based NorthstarWiki has been replaced in favour of the [NorthstarDocs](https://docs.northstar.tf/) where this wiki has been integrated.

Check it out here: [https://docs.northstar.tf/Wiki/](https://docs.northstar.tf/Wiki/)

The same page on the new wiki should be located here: [https://docs.northstar.tf/Wiki/hosting-a-server-with-northstar/dedicated-server/best-practices](https://docs.northstar.tf/Wiki/hosting-a-server-with-northstar/dedicated-server/best-practices)

{% endhint %}

# Best practices

{% hint style="info" %}
TODO: If you have experience in hosting Northstar servers and want to share your knowledge, please open a [pull request](https://github.com/R2Northstar/NorthstarWiki/pulls).
{% endhint %}

## Optimization Commands (Optional)

| Command                          | Description                                                                                                                    |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| `net_compresspackets 1`          | Enable compress packets                                                                                                        |
| `net_compresspackets_minsize 64` | Decrease usage from ~12-16 mbps to ~6-8 mbps on 20 player PVP server and ~9-12mbps to ~5-7 mbps on 12 player gun game server   |
| `sv_maxrate 127000`              | Sets the maximum bandwidth rate allowed (both incoming/outcoming) per second (in bytes)                                        |

**Note:** The effect is dependent on your network, system, etc. Therefore, you should really add the command one by one and test it to see if there is any benefit for your server.
