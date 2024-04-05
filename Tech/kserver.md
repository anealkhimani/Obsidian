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
Currently runs several [[Docker]] containers to serve things like
- [[Plex]]
- [[Home Assistant]]
- [[Sonarr]]
- [[Radarr]]
etc.



## TODO
---
## [Hardening Checklist](https://www.pluralsight.com/blog/it-ops/linux-hardening-secure-server-checklist)
- [ ] Enable a BIOS password on [[kserver]] [priority:: medium]  [created:: 2024-03-29]  [due:: 2024-04-01]
- [ ] Disable Booting from removable media in BIOS  [priority:: medium]  [created:: 2024-03-29]  [due:: 2024-04-01]

## History
---
>[!note]- [[2024-04-05]]
>- Began running 2 of 3 new HD tests before installing

