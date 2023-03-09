# Introduction

This repository is about microservices architecture and distributed systems using P**ython, Kubernetes, RabbitMQ, MongoDB, and MySQL**.

The mircoservice is about converting vedios to MP3

## Overall Flow of System
When a user uploads a video to be converted to MP3, the request will first hit Gateway and Gateway will then store the video in MongoDB and then put a meesage on a RabbitMQ queue letting Downstream Service know that there is a video to be processed in MongoDB. The video to MP3 converter service will consume messages from the queue. It will then get the ID of the video from the message  and pull that video  from MongoDB convert the video to MP3 then store the MP3 in MongoDB then it will put a  new message on the queueto be consumed by the notification service that says the conversion job is done. The message from the queue and sends an email notification informing the client that the MP3 for the video that he uploaded is ready for download.the client wil then use a unique ID acquired from the notification plus his JWT to make a request the API Gateway to download the MP3 and the API Gateway will pull the MP3 from MongoDB and serve it to the client.
