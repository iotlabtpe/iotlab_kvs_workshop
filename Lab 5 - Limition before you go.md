---
layout: default
categories: [lab]
tags: [setup]
excerpt_separator: <!--more-->
permalink: /lab/lab-5
name: /lab/lab-5.html
---

# Limition, before you go

### Q: What’s the limits for kinesis video stream services?

https://docs.aws.amazon.com/kinesisvideostreams/latest/dg/limits.html



- `Account Limit: Request TPS`, means How many times could we request per second per account. 
- `Stream-level limit TPS`, means How many time could we request for that (video)stream per second. 
- `Connection-level limit`, means How many concurrency could we have per (video)stream. 
- `Session-level limit TPS`, similar to Connection-level limit, to be confirmed, Playback Protocol.

*For example*, PutMedia, use this API to send media data to a Kinesis video stream. 

| API          | Stream-level limit | Connection-level limit | Bandwidth limit | Fragment-level limit |
| ------------ | ------------------ | ---------------------- | --------------- | -------------------- |
| **PutMedia** | 5 TPS [h]          | 1 [s]                  | 12.5 MB/second  |                      |

- Minimum fragment duration: 1 second [h]
- Maximum fragment duration: 10 seconds [h]
- Maximum fragment size: 50 MB [h]
- Maximum number of tracks: 3 [s]

> Customer software triggered by event, like human or pet passing, after that it will put 120 seconds video record up to KVS server, then stop this stream for cost saving. In certain case, two event happened side by side, first stream is still not finished due to networking jam, the second stream is going, in short under concurrency situation, video reiteration is not satisfied.

### Q: How many producer(camera) and consumer(player or EC2)

One producer and two consumer, check *limits for kinesis video stream services*.

We can try this, setup more than two player and see what happens.

### Q: What’s the limits for kinesis video stream producer SDK?

https://docs.aws.amazon.com/kinesisvideostreams/latest/dg/producer-sdk-limits.html

 Highlight: 

- `Min storage size` is 1 MiB, *not 10 MiB* 
- `Min buffer duration` is 2-3 seconds, not 10 seconds. 
- `Max fragment size`(for example all of video frames between I frame in H.264) is 50MB 
- `Max fragment duration`(for example GOP in H.264) is 10 second. 
- `Max retention period`, 10 years.



## Done


You are done with the limitation and finished.