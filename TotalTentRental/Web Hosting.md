---
tags:
  - MongoDB
---
[[2024-05-29]], I started a new 'Droplet' on my server provider [[DigitalOcean]]
The droplet should cost me about $12/month? 

## MongoDB
I created a new Project in [MongoDB Atlas](https://mongodb.com) to persist data for various things related to this business.  In that Project I created a cluster named `website` with user credentials:
```
UN: anealkhimani
PW: B2RpG2ShJfi3N2T2
```
This cluster is accessible from within specific IP addresses only, so for now, it will only allow connections from my work IP address.  You can add more in the UI at MongoDB.com>(project_name)>Network Access