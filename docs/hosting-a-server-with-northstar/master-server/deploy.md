# Deploying Master Server

## Development

A Development Master Server uses http requests, it should be used for development purposes on your local machine.

### Installation steps

1. Clone [NorthstarMasterServer](https://github.com/R2Northstar/NorthstarMasterServer).
2. Run `npm install` && `npm run watch`.

Your master server is now running, to connect to it you need to change some configuration files.

Northstar by default points to https://northstar.tf as the masterserver URL, you need to replace it in the `autoexec_ns_server.cfg` and `autoexec_ns_client.cfg` config files. The default [dev.env](https://github.com/R2Northstar/NorthstarMasterServer/blob/main/dev.env) uses the ip `0.0.0.0` and port `8080` so you need to replace the url to `http://0.0.0.0:8080`.
