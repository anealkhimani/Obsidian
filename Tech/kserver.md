---
tags:
  - kserver
  - Elgin
  - Linux
  - hardware
  - software
  - computer
  - OS
---

## Base Info
---

| Platform _(notebook/laptop/Pi/ESP etc.)_ | Desktop (Dell OptiPlex 7010)                      |
| ---------------------------------------- | ------------------------------------------------- |
| Form Factor                              | Tower                                             |
| Hostname                                 | kserver                                           |
| OS                                       | Debian GNU/Linux 12 (bookworm)                    |
| Processor Type                           | Intel Core i5-3470 @3.2GHz                        |
| RAM                                      | 4 x 4GB DIMM DDR3 @ 1333 MT/s                     |
| HD1 (Boot/OS)                            | Samsung SSD 870 1TB<br>/dev/sdb                   |
| HD2                                      | (Will Hold SeaGate IronWolf 12TB)                 |
| HD3                                      | (Will Hold SeaGate IronWolf 12TB)                 |
| HD4                                      | (Will Hold SeaGate IronWolf 12TB)                 |
| IP Address                               | 192.167.1.207 (**FIxed** Allocated at router)     |
| Physical Location                        | Basement in Cabinet beneath [[Elgin]] Power Panel |

## Notes
---
Serves as a... server?
Currently runs several #docker containers to serve things like
- [[Plex]]
- [[Home Assistant]]
- [[Sonarr]]
- [[Radarr]]
etc.



## TODO
---

# Machine Information

| Machine Name:               | kserver                                                              |
| --------------------------- | -------------------------------------------------------------------- |
| IP Address:                 | 192.168.1.207                                                        |
| MAC Address:                | 98:90:96:a3:18:4b                                                    |
| Admin:                      | anealkhimani                                                         |
| Date of this Documentation: | `$= dv.current().file.ctime.toLocaleString(DateTime.DATETIME_SHORT)` |
| Asset #:                    | None                                                                 |
| OS                          | Debian GNU/Linux 12 (bookworm)                                       |

## Description
#kserver is a computer on our [[Elgin]] dr. Home network.  
It currently has Debian installed as the OS.
Its job is to serve applications and do chores to make life easier for Liz and myself (although, I doubt it makes things _easier_ for me...)

Currently, it's running most of it's automations/applications utilizing #docker as a containerization platform.  

## [Hardening Checklist](https://www.pluralsight.com/blog/it-ops/linux-hardening-secure-server-checklist)
- [ ] Enable a BIOS password on [[kserver]] [priority:: medium]  [created:: 2024-03-29]  [due:: 2024-04-01]
- [ ] Disable Booting from removable media in BIOS  [priority:: medium]  [created:: 2024-03-29]  [due:: 2024-04-01]

