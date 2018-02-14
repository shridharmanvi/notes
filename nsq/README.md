# Documentation and findings on nsq

### Useful links:
Introductory blog on nsq (using python client): https://dustinoprea.com/2013/11/26/using-bitlys-nsq-job-queue/
Introductory talk on nsq:  https://www.youtube.com/watch?v=OwD-W7uU2zU


### Some points on nsq
* Nsq is a real time distributed mesaging queue platform built in go 
* It does not maintain multiple copies of messages
* Supports multiple pub/sub patterns
	- Distribution - Distributes the messages to all the consumers
	- Fanning - Share messages between different consumers in a round robin fashion
* Supports logging of messages (Just another consumer) - all above patterns above hold true for this
* If one of the consumers die, messages are adjusted to be shared between existing consumers. Once it comes back up the new node is considered for message distribution.
* If no consumers are available, messages are held within nsqd to a threshold before flushing it out to disk


### Components:
* nsqd - Demon which queues messages on producer side (Usually every producer is accompained by a nsqd demon)
* nsqlookupd - State keeper of the cluster
* nsqadmin - UI metrics reporter for all topics
