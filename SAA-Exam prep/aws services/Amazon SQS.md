Decoupling an application means breaking an application into independent parts that don't tightly depend on each other. 

- Amazon SQS is a fully managed service, used to decouple applications. 
- Default Retention period of message - 4 days, maximum = 14 days.


## Producing messages

- Producers send message to SQS using the SDK. 
- The message is persisted in SQS until a consumer deletes it. 

## Consuming messages

- Consumer(Running on EC2 instance server, or aws lambda)
- Poll for messages. 


In simple terms,

- One service pushes messages
- Another service pulls messages later. 

# Types of Queues

## Standard Queue

- At least once delivery
- Message can be duplicated 
- Order not guaranteed. 

- Use when: high volume , order don't matter


## FIFO Queue

- Exactly once processing
- Strict order

- Use when: Financial transactions, Order processing

### Message Lifecycle

1. Producer sends a message
		send message --> queue
2. Consumer receives message
		receive message --> gets message

But message is not deleted automatically. 

Instead message becomes invisible for sometime, This time is called **visibility timeout**.


#### Visibility timeout

When worker gets a message: 
- SQS hides it from other workers. 
- Worker processes it. 
- Worker must call: Delete message

If Worker crashes before deleting message:
- Visibility timeout expires
- message becomes visible again. 


## Dead letter Queue(DLQ)

If a message keeps failing repeatedly.

- It keeps coming back.
- can cause infinite loop

This problem can be solved using DLQ(Dead letter Queue)

If message fails N times --> Send to DLQ


---------------------------------------------------

There are two ways in which consumer polls for messages. 

### Short Polling

Immediate response, may return nothing, and this is more costly. 


### Long Polling

- Waits upto x seconds for messages. 
- Cheaper 
- Lower Latency.


### Scaling with SQS

You can scale consumer not SQS

Add more: 
- EC2 
- ECS tasks 
- Lambda functions

#### SQS with Lambda
Lambda can poll SQS automatically


***NOTE: We can also use SQS as a buffer to database writes***

