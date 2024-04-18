---
tags:
    - homeassistant
    - docker
---
# Overview
- Home automation platform used to control/monitor devices and other things in the house
- It currently runs on [[k_server]] in a [[Docker]] container.

# Integrations
---
## [Nabu Casa](https://www.nabucasa.com/)
This service is used to enable us to connect to this Docker container running locally on our home network over the internet, without actually exposing it.  We pay a $6 monthly service fee for this service.  While I did initially try to DIY it, the $6 fee goes to support the project, which I'm cool with.

## Bosch Home Connect
This is an integration in Home Assistant that allows for control/sensors connected to appliances in the Bosch family (Our DIshwasher)
The integration required creating a developer account with Bosch, Adding an 'application' and locating/using their provided 0Auth2 client_id/Secret in Home Assistant to make all the things sync up. [Check Here](https://developer.home-connect.com/) for info about that

## Template Stuff 
Here's a nice #template that lists all domains and all entities in that domain.
Useful in the `Developer Tools>Template` section:
```jinja
{% for d in states | groupby('domain') %}
  {% if loop.first %} Domains: {{loop.length}}
  {% endif %} - {{ d[0] }} ({{ states[d[0]] | count }})
      - {{ states[d[0]] |map(attribute='entity_id')| list|sort|join('\n      - ') }}
{% endfor %}
```

This YAML block will call the tts service and say a random phrase.  Will be useful once I figure out how to notify myself of stuff
```yaml
service: tts.cloud_say
data:
  cache: false
  entity_id: media_player.basement_display
  message: >
    {{ ["test 1", "doober", "i cant build a cat", "I design and build shrubberies", "someone has beaten a giant here"] | random }}

```

This #template lets you check an array of strings for specific text and returns another string if so, or if not:
```jinja
{% if ['doob', 'fubar', 'fancy'] | select('search', 'ar') | list | count == 0 %}
 It's not there
{% else %}
 I found it!
{% endif %}
```
## [[Zigbee2mqtt]]
This app is responsible for finding the Zigbee devices on the network and exposing them to Home Assistant.



## Email Things
I've set up access to the [Mail and Packages integration](https://github.com/moralmunky/Home-Assistant-Mail-And-Packages/wiki/Configuration-and-Email-Settings) into Home Assistant.  This integration watches your inbox for emails from specific providers (USPS, UPS, FedEx) and adds sensor data in HA when it sees that you've got packages arriving.
As part of the setup, I had to create an app password for Google to allow the integration to view my email.  the App Name and #password are:
> [!info]- HomeAssistant Mail & Packages
> kdzb hsly zinc wvfc

The integration _seems_ to work?  It appears that my Gmail settings automatically move incoming USPS emails into 


## Roborock Q Revo
HA has an integration for our robot vacuum.  Once the integration is added, several sensors are added to HA that let you track things like last_cleaning, error_codes, etc.
Several services are exposed as well, which will technically allow you to send the robot to go do cleaning in specific rooms.  Check the information [here](https://www.home-assistant.io/integrations/roborock/) for more info.
Basically, you need to enable Debug Logging for the integration in HA.  Then, reload the integration.  Once reloaded, inspect the logs for HA to find the 'Got home data' section.  Here, there'll be a 'rooms' array containing the names/IDs of the rooms you've defined in the Roborock app.
Use these ID's to discern the room mapping. _(check the table below)_

| HomeDataRoom ID | Room Name      | 2-digit ID |
| --------------- | -------------- | ---------- |
| 5103121         | Office         | 18         |
| 3883732         | Dining room    | 20         |
| 3883730         | Master bedroom | 16         |
| 3883729         | Guest bedroom  | 17         |
| 3883728         | Bathroom       | 19         |
| 3883727         | Living room    | 22         |
| 3883725         | Hall           | 23         |
| 3883724         | Kitchen        | 21         |
 A possible service call could look like below:
 ```yaml
service: vacuum.send_command
data:
  command: app_segment_clean
  params:
    - segments:
        - 22
        - 23
      repeat: 2
target:
  entity_id: vacuum.s7_roborock
```


## [IMAP Integration](https://www.home-assistant.io/integrations/imap/)
I've added an ==App Password== to my Google account for the IMAP sensor (to enable me to read my Gmail messages from within HA)
The password is:
`dmdw tcps nowi tffo`

This integration adds a sensor to HA whose state is equal to the number of unread emails in your account.

When a new email arrives, it can fire an automation that you can use to do other things, like notify yourself, set template sensors and such.  I'll attempt to use the latter option to try to gather my daily E-Trade Balance and my Chase Checking account balance as I used to do in my old iteration of HA