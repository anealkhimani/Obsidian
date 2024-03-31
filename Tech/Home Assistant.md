---
tags:
    - homeassistant
    - docker
---
# Overview
- Home automation platform used to control/monitor devices and other things in the house
- It currently runs on [[k_server]] in a #docker container.
## [Nabu Casa](https://www.nabucasa.com/)
This service is used to enable us to connect to this Docker container running locally on our home network over the internet, without actually exposing it.  We pay a $6 monthly service fee for this service.  While I did initially try to DIY it, the $6 fee goes to support the project, which I'm cool with.

## Bosch Home Connect
This is an integration in Home Assistant that allows for control/sensors connected to appliances in the Bosch family (Our DIshwasher)
The integration required creating a developer account with Bosch, Adding an 'application' and locating/using their provided 0Auth2 client_id/Secret in Home Assistant to make all the things sync up. [Check Here](https://developer.home-connect.com/) for info about that


## Template Stuff
Here's a nice one that lists all domains and all entities in that domain.
Useful in the `Developer Tools>Template` section:
```
{% for d in states | groupby('domain') %}
  {% if loop.first %} Domains: {{loop.length}}
  {% endif %} - {{ d[0] }} ({{ states[d[0]] | count }})
      - {{ states[d[0]] |map(attribute='entity_id')| list|join('\n      - ') }}
{% endfor %}
```


## [[Zigbee2mqtt]]
This app is responsible for finding the Zigbee devices on the network and exposing them to Home Assistant.