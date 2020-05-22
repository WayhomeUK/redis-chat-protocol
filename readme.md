Redis Chat Protocol
===================

Message
-------


```json
{
    "username": "l33th4x0r",
    "body": "I'm a looking for sick warez!",
    "timestamp": "2020-05-22T14:07:50+0100"
}
```

To create a message:

1. serialise like above
2. `LPUSH` message on to list with key `general-history`
3. `PUBLISH` message on to topic `general-chat`

To read message history

1. `LPUSH` `general-history` 0 <your prefered history>
2. de-serialise as above

To read message live as they come in:

1. `SUBSCRIBE` to topic `general-chat`
2. de-serialise as above
