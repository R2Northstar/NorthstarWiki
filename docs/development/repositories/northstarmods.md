---
description: Core squirrel mods
---

{% hint style="warning" %}
The GitBook based NorthstarWiki has been replaced in favour of the [NorthstarDocs](https://docs.northstar.tf/) where this wiki has been integrated.

Check it out here: [https://docs.northstar.tf/Wiki/](https://docs.northstar.tf/Wiki/)

The same page on the new wiki should be located here: [https://docs.northstar.tf/Wiki/development/repositories/northstarmods](https://docs.northstar.tf/Wiki/development/repositories/northstarmods)

{% endhint %}

# NorthstarMods

TODO

When adding new Sqirrel script source files that are from the base game, make sure to commit the unmodified file first.
In particular, on `main` they should committed as `Respawn` with the email address `respawn@northstar.tf`.

```sh
git -c user.name="Respawn" -c user.email="<respawn@northstar.tf>" commit -m "Add SQUIRREL_FILE.nut from VPK_NAME"
```

This process is done to later leverage the power of `git blame` to see who authored a particular code line which assists with better understanding changes in the codebase.
