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

When I hit this endpoint, a JS array is returned, each index holding an object describing an event.  Below is the return of one object from the array when I hit the endpoint on [[Daily/2024-04-11]]:
>[!note]- Results:
>```javascript
>{"cover":{"source":"https://iti-images.s3.amazonaws.com/events/142c2d37-ddae-678a-37a7-20515e8e5ebb.webp"},"address":{"lat":33.77862389999999,"lng":-84.2793154,"address":"181 N Arcadia Ave, Decatur, GA 30030, USA","placeId":"ChIJWWc_NWYH9YgRR4qKlfF1rZ8","cityName":"Decatur","stateAbbr":"GA","country":"United States","addressComponents":[]},"owner":{"name":"Jeremiah's Italian Ice of Decatur"},"analytics":{"gotoBuyTicketCount":0,"getDirectionCount":0,"gotoGoogleReview":0,"shareEmailCount":0,"shareFBCount":0,"shareTweetCount":0},"customCategories":[],"isApproved":true,"isChoice":true,"isCustom":false,"isToBeExport":false,"isRemoved":false,"isBlocked":false,"isLocked":false,"isManuallyCreated":true,"isHubCreated":false,"isFacebookEvent":false,"isOnlineEvent":false,"isHybridEvent":false,"isHideTicketUrl":false,"changeHistory":[],"_id":"660abc00f1bb8d45e562346a","id":"04bd0009-0765-8f1c-0ae6-692aa1c9d9d1","name":"Jeremiah's Italian Ice of Decatur Grand Opening Event","title":"Jeremiah's Italian Ice of Decatur Grand Opening Event","description":"Join Jeremiah's Italian Ice of Decatur for a grand opening celebration on April 20, 2024! The first 100 guests have the chance to win FREE gelati for a year! In addition to trying the delicious treats, join us for yard games and facepainting. Families are encouraged to attend. ","category":null,"startTime":"2024-04-20T17:00:00.000Z","endTime":"2024-04-20T15:00:00.000Z","eventTimes":[{"_id":"660abc00f1bb8d45e562346b","startTime":"2024-04-20T17:00:00.000Z","endTime":"2024-04-20T15:00:00.000Z"}],"timezone":"EST","hostLink":"https://jeremiahsice.com/locations/decatur-ga/","eventLink":null,"feedId":"","manualFBEventHost":"Jeremiah's Italian Ice of Decatur","ticketUri":null,"venue":"Jeremiah's Italian Ice of Decatur","organizerEmail":null,"attendingCount":0,"categories":[],"ticketInfo":[],"eventTimesText":[],"timestamp":"2024-04-01T13:52:00.526Z","createdAt":"2024-04-01T13:52:00.526Z","multiHosts":[],"__v":0,"nameId":"jeremiahs-italian-ice-of-decatur-grand-opening-event-660abc00f1bb8d45e562346a","pinnedTime":"2024-04-10T14:22:26.570Z"}
>```




## History
- [[2024-04-10]]: Added `node-red-node-sqlite` node to my pallet to enable #SQL interaction with a sqlite database.
