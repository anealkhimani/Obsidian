---
tags:
  - linux
  - kserver
---

# What:
Linux is a computer operating system.  I'm currently running that OS on both my daily driver ([[darthvader | hostname: darthvader]]) and [[kserver | our media server]] .


## System Information
Lot's can be discovered using the `dmidecode` app.
It requires sudo privileges


## Processor
You can gather processor information thusly:
```
cat /proc/cpuinfo
```

If you're only interested in the architecture of the CPU:
`arch`

## Hard Drive