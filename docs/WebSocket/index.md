---
title: Get Chat
---

# Get chat Using WebSockets
:::tip
If the npm module is not installed, please refer to the getting-started guide.
:::

```javascript
const WebSocket = require('ws')
const uuid = require('uuid')

// Create a new websocket server on port 3000
console.log('Ready. On MineCraft chat, type /connect localhost:3000')
const wss = new WebSocket.Server({ port: 3000 })

// On Minecraft, when you type "/connect localhost:3000" it creates a connection
wss.on('connection', socket => {
  console.log('Connected')

  // Tell Minecraft to send all chat messages. Required once when Minecraft starts
  socket.send(JSON.stringify({
    "header": {
      "version": 1,                     // Use version 1 message protocol
      "requestId": uuid.v4(),           // A unique ID for the request
      "messageType": "commandRequest",  // This is a request ...
      "messagePurpose": "subscribe"     // ... to subscribe to ...
    },
    "body": {
      "eventName": "PlayerMessage"      // ... all player messages.
    },
  }))

  // When MineCraft sends a message (e.g. on player chat), print it.
  socket.on('message', packet => {
    const msg = JSON.parse(packet)
    console.log(msg)
  })
})
```
Subscribe to the chat event and fetch the chat packet to load the chat.

Now, if you've pasted this into ``index.js``, enter ``node index.js`` in the terminal to run the code

"If ``Ready. On MineCraft chat, type /connect localhost:3000`` appears in the terminal, type ``/connect localhost:3000`` in Minecraft Chat to connect.

Then, you can fetch the chat using WebSockets.

This document references https://github.com/sanand0/minecraft-websocket/tree/master/tutorial#programming-minecraft-with-websockets.
