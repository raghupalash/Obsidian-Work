In long polling, instead of getting a request and giving an immediate response(unlike [[Traditional Polling]]), the server keeps the request open untill there's new data - when the server has some new data, it sends the response to the client and closes the request.

Data transfer is only one way though, for bi-directional data transfer, there's  [[Web Sockets]].

Although this system reduces latency, it's less scalable - because as the amount of clients and data grows, amount of open long polling connections will grow - which will consume server resources.

That's why we oughta use [[Push notifications]] system like [[Kafka]].