SocketHttpListener
==================

A standalone HttpListener with support for WebSockets and Mono

As part of Media Browser Server we needed an http server implementation that could support both WebSockets and Mono together on a single port.

This code was originally forked from websocket-sharp:

https://github.com/sta/websocket-sharp

websocket-sharp was originally a clone of the mono HttpListener found here:

https://github.com/mono/mono/tree/master/mcs/class/System/System.Net

It also added WebSocket support. Over time websocket-sharp began to introduce a lot of refactoring whereas I prefer a straight clone of the mono implementation with added web socket support. So I rebased from the mono version and added web socket support.

In addition, there are a few very minor differences with the mono HttpListener:

* Added ILogger dependency for application logging
* Resolved an issue parsing http headers from Upnp devices. (We'll submit a pull request to mono for this).
* Worked around a known issue with Socket.AcceptAsync and windows. See: https://github.com/MediaBrowser/SocketHttpListener/blob/master/SocketHttpListener/Net/EndPointListener.cs#L170
