---
tags:
  - automation
  - kserver
  - docker
---
# What it is:
[NodeRed](https://nodered.org) is a web-based, low-code automation application you can use to create workflows.  A high-level conceptual view is that you create a 'Flow' which consists of various 'nodes' that pass messages through them.  These two things combined can do fancy things.  For example:
- You could create a flow that has 3 nodes:
	1. Watch for a file change node
	2. parse the file's new data
	3. pass that data along to another service (MQTT, REST call, etc.)

In an ideal world, this could eliminate the need to create automations within [[Home Assistant]], but in my world it'll be used to supplement those automations (or be an easier way to do complex things, like parse large JSON objects, etc.)

## Interesting
Here's a URL from the Decatur events website.  They use a service called 'imgoing' to view/display events happening in Decatur.  Their URL is:
```
https://imgoing-prod-api.xyz/api/visitors/DecaturGA/events?page=1&limit=16&category=All&source=google
```
Now it's my URL too!  I'll use it to populate a 'Local Calendar' element in [[Home Assistant]].
