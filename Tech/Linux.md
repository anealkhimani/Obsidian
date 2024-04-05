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

You can inspect the various 'types' by [RTFM](https://www.dictionary.com/browse/rtfm)


## Processor
---
You can gather processor information thusly:
```
cat /proc/cpuinfo
```

If you're only interested in the architecture of the CPU:
`arch`

## Hard Drive
---
Some tools to view Hard disks installed on a system that I use are as follows:
```
sudo parted -l
```
This one will show disks/partitions and will also provide the device and model data
Below is the output for [[darthvader]]:
```bash
Model: ATA SanDisk SDSSDA-1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  538MB   537MB   primary   fat32        boot
 2      539MB   1000GB  1000GB  extended
 5      539MB   1000GB  1000GB  logical   ext4
```

On [[Alan Shiflett | Alan's]] recommendation, I run some basic testing on hard drives before installing them permanently in a computer.
I recently bought 3 x 12TB Seagate IronWolf drives to expand [[kserver]].
Before installing them, I connected each to an external SATA device and ran:

```
smartctl -t long /dev/sd?
```

_(of course, replacing the ? above with the actual device filename.)_

This command should be run against an _unmounted_ disk and will take a considerable length of time (~17 hours for each disk)


## Memory
---
Installed RAM can be inspected with:
```
sudo dmidecode -t 17
```
This will show total installed RAM, Types, Capacity, Form Factor, Slot (Locator), Speed and more.  _(the output is large so I'm skipping it here)_