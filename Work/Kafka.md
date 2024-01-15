- Kafka is a distributed "streaming" system. 
- It's based on a publish-subscribe model. 
- Three importnant components of Kafka are - producer, topics and consumers. 
	- Producer - producer of the data or "message". 
	- Topic - Messages are grouped by channels or "topics". 
	- Consumer - These subscribe to particular topics to recieve the data in the order it was created. 
- One crucial aspect of Kafka is that it shows the message in the exact order they were sent. It maintains an immutable stack of messages in their exact order. It's called **"commit log"** And it's possible to navigate this "message history" and start from wherever the consumer want to. 
- Kafka can efficiently handle a large amount of data. 
- Kafka is also very fault tolerant! since it maintains a distributed database system. 
- Kafka can also run on multiple servers called "brokers".
- In Kafka, we tend to think less in terms of **"things"** and more in terms of **"events"**.

Also see, [[Pull queries]] and [[Push notifications]].