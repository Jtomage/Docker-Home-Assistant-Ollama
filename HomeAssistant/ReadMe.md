# Home Assistant

This the core application for the smart home. It should be used to trigger the different events and automatiions used in the smart home

## Docker Compose Notes

#### cap_add vs priviledge

```
cap_add
    - SYS_ADMIN
```

Was added to the docker compose configuration to gain access to Wifi devices. This worked instead of using `priviledge: true`

#### Docker compose Extentiosn

Using extension in hopes it makes configuring docker compose files easier. https://docs.docker.com/reference/compose-file/extension/

#### HACS

to install HACS, commmunity supported add ons, enter the home assistant container

`docker exec -it homeassistant bash`

then when in the container run

`wget -O - https://get.hacs.xyz | bash -`