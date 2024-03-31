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