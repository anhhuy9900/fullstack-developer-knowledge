# Websocket

#### Websocket server

- Unlike HTTP servers, WebSockets ones don’t have any routes by default because it is just not needed. In this protocol, you just use a string to send and receive information (a good practice is to send a JSON object serialized to a string). That’s why the configuration is so simple, still, it’s not the end. Now we have to handle connections to the server, receive data from clients, and send them to the other participants in our chat.
- WebSockets, on the other hand, allow for sending message-based data, similar to UDP, but with the reliability of TCP. WebSocket uses HTTP as the initial transport mechanism, but keeps the TCP connection alive after the HTTP response is received so that it can be used for sending messages between client and server. WebSockets allow us to build “real-time” applications without the use of long-polling.

#### Why should we use WebSocket?

- Websocket provides us real-time updates, it is compatible with various platforms like Android, iOS, Mac, Windows, etc. Websockets help in sending multiple requests simultaneously and can also have multiple connections. We can enable proxies. And there are many open-source platforms available to help you build Websocket apps.

#### Pings and Pongs: The Heartbeat of WebSockets

- At any point after the handshake, either the client or the server can choose to send a ping to the other party. When the ping is received, the recipient must send back a pong as soon as possible. You can use this to make sure that the client is still connected, for example.


### References

- [https://sookocheff.com/post/networking/how-do-websockets-work/](https://sookocheff.com/post/networking/how-do-websockets-work/)
- [https://www.geeksforgeeks.org/what-is-web-socket-and-how-it-is-different-from-the-http/](https://www.geeksforgeeks.org/what-is-web-socket-and-how-it-is-different-from-the-http/)
- [https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API/Writing_WebSocket_servers#pings_and_pongs_the_heartbeat_of_websockets](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API/Writing_WebSocket_servers#pings_and_pongs_the_heartbeat_of_websockets)
- [https://kipalog.com/posts/Duc-khoet-Javascript--Phan-5---Dao-sau-WebSocket---HTTP-2-voi-SSE---Hay-chon-gia-dung](https://kipalog.com/posts/Duc-khoet-Javascript--Phan-5---Dao-sau-WebSocket---HTTP-2-voi-SSE---Hay-chon-gia-dung)