---
tags:
  yaml
  zigbee2mqtt
  docker
---

# General
This application utilizes a Zigbee Radio Device (In my case, it's a [USB dongle](https://phoscon.de/en/conbee2), plugged into an extension cable, then into [[kserver]])

Currently, this application is running in a Docker Container on [[kserver]]
and the web UI is accessible at [192.168.1.207:8888](http://192.168.1.207:8888)

This app has the ability to locate zigbee devices that are set to be discovered.  Then, once it locates the device, it allows you to rename it as needed and will automatically send a MQTT 'discovery' message that [[Home Assistant]] can pick up on.  Once [[Home Assistant|HA]] sees this discovery message, it adds the device to its UI for control and automation.


## USB Dongle
As mentioned above, the Zigbee Radio device is a Conbee II USB dongle.  I bought it a few years ago and have been using it in a few different ways.  My most recent implementation is the one in this note.

on [[kserver]], this USB device is mounted at `/dev/ttyACM0`
Occasionally, you'll run into issues starting up this container on kserver.
In order to update the firmware on the ConbeeII stick, I was required to install a Deconz app.  That app created 2 systemctl services on kserver (deconz and deconz-gui).  The deconz service was set to 'enabled', which of course starts the service on system boot.  

That service began constant communication with the dongle, which made it unavailable to the container when it spun up.  The Zigbee2mqtt app logs output a `Error: Error - cannot access Serial device at /dev/ACM0`
(or some such)

The deconz service is the culprit.  Stop that service and the container restarts, error free.

## Installation
If you follow closely the instructions on the getting started section of the website (mostly the [Docker Compose Example](https://www.zigbee2mqtt.io/guide/getting-started/#installation)) provided there, you'll see what you need to do.  During the "Let's create a configuration.yaml" file part, you'll need to compensate for the fact that Home Assistant is going to be listening for incoming MQTT packets from this application by adding the `homeassistant: true` directive in there.
You'll also notice that the link above provides a MQTT service in the docker-compose file as well to spin up an eclipse-mosquitto container.  This is also a pre-requisite (duh), and it shows a working example.  You may need to tweak it slightly.

Here's the section from my docker-compose.yaml #yaml:
```
# Zigbee2mqtt
  zigbee2mqtt:
    container_name: zigbee2mqtt
    image: koenkk/zigbee2mqtt
    restart: unless-stopped
    volumes:
      - /home/anealkhimani/docker/home/zigbee2mqtt:/app/data
      - /run/udev:/run/udev:ro
    ports:
      - 8888:8080
    environment:
      - TZ=America/New_York
    devices:
      - /dev/ttyACM0:/dev/ttyACM0

  # Mosquitto
  mosquitto:
    container_name: mosquitto
    image: eclipse-mosquitto:2.0
    restart: unless-stopped
    command: "mosquitto -c /mosquitto-no-auth.conf"
    ports:
      - 1883:1883
      - 9001:9001
    volumes:
      - /home/anealkhimani/docker/mosquitto:/mosquitto
```

Below is the Zigbee2mqtt `configuration.yaml` file I created to continue the installation: #yaml 
```
permit_join: true
homeassistant: true
mqtt:
  base_topic: zigbee2mqtt
  server: mqtt://mosquitto
serial:
  port: /dev/ttyACM0
frontend: true
advanced:
  network_key: GENERATE
```

You'll notice that there's some small deviations from the documentation.  Namely, we treat the `frontend` key as a boolean and mark it as 'true' and omit the `port` subkey
Also, we set the `mqtt>server` key to value `mqtt://mosquitto`.  We do this because that's the name we gave to the container in the `docker-compose.yaml` above, and docker treats this kind of like a hostname for the container.  Also of course, the serial address of the USB dongle is unique to my setup `/dev/ttyACM0`
