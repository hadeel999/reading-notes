# Socket.io

## What is a Web Socket?
**WebSocket** is a computer communications protocol, providing full-duplex communication channels over a single TCP connection.

**WebSocket** is distinct from HTTP.

The **WebSocket** protocol enables interaction between a web browser (or other client application) and a web server with lower overhead than half-duplex alternatives such as *HTTP polling*, facilitating real-time data transfer from and to the server.

The **WebSocket** protocol specification defines `ws` (WebSocket) and `wss` (WebSocket Secure) as two new uniform resource identifier (URI) schemes that are used for `unencrypted` and `encrypted` connections respectively.

## Web Socket Request/Response Handshake
To establish a WebSocket connection, the client sends a WebSocket handshake request, for which the server returns a WebSocket handshake response as shown in picture below:

![](./images/read12a.PNG)

### JavaScript client example:
```
// Creates new WebSocket object with a wss URI as the parameter
const socket = new WebSocket('wss://game.example.com/ws/updates');

// Fired when a connection with a WebSocket is opened
socket.onopen = function () {
  setInterval(function() {
    if (socket.bufferedAmount == 0)
      socket.send(getUpdateData());
  }, 50);
};

// Fired when data is received through a WebSocket
socket.onmessage = function(event) {
  handleUpdateData(event.data);
};

// Fired when a connection with a WebSocket is closed
socket.onclose = function(event) {
  onSocketClose(event);
};

// Fired when a connection with a WebSocket has been closed because of an error
socket.onerror = function(event) {
  onSocketError(event);
};
```

