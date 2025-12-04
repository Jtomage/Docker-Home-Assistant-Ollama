# Smart Home

Setting Up a Smart Home With Docker Compose using Home Assistant as the base and all
services in docker can be integrated with Home Assistant or
with associated Home Assistant Infrastrucuture Add ons

> [!WARNING]
>
> Have not tested the files. Currently migrating the changes over from my initial test files

### To Do List

- [ ] Add script to run all docker compose files

## Table of Contents

1. [Initialization](#initialization)
2. [Home Assistant]()
3. [Infrastructure Add Ons]()
   1. [Node Read]()
   2. [Code Server]()
4. [Voice Assistant & AI]()
    1. [Whisper]()
    2. [Piper]()
    3. [Ollama]()
5. [Future](#future)


## Initialization

Install Docker with docker compose

### Smart Home Network

The main network that all the Smart home services will communicate on. 

### Main Volume Container

Storing changes in a volume which can be exported, compressed and uploaded to the cloud / different drive for back up using cron job or any other version of a scheduled task. 

Currently docker compose  will allow a subpath on a volume which can store different applications data in different directories. However, the dictories need to be created in the volume. the reason for the (init)ialization container.

#### Init_smart_volume

Docker Volume subpath does **NOT** create the directories. Therefore the current hack to use an init container to create the directories detailed as workaround for the issue. https://github.com/moby/moby/issues/47842 

When using `volume.subpath` the docker desktop may show that the volume is not in use but it will be in used and get written to.

## Home Assistant

The core of the Smart Home. Used to connect devices on the wifi and other networks. Everything in this setup will be based 
around this application. 

#### Configurations

```
cap_add
    - SYS_ADMIN
```
Do not need to use priviledge, SYS_ADMIN worked. 

## Node-Red

For more complex smart home automations. Can connect devices wifi devices as well. Can Create different workflows that can be triggered via Home Assistant or on its own

From the change log of the broadlink control v2.1.6
RF learn and send may not be working yet on the RM Pro 4 series but should be working in the earlier RM Pro units, although I don't have either to test with.
https://flows.nodered.org/node/node-red-contrib-broadlink-control

### Configuration

- Connect Node Red to Home Assistant
    - Install Home Assistant Websockets palette
      - Hamburger Menu -> Manage Palette
      - Install tab
      - Search For node-red-contrib-home-assistant-websocket
      - click install
- RF / IR Blasters
    - Currently have Broadlink
    - Install Broadlink Controls
      - Hamburger Menu -> Manage Palette
      - Install tab
      - Search For node-red-contrib-broadlink-control
      - click install
- IP Camera
    - When setting the configuration, the video may not load, there add, then review later

## Mosquitto

MQTT messaging broker. Used to relay information from different devices. 

## Code-server

Added VS Code, remote code server, as a container to configure Home Assisstant and related files. 

## AI

### Whisper

### Piper

### Ollama


## Future

Looking to add these latter

### ESPHome

https://esphome.io/

### Frigate NVR 

https://frigate.video/

used for AI object detection

### Espspectre

https://github.com/francescopace/espectre

uses wifi like lidar