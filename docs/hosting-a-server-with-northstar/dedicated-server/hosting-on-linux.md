# Hosting on Linux

## Hosting on Linux

{% hint style="info" %}
This page is currently work-in-progress.
{% endhint %}

Linux users can launch the server executable using a Docker image or by using Wine. If you do not have a DirectX 11 capable GPU in your system (for example if you are using a hosting service), you will want to host a **Headless server.**

## Headless Servers

### Using Docker

#### [pg9182/northstar\_dedicated](https://github.com/pg9182/northstar-dedicated) : Docker image with server management tools and better performance. Check the `README` page for more info on pg9182's repository.

This guide will assume that you use a Debian based system. In this case, this guide will focus on using Ubuntu 22.04 LTS. (Most linux systems should be the same, but some might need some tweaks)\
\
Get started by installing Docker using the following script: `curl https://get.docker.com | sudo sh -`

Once the script has finished, Docker will be successfully installed. Next thing is to install docker-compose by doing `sudo apt install docker-compose -y`

Once that is done, you will need to download the Titanfall2 game files, this can be done by either installing using SteamCMD, or using pg9182's script located [here.](https://gist.github.com/pg9182/9a962adbfc27e93237cd14e4523c9da8)

pg9182's script is easiest, so that will be used in the guide. Run this command to download and execute the file:\
`sudo apt install jq wget ca-certificates -y && mkdir ~/tf2 && cd ~/tf2 && sh -c "$(curl -fsSL https://gist.githubusercontent.com/pg9182/9a962adbfc27e93237cd14e4523c9da8/raw/eccffd400326dd423ccaeb027a65d59168a00b7c/nsfetch.sh)" && cd ..`

After the script has finished, create a file called `docker-compose.yml`, run nano `docker-compose.yml` (or your favourite text editor) and add the following into it.

```
version: "3.7"  
  
services:
  aitdm1:
    image: ghcr.io/pg9182/northstar-dedicated:1-tf2.0.11.0
    pull_policy: always
    entrypoint: ['/bin/sh', '-c'] 
    command: ['/usr/libexec/nsdedi; /bin/sleep 60']
    environment:
      - NS_PORT=27015
      - NS_PORT_AUTH=8081
      - 'NS_SERVER_NAME=SERVERNAME' # Change your servername here
      - 'NS_SERVER_DESC=SERVERDESCRIPTION' # Change you Server Description here
      - |
        NS_EXTRA_ARGUMENTS=
        +map mp_angel_city # Change Map here
        +mp_gamemode aitdm # Change Gamemode here
        +setplaylist aitdm # Change Playlist here
        +net_compresspackets_minsize 64
        +net_compresspackets 1
        +spewlog_enable 1
        +sv_maxrate 127000
        +ns_should_return_to_lobby 0
    volumes:
      - ./tf2:/mnt/titanfall:ro
    ports:
      - '27015:27015/udp'
      - '8081:8081/tcp'
    restart: always
```

After you have edited the file, exit and then run this command to allow traffic to flow through the firewall: `sudo ufw allow 27015/udp && sudo ufw allow 8081/tcp`, after this run `docker-compose up -d`, after 60-120 seconds, your server should show on the server browser. If not, run `docker-compose logs -f`, and check the error message at the bottom.

### Without using Docker

> Hosting on a headless Linux server without Docker on Linux is not recommended, as you'll be forced to build packages yourself.

You can find instructions for running a dedicated server using Wine on [pg9182's repository.](https://github.com/pg9182/northstar-dedicated#running-with-wine)

[This comment on GitHub](https://github.com/R2Northstar/Northstar/issues/49#issuecomment-1001094694) also contains some information for hosting a dedicated server on Linux.
