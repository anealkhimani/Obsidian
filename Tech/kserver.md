---
tags:
    - kserver
    - Elgin
    - Linux
    - hardware
    - software
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

