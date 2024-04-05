---
tags:
  - linux
  - kserver
---

# What:
Linux is a computer operating system.  I'm currently running that OS on both my daily driver ([[darthvader | hostname: darthvader]]) and [[kserver | our media server]] .


## General System Information
---
Lot's can be discovered using the `dmidecode` app.
If you pass the `-t` flag, you can then specify a 'type' of data you're interested in and it'll display system information about that type.  Here's some good ones:
`sudo dmidecode -t 1` will give general machine information:
```
# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 2.7 present.

Handle 0x0001, DMI type 1, 27 bytes
System Information
        Manufacturer: Dell Inc.
        Product Name: OptiPlex 7020
        Version: 01
        Serial Number: GLQBS22
        UUID: 4c4c4544-004c-5110-8042-c7c04f533232
        Wake-up Type: Power Switch
        SKU Number: OptiPlex 7020
        Family: Not Specified
```
Here you can see we got the Manufacturer, the Product Name, Dell's Asset ID (Serial Number) and more.

Installed RAM can be inspected with:
`sudo dmidecode -t 17`
This will show total installed RAM, Types, Capacity, Form Factor, Slot (Locator), Speed and more.  _(the output is large so I'm skipping it here)_

You can inspect the various 'types' by [RTFM](https://www.dictionary.com/browse/rtfm)


## Processor
You can gather processor information thusly:
```
cat /proc/cpuinfo
```

If you're only interested in the architecture of the CPU:
`arch`

## Hard Drive