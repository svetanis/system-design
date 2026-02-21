# Design a Messaging App Like WhatsApp
WhatsApp is a messaging service that allows users to send and receive encrypted
messages and calls from their phones and computers. 

## Functional Requirements
1. Users should be able to start group chats with multiple participants (limit 100)
2. Users should be able to send/receive messages
3. Users should be able to receive messages sent while they are not online (up to 30 days)
4. Users should be able to send/receive media in their messages

## Non-Functional Requirements
1. strong consistency and guarantees for message delivery & ordering
2. low latency send/receive messages (<500ms)
3. high throughput for 1B DAU
4. fault tolerant
5. messages storage guarntee for up to 30 days

## Core Entities
1. Messages
2. Users
3. Chats
4. Clients

## API Design
```java
1. WS: create chat
	{name : "",
	 participants : []
	} -> chatId
	
2. WS: send message
	{chatId : "",
	 message : "",
	 attachments : []
	} -> 200 OK | FAILURE
	
3. WS: chat update
	{chatId : "",
	 message : "",
	 participants : []
	} -> RECEIVED
	
4. WS: receive message
	{chatId : "",
	 message : "",
	 attachments : []
	} -> RECEIVED

5. WS: modify chat participants
	{chatId : "",
	 userId : "",
	 "operation" : "ADD" | "REMOVE"
	} -> "SUCCESS" | "FAILURE"
```

## [High Level Design](https://github.com/svetanis/system-design/blob/main/chat-messenger/high-level-design.png)

## [NotebookLM Slides](https://github.com/svetanis/system-design/blob/main/chat-messenger/slides.pdf)

## [NotebookLM Diagram](https://github.com/svetanis/system-design/blob/main/chat-messenger/diagram.png)
