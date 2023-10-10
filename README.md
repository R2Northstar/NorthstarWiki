# Northstar Wiki Repo

This repo contains documentation around the [Northstar mod](https://github.com/R2Northstar), a Titanfall 2 mod to join and host custom community servers.

The `docs/` directory contains the content synchronised to the [GitBook Wiki page](https://r2northstar.gitbook.io/).

Use this repo to perform pull requests and open issues to request changes to the wiki content.

## Building locally

Unfortunately, [GitBook](https://www.gitbook.com/) does not offer a way to work and preview edited content locally.

However, under the hood GitBook just uses [Markdown](https://www.markdownguide.org/) files that can be edited using any text editor.
They can also be previewed to some degree on GitHub directly.

When working locally, [`mdBook`](https://rust-lang.github.io/mdBook/) can be used to render previews by simply running `mdbook serve`.
Note that GitBook has a custom extended markdown syntax that is not supported by mdBook but using mdBook results in a rendered version that is good enough to verify the correctness of most changes.
