---
tags:
  - docker
---

## General:
[Docker](https://docker.com) is a containerization system.  It allows one to run applications in a virtual environment, and it makes it easy to build, share and develop applications

## Useful bits
To GREP the logs from a running container:
```bash
docker logs <container_name> 2>&1 | grep "127."
```
Replace <container_name> above with the name of your running container and the pipe the output to grep, as normal.  This just redirects the output of the `docker logs` command to stdout so you can grep it...

Conversely, you can redirect the output from the log file into a local file thusly:
```bash
docker logs <container_name> &> ~/some/local/file
```


