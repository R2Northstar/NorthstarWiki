# Hosting on Linux

{% hint style="info" %}
This page is currently work-in-progress.
{% endhint %}

Linux users can launch the server executable using a Docker image or by using Wine.
If you do not have a DirectX 11 capable GPU in your system (for example if you are using a hosting service), you will want to host a **Headless server.**

# <a name="Headless_Servers">Headless Servers</a>

## Using Docker

The Docker image for the latest version of Northstar can be found in this GitHub repo: [https://github.com/pg9182/northstar-dedicated](https://github.com/pg9182/northstar-dedicated)

### Prerequisites

| Requirement | Description                                             |
| ----------- | ------------------------------------------------------- |
| Kernel      | Linux 5.3+, but 4.9+ should work                        |
| CPU         | x86\_64, at least 3 cores minimum                       |
| RAM         | 2GB (Typically peaks at 1.6GB)                          |
| Disk        | 5GB                                                     |
| Network     | Recommended at least 7-20Mbps up                        |
| Docker      | Have Docker and Docker-Compose installed on the machine |

### Installation

#### Install Docker and Docker-Compose

If you don't already have docker & docker-compose installed, you can install them by running these commands in a terminal. 
**These install directions come directly from https://docs.docker.com/engine/install/**
##### Ubuntu
```  ```

##### Fedora



#### Prep Titanfall Server files

You will need obtain Titanfall's game files, typically by copying over your Titanfall installation folder and placing it on the Linux machine. Most of these files are for SP and therefore we can delete from the installation folder and prune the file size down to \~5GB.

Easiest way to do this is to copy the entire Titanfall2 folder to the server and delete the [following files](https://github.com/pg9182/northstar-dedicated#reducing-the-size-), or alternatively download and run [this sh script](https://gist.github.com/pg9182/9a962adbfc27e93237cd14e4523c9da8) made by pg9182 (note: this only downloads assets necessary to run a server and does not download a copy of the game).

#### Copy Titanfall Folder over to the Linux Machine

1. Access the files on your Linux machine using tools like [WinSCP](https://winscp.net/eng/download.php)
2. Navigate to the folder where you want to store the files. You can put them into `~/Titanfall2` for example.
3. Copy the newly pruned Titanfall folder to the server.

![Game files copied to `/mnt/Titanfall` as an example](https://i.postimg.cc/15HbbzFr/image.png)

#### Copy mods to server

If you have configured some mods,these can be placed at a similar location, like `~/mods` for example
![Mods placed inside /mnt/mods](https://i.postimg.cc/tRD5jnrJ/image.png)

#### Create docker-compose file

We are going to be using Docker-Compose to set up our container, this gives us much more flexibility and allows us to make changes to the start up args much cleaner. This example will let you start your servers without needing to have your compose in the same folder and directory as Titanfall 2 and your mods folder. Create a compose file in your home directory, or wherever is most convenient.

```
nano docker-compose.yml
```

Example docker-compose.yml

```yaml
version: '3'
services:
 northstar-skirmish: 
   image: ghcr.io/pg9182/northstar-dedicated:1-tf2.0.11.0 
   pull_policy: always 
   environment:
     - NS_PORT=37015
     - NS_PORT_AUTH=8081
     - 'NS_SERVER_NAME=Enter Server Name here'
     - 'NS_SERVER_DESC=Enter your description here'
     - NS_EXTRA_ARGUMENTS=
       +setplaylist aitdm //skirmish
       +mp_gamemode aitdm //skirmish
       +map mp_angel_city
       +ns_private_match_countdown_length 0
       +ns_should_return_to_lobby 0
       +net_compresspackets_minsize 64
       +net_compresspackets 1
       +spewlog_enable 0
       +sv_maxrate 127000
   volumes:
     - /home/user/Titanfall2:/mnt/titanfall:ro
     - /home/user/Titanfall2/mods:/mnt/mods:ro
   ports:
     - '37015:37015/udp'
     - '8081:8081/tcp'
   restart: always
```

A list of all the CONVARs are [here](../../hosting-a-server-with-northstar/dedicated-server#convars)

### Starting

#### Run the following command

To run this container go to the folder you saved the `docker-compose.yml` in and type

```
docker-compose up
```


## Without using Docker

> Hosting on a headless Linux server without Docker on Linux is not recommended, as you'll be forced to build packages yourself.

You can find instructions for running a dedicated server using Wine on [pg9182's repository.](https://github.com/pg9182/northstar-dedicated#running-with-wine)

[This comment on GitHub](https://github.com/R2Northstar/Northstar/issues/49#issuecomment-1001094694) also contains some information for hosting a dedicated server on Linux.
