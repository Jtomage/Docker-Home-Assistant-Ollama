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
2. [Home Assistant](./HomeAssistant/ReadMe.md)
3. Infrastructure Add Ons
   1. [Node Read](./HomeAssistant/01-Infrastructure/node-red/ReadMe.md)
   2. [Code Server](./HomeAssistant/01-Infrastructure/code-server/ReadMe.md)
4. [Voice Assistant & AI](./HomeAssistant/02-AI/ReadMe.md)
    1. [Whisper](./HomeAssistant/02-AI/faster-whisper/ReadMe.md)
    2. [Piper](./HomeAssistant/02-AI/piper/ReadMe.md)
    3. [Ollama](./HomeAssistant/02-AI/ollama/ReadMe.md)
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